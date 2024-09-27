ARG SOLR_VERSION=9.6
FROM tugboatqa/solr:${SOLR_VERSION}
ENV COMPOSER_DISCARD_CHANGES=true
ENV COMPOSER_NO_INTERACTION=true
ENV COMPOSER_ALLOW_SUPERUSER=true

ENV SOLR_OPTS="-Djute.maxbuffer=50000000"
ENV SOLR_AUTH_TYPE=basic
ENV SOLR_AUTHENTICATION_OPTS="-Dbasicauth=solr:SolrRocks"
ENV SOLR_MODE=solrcloud

COPY <<EOF /etc/default/solr.in.sh
SOLR_OPTS="-Djute.maxbuffer=50000000"
SOLR_AUTH_TYPE=basic
SOLR_AUTHENTICATION_OPTS="-Dbasicauth=solr:SolrRocks"
SOLR_MODE=solrcloud
EOF

COPY <<EOF /var/solr/data/security.json
{
  "#ddev-generated":true,
  "authentication":{
    "class":"solr.BasicAuthPlugin",
    "credentials":{
      "solr":"IV0EHq1OnNrj6gvRCwvFwTrZ1+z1oBbnQdiVC3otuq0= Ndd7LKvVBAaZIF0QAVi1ekCfAJXr1GGfLtRUXhgrF8c="
    },
    "blockUnknown":false
  },
  "authorization":{
    "class":"solr.RuleBasedAuthorizationPlugin",
    "permissions":[
      {
        "name":"admin-ui",
        "path":"/admin/*",
        "role":"admin"
      },
      {
        "name":"read",
        "role":null
      },
      {
        "name":"update",
        "role":null
      },
      {
        "name":"all",
        "role":"admin"
      }
    ],
    "user-role":{
      "solr":"admin"
    }
  }
}
EOF

COPY <<EOF docker/scripts/zkauth.sh
#!/bin/sh
echo "set zoo keeper auth"
solr zk cp file:/var/solr/data/security.json zk:/security.json -z localhost:9983
EOF

RUN chown -R solr:solr /var/solr/data && \
chmod +x docker/scripts/zkauth.sh
