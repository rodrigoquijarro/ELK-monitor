# Performance Monitoring with Docker & ELK Stack.


## Purpose

The purpose of the project is to understand what is ELK-Stack, what are their components and how to implement them in a virtual enviroment, to provide a powerful platform to aggregate logs from multiple systems, and centralize the data with a set of tools for metric analysis.
   
## Planned learning outcomes;
Capacity to integrate ELK-Stack components, evaluate and manage real data-log and how to ingest, search and visualize it. The learning outcome covers Logstash configuration, Elasticsearch overview, Filebeat, Metricbeat and Winlogbeat deployment, Kibana dashboards creation and recommended architecture for designing a monitoring and observability log system.

## Presentation plan

- What is ELK
- How it works
- Advantages & Limitations
- Properties 
- Scenario
- Configuration Issues
- Performance monitoring in Docker



## What is ELK

Computers, networks, and other IT systems generate records called audit trail records or logs that document system activities. Log analysis is the evaluation of these records and is used by organizations to help mitigate a variety of risks.

Analysts need to ensure that the logs consist of a complete range of messages and are interpreted according to context. Log elements should be normalized, using the same terms or terminology, to avoid confusion and provide cohesiveness. For example, one system might use “warning” while another uses “critical.” Making sure terms and data formats are in sync will help ease analysis and reduce errors. Normalization also ensures that statistics and reports from different sources are meaningful and accurate.

Once the log data is collected, cleaned, and structured, they can be properly analyzed to prevent downtimes, slow performance, detect patterns and anomalies and meet compliance regulations.

Of course, considering that currently, the data log info that companies generate between applications and Infrastructure can be simply terabytes in just one day, considering Microservices, containers, orchestration, and Cloud information. 

In simple words, our main objective is to define what information do we need to log? from where to collect it, what info is priceless for us, and how long do we need to retain the information. 

ELK Stack is a powerful platform that collects and processes data from multiple sources, in many formats, to search, analyze, and visualize that data in real-time. ELK provides centralized logging that is useful when attempting to identify problems with servers or applications. It allows searching all logs in a single place. It also helps to find issues that occur in multiple servers by connecting logs during specific time frames.

The ELK Stack is a collection of three open-source products:
Elasticsearch, Logstash, and Kibana. They are all developed, manage, and maintained by Elasticsearch.
 
### LOGSTASH

LogStash is a log aggregator that collects data from various input sources, executes different transformations and enhancements to ship the data to elasticsearch, or even, any other supported output destinations.

### ELASTICSEARCH

ElasticSearch is a NoSQL database, based on the Lucene search engine. It offers simple deployment, easy management but the most important, maximum reliability.
It also offers advanced queries to perform detailed analysis and data store in a centralized manner, helping to execute quick information searches and analyze significant data volumes. 
Elasticsearch is highly used as the main engine to power applications that completed search requirements. 

### KIBANA

Kibana is a visualization layer that works on top of Elasticsearch, providing visualization to analyze data, improving the decision.  


And last but not least — ELK stack is composed of two additional components: 

### Beats,  
Beats is a suite of lightweight agents that are installed on edge hosts to collect different types of data for forwarding into the stack.

### X-Pack, 
It is an Elastic Stack extension that provides security, alerting, monitoring, reporting, machine learning, and many other capabilities. 

Together, these components will be used for logging, monitoring, and troubleshooting IT environments but also business intelligence and web analytics.

By default, X-Pack is installed when Elasticsearch is deployed. Please consider that just the monitoring service is for free. If you want to try all of the X-Pack features, you can start a 30-day trial.

Logstash processing is organized into one or more pipelines. In each pipeline, one or more input plugins receive or collect data that is then placed on an internal queue. This is by default small and held in memory, but can be configured to be larger and persisted on disk in order to improve reliability and resiliency.

processing threads read data from the queue and process these through any configured filter plugins in sequence.

Once the data has been processed, the processing threads send the data to the appropriate output plugins, which are responsible for formatting and sending data onwards, e.g. to Elasticsearch.

Beats are essentially lightweight, purpose-built agents that acquire data and then feed it to Elasticsearch

- Filebeat is designed to read files from your system. It is particularly useful for system and application log files but can be used for any text files that you would like to index to Elasticsearch.

- Winlogbeat is a tool specifically designed for providing live streams of Windows event logs. It can read events from any Windows event log channel, monitoring log-ons, log-on failures, USB storage device usage and the installation of new software programs. 

- Packetbeat, a lightweight network packet analyzer, monitors network protocols to enable users to keep tabs on network latency, errors, response times

- Auditbeat performs a similar function on Linux platforms, monitoring user and process activity across your fleet.

- Metricbeat
As the name implies, Metricbeat is used to collect metrics from servers and systems. It is a lightweight platform dedicated to sending system and service statistics. 

- Heartbeat is a lightweight shipper for uptime monitoring. 

Logstash consumes a lot of resources so it is not an optimum solution to have logstash installed on all file servers. Instead, we can use Beats in such scenarios.

We will then deploy filebeat into multiple servers, these will then read the log files and send it to logstash or elasticsearch. Now we will use Filebeat to read the log file and send it to logstash to index it to elasticsearch.

Observability' is not something that a vendor delivers in a box -- it is an attribute of a system you build, much like usability, high availability, and stability. The goal of designing and building an 'observable' system is to make sure that when it is run in production, operators responsible for it can detect undesirable behaviors (service downtime, errors, slow responses) and this is how ELK processes the information. Clear, coherent, and understandable information. 

Winlogbeat, for example, with security, system, and application events.

Metricbeat, with CPU performance, and memory and disk usage.

In the same way, the information can be collected by Beats, processed by logstash, analyzed by elasticsearch, and visualized through kibana but sending information from specific sources.

The ELK stack in many projects is simply irreplaceable. Managers can monitor the bursts of errors on the frontend after the next release and come to the developers with a certain set of information. And developers and devs, in turn, find correlations with errors in the application, see their most important data, necessary for debugging and accurate localization of errors. It is also possible to instantly build various reports.

As we mentioned before, in the case of resource consumption different approaches can be performed to fit the best solution, without losing the same optimization. In this scenario for example, integrating raw data from logs sources but at the same time with Beats participation for optimization.

The demo architecture is composed of three components, one of them will be the ELK Stack server, who will allocate Elasticsearch, Logstash, and Kibana. In order to optimize time for this demonstration, these components will be deployed as containers by docker-compose, log events will be collected from the same server but at the same time from tho different clients, one ubuntu machine with filebeat and metricbeat.

The ELK stack in many projects is simply irreplaceable. Managers can monitor the bursts of errors on the frontend after the next release and come to the developers with a certain set of information. And developers and devs, in turn, find correlations with errors in the application, see their most important data, necessary for debugging and accurate localization of errors. It is also possible to instantly build various reports.







