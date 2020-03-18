### Version
curl -X GET "localhost:9200/

### Get Health of Server
date && curl -XGET 'http://localhost:9200/_cluster/health?pretty'

### Get Nodes setup
curl -X GET "localhost:9200/_cat/nodes"

### Snapshots
curl -X GET "localhost:9200/_snapshot/20180529_backup/snapshot_1/_status?pretty" > status.json

### Settings
curl -XGET localhost:9200/_all/_settings?pretty

### Stats
curl -X GET "localhost:9200/_stats
