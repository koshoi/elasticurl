# elasticurl

Kibana is great! It offers a great variety of features except for 'being a **comfortable** to use log viewer' feature.

It also lacks a very important property: you can't do
```bash
| grep ... | grep .... | jq '...' | perl -lnae '...' | grep ...
```

with Kibana.

## Usage

```
$ elasticurl --help
elasticurl [OPTIONS]
	retrieve logs from elasticsearch

configurable options are

	-a|--auth user:password
		specify credentials for elasticsearch (default='elastic:changeme')

	-f|--filter key=value
		specify filter for output logs

	-i|--index 'index_name'
		specify elastic index (default='logstash')

	-n|--namespace 'k8s_namespace'
		specify namespace
		equivalent to -f namespace=k8s_namespace

	-s|--service 'service_name'
		specify service
		equivalent to -f service=service_name

	-e|--endpoint host
		specify elasticsearch endpoint (default='localhost:9200')

	-d|--debug
		enable debug output

	-r|--raw
		raw elastic output

	-R|--recursive-jq
		apply additional jq recursive JSON parsing

	--help
		print help
```

## Dependencies

Those binaries are required on your machine with elasticurl
- curl
- bash
- printf
- grep
- sed
- jq

## Examples

```bash
$ elasticurl -f request_id=7769b903-6ad8-4ce8-abbe-8c6794d0d594

$ elasticurl -f status=200 --namespace stage

$ elasticurl -R -f level=error --index someElasticIndex
```
