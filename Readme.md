# FlexCrowd Main Repository

## Installation

### Applications version

| Item 			| version 	|
|---------------|------------	|
| Nodejs 			| v6.10.1 	|
| NPM 				| v3.10.10 	|
| SailsJS 		| 0.12.13  	|
| Elasticsearch 	| v5.5.2 		|
| PredictionIO 	| v0.11.0 	|


## PredictionIO

### Installation

#### URL : http://localhost:7070

`PredictionIO-0.11.0-incubating/bin/pio status`

`PredictionIO-0.11.0-incubating/bin/pio-[start|stop]-all`

### Links

##### Command Line
> http://predictionio.incubator.apache.org/cli/#engine-commands

##### Learning DASE
> http://predictionio.incubator.apache.org/customize/

##### Datastore
> http://predictionio.incubator.apache.org/system/anotherdatastore/

## Elasticsearch

### Installation

#### URL : http://localhost:9200

#### Links

##### Field datatypes
> https://www.elastic.co/guide/en/elasticsearch/reference/2.4/mapping-types.html

##### Setup
> http://predictionio.incubator.apache.org/deploy/
> https://www.sitepoint.com/search-engine-node-elasticsearch/

##### Document queries
> https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html

> https://github.com/marsanla/sails-elasticsearch

##### Indexing
> https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html

##### Relationships
> https://www.elastic.co/guide/en/elasticsearch/guide/current/relations.html

##### Import from JSON

`node_modules/elastic-import/bin/elastic-import.js /Applications/AMPPS/www/flexcrowd/kibana/data/cs_ops_active.json localhost:9200 flexcrowd platform -i ignoreMe,myArray[*].ignoreMe --json`

`curl  --header "Content-Type:application/json" -s -XPOST localhost:9200/flexcrowd/platform/_bulk --data-binary "@/Applications/AMPPS/www/flexcrowd/kibana/data/cs_ops_active.json"`

## Misc

`netstat -vanp tcp | grep 9200`

## Kibana

Elasticsearch data visualization

#### URL : http://localhost:5601

`./bin/kibana`