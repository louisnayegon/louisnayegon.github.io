## SPARQL

### Delete All Triples

```sparql
DELETE {?s ?p ?o} WHERE { ?s ?p ?o; }
or
DROP ALL
```

### List All Triples

```sparql
SELECT DISTINCT * WHERE {?s ?p ?o}
```

### Exporting Blaze Graph Knowledge Bases

I’ve been looking for examples on how to export data from Blaze Graph and came up with this solution.
I hope this is of help to others.

```bash
#!/bin/sh

REMOTEPEMFILE=filename.pem
REMOTEIPADDRESS=111.222.333.444
REMOTETEMPDIR="~/temp"
LOCALTEMPDIR=~/temp

ssh -i ${REMOTEPEMFILE} ubuntu@${REMOTEIPADDRESS} << EOF
  set -x
  rm -rf ${REMOTETEMPDIR}
  mkdir ${REMOTETEMPDIR}

  ## Location where Blaze Graph is installed
  cd /var/lib/bigdata

  ## Stop the Blaze Graph service
  sudo bin/bigdataNSS stop

  ## Export the data as triples in xml format
  sudo java -cp "lib/*" 
       -server 
       -Dlog4j.primary.configuration=file:var/jetty/WEB-INF/classes/log4j.properties 
       -Dlog4j.configuration=file:var/jetty/WEB-INF/classes/log4j.properties 
       com.bigdata.rdf.sail.ExportKB 
       -outdir ${REMOTETEMPDIR}/ 
       var/jetty/WEB-INF/RWStore.properties

  ## Start the Blaze Graph service
  sudo bin/bigdataNSS start
  ls -hal ${REMOTETEMPDIR}
EOF

set -x
rm -rf ${LOCALTEMPDIR}
mkdir ${LOCALTEMPDIR}
sudo rsync -avz -e "ssh -i ${REMOTEPEMFILE}" ubuntu@${REMOTEIPADDRESS}:${REMOTETEMPDIR}/ ${LOCALTEMPDIR}
```
