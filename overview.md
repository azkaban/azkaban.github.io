---
layout: default
nav: overview
title: "Overview"
---

Azkaban was implemented at LinkedIn to solve the problem of Hadoop job dependencies. We had jobs that needed to run in order, from etl jobs to data analytics products.

Initially a single server solution, with the increased number of Hadoop users over the years, Azkaban has evolved to be a more robust solution.

Azkaban consists of 3 key components:

* Relational Database (MySQL)
* AzkabanWebServer
* AzkabanExecutorServer

<img title="Azkaban Overview" src="img/azkaban2overviewdesign.png" alt="Azkaban Overview" width="500" />

## Relational Database (MySQL)

Azkaban uses MySQL to store much of its state. Both the AzkabanWebServer and the AzkabanExecutorServer access the DB.

### How does AzkabanWebServer use the DB?

The web server uses the db for the following reasons:

* _Project Management_ - The projects, the permissions on the projects as well as the uploaded files.
* _Executing Flow State_ - Keep track of executing flows and which Executor is running them.
* _Previous Flow/Jobs_ - Search through previous executions of jobs and flows as well as access their log files.
* _Scheduler_ - Keeps the state of the scheduled jobs.
* _SLA_ - Keeps all the sla rules

### How does the AzkabanExecutorServer use the DB?
The executor server uses the db for the following reasons:

* _Access the project_ - Retrieves project files from the db.
* _Executing Flows/Jobs_ - Retrieves and updates data for flows and that are executing
* _Logs_ - Stores the output logs for jobs and flows into the db.
* _Interflow dependency_ - If a flow is running on a different executor, it will take state from the DB.

There is no reason why MySQL was chosen except that it is a widely used DB. We are looking to implement compatibility with other DB's, although the search requirement on historically running jobs benefits from a relational data store.

## AzkabanWebServer

The AzkabanWebServer is the main manager to all of Azkaban. It handles project management, authentication, scheduler, and monitoring of executions. It also serves as the web user interface.

Using Azkaban is easy. Azkaban uses _\*.job_ key-value property files to define individual tasks in a work flow, and the _dependencies_ property to define the dependency chain of the jobs. These job files and associated code can be archived into a _\*.zip_ and uploaded through the web server through the Azkaban UI or through curl.

## AzkabanExecutorServer

Previous versions of Azkaban had both the AzkabanWebServer and the AzkabanExecutorServer features in a single server. The Executor has since been separated into its own server. There were several reasons for splitting these services: we will soon be able to scale the number of executions and fall back on operating Executors if one fails. Also, we are able to roll our upgrades of Azkaban with minimal impact on the users. As Azkaban's usage grew, we found that upgrading Azkaban became increasingly more difficult as all times of the day became 'peak'.

