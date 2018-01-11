# Flexcrowd Main Repository

## Installation

### Applications version

| Item 			| version 	|
|---------------|------------	|
| Nodejs 			| v6.11.2 	|
| NPM 				| v3.10.10 	|
| SailsJS 		| v0.12.14  	|
| Elasticsearch 	| v5.5.2 		|
| PredictionIO 	| v0.11.0 	|

## Elasticsearch

### Installation

#### URL : http://localhost:9200

#### Links

> [Index Module](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-modules.html)

> [Basic concepts](https://www.elastic.co/guide/en/elasticsearch/reference/current/_basic_concepts.html)

> [Dynamic Mapping](https://www.elastic.co/guide/en/elasticsearch/reference/current/dynamic-mapping.html) 

> [Partial update](https://www.elastic.co/guide/en/elasticsearch/guide/current/partial-updates.html)

> [Autocomplete](https://www.elastic.co/guide/en/elasticsearch/guide/current/_index_time_search_as_you_type.html)

> [Multi-field search](https://www.elastic.co/blog/multi-field-search-just-got-better)

> [Field datatypes](https://www.elastic.co/guide/en/elasticsearch/reference/2.4/mapping-types.html)

> [Setup](http://predictionio.incubator.apache.org/deploy/)

> [Document queries](https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html)

> [Indexing](https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html)

> [Relationships](https://www.elastic.co/guide/en/elasticsearch/guide/current/relations.html)

> [Bucket Aggregation](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-terms-aggregation.html)

> [Cheatsheet](http://elasticsearch-cheatsheet.jolicode.com)

> https://www.sitepoint.com/search-engine-node-elasticsearch/

> https://github.com/marsanla/sails-elasticsearch

> http://chrissimpson.co.uk/elasticsearch-yellow-cluster-status-explained.html


#### Import dataset from JSON

cd to backend folder

> Can also be done via the admin Front-end

##### Import Plaform
	node_modules/elastic-import/bin/elastic-import.js ./data/liste_plateformes_crowdflower_vf.json localhost:9200 operation platform -i ignoreMe,myArray[*].ignoreMe --json

##### Import Categories
	node_modules/elastic-import/bin/elastic-import.js ./data/description_categories.json localhost:9200 operation category -i ignoreMe,myArray[*].ignoreMe --json

##### VM Commands
	sudo /etc/init.d/elasticsearch restart
	
#### Elasticsearch dump

> Can also be done via the admin Front-end

	npm install elasticdump
	
	cd to backend directory
	
	--input=http://localhost:9200/operation --output=./data/flexcrowd_[data|mapping|analyzer].json --type=[analyzer | mapping | data]
	
	# Import from local to server
	elasticdump --input=http://localhost:9200/operation --output=http://flexcrowd.org:8083/operation --type=data
	
	# Import from server to local
	elasticdump --input=http://flexcrowd.org:8083/operation --output=http://localhost:9200/operation --type=data
	
	# Import from local server to files
	elasticdump --input=http://localhost:9200/operation --output=./data/10012018.json --type=data
	
	# Import from file to local server
	elasticdump --input=./data/10012018.json --output=http://localhost:9200/operation --type=data



## Kibana

Elasticsearch data visualization

Need to be installed manually from 

#### URL : http://localhost:5601

`./bin/kibana`



## Server application launch

###Flx-Process module
The flx-process module is to manage the flow state and branching based on a YML file describing intent and entities

#### Linking the flx-process module to the Back-end application

	cd to flx-process (backend/flx-process)
`npm link`
	
	cd to backend root directory
`npm link flx-process`

###Development environment

#### Front-end
> Url: http://flexcrowd.org:8081

	pm2 start --name FLXC-FE-DEV npm -- run [dev|prod]	
#### Backend-end

> Install bower globally
	
	npm install bower -g
	cd to/backend/assets folder
	bower install

> Url: http://fflexcrowd.org:8082

	pm2 start process.json --env [development|production] 

#### Elastic-search
> Url: http://flexcrowd.org:9200

###Production environment



## PredictionIO

#### URL : http://localhost:7070

### Installation

> Download PredictionIO from [Apache mirror](https://www.apache.org/dyn/closer.cgi/incubator/predictionio/0.11.0-incubating/apache-predictionio-0.11.0-incubating.tar.gz)

> Set the desired version for Scala, Spark and Elasticsearch to build the binary distribution

Latest version as of 29.08.2017

| Item 		   | Version 	| Used version |
|---------------|---------	|--------------|
| Scala 		   | v2.12.3 	| v2.10.6		  |
| Spark         | v2.2.0 	| v2.1.0       |
| Elasticseach  | v5.5.2  	| v5.5.2       |

	
	./make-distribution.sh -Dscala.version=2.10.6 -Dspark.version=2.1.0 -Delasticsearch.version=5.5.2
	
> Installing dependencies packages in `PredictionIO-0.11.0-incubating/vendors`

After building a distribution, never rebuild with different version in the same directory, you'll need to start with a fresh copy of PredictionIO framework
	
	wget http://d3kbcqa49mib13.cloudfront.net/spark-1.6.3-bin-hadoop2.6.tgz
	
	wget https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-1.7.6.tar.gz	

Export The Prediction IO Path (Linux)

	PATH=$PATH:/Applications/AMPPS/www/flexcrowd/predictionio/PredictionIO-0.11.0-incubating/bin; export PATH
	
Give Permission To Prediction IO Installation

`PredictionIO-0.11.0-incubating/bin/pio-start-all`

`pio status`

`pio-[start|stop]-all`

Download or clone an engine template

Create an application for the engine template

Import data to Prediction Application

	pio import —-appid [appID] —-input ../data/pio_data-sample.json
	pio import --appid 2 --input my_events.json


### Links

> [Command Line] (http://predictionio.incubator.apache.org/cli/#engine-commands)

> [Learning DASE](http://predictionio.incubator.apache.org/customize/)

> [Datastore](http://predictionio.incubator.apache.org/system/anotherdatastore/)

## Misc

`netstat -vanp tcp | grep 9200`