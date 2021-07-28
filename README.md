# kotlin-web-api-gradle-spring-jaeger-prometheus-grafana-name-service

## Description
Calls remote services and
benchmarks the response. Uses prometheus
to graph response times and grafana for
tracing.

### STEP 1
Once the project is done building, make
some api calls `http://localhost:83/api/v1/names/random`.

### STEP 2
- goto http://localhost
- click on "Explore"
  - at the top change datasource to "Jaeger"
  - under "Trace" pick a service
    - pick "GET"
      - pick a single trace

To see a graph of response times:
- Nav to http://localhost:81
- Classic UI
  - Click Graph tab
    - Search: 'scrape_series_added'
      or 'scrape_duration_second'
      or 'http_request_duration_ms_bucket'
    - Duration 1m

For health check:
- Nav to http://localhost:81
- Targetes

To see a coverage of response times:
- Nav to http://localhost:82
- Look on left-hand side find services.

## Tech stack
- kotlin
- gradle
  - opentracing

## Docker stack
- gradle:jdk11
- jaegertracing/all-in-one:1.17
- prom/prometheus
- grafana/grafana

## To run
`sudo ./install.sh -u`
- GRAFANA DASHBOARD http://localhost
- PROMETHEUS DASHBOARD http://localhost:81
- JAEGER DASHBOARD http://localhost:82
- API http://localhost:83/api/v1/names/random

## To stop
`sudo ./install.sh -d`

## For help
`sudo ./install.sh -h`

## Credits
- [Project concept](https://github.com/himankbatra/opentracing-microservices-example)
