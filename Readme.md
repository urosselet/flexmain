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

1. Pull the project main repositpory (flexmain) from GitLab

		git clone --recursive git@git.ig.he-arc.ch:ulysse.rosselet/flexmain.git
	
		git checkout feature/[v0.X.0]

2. Elasticsearch installation
	> JVM need to be installed before launching elasticsearch
		
	> Based on your OS, download and install the appropriate distribution from Elasticsearch website
				
3. Install node modules for the Front-end and Back-end repository
	
	> NodeJS and NPM need to be installed before executing the following command
	
	> Sailsjs, Bower and node-gyp need to be installed globally (npm i -g sails)
	
	cd to [front-end | backend] then execute
	
		npm install
		
	cd to back-end/assets then execute the following command
	
		bower install
		

## Elasticsearch

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


## Server application launch

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

## Misc

`netstat -vanp tcp | grep 9200`