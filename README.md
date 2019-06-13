# CassandraCourse

In this project I'm going to follow [this](https://academy.datastax.com/resources/ds220-data-modeling)
course from [Datastax Academy](https://academy.datastax.com), which is for free.

## Getting Started

### Prerequisites

To complete this course I'm going to use the following technologies:

* [Docker](https://www.docker.com/)

### Installing

To have a Cassandra we are going to use Cassandra Docker image:

```bash
~$ docker pull cassandra:3.11
```

### Running

Start Cassandra as given below:

```bash
~$ docker run --name cassandra -d cassandra:3.11
```

### Running `cqlsh`

Access to the container to be able to run `cqlsh`:

```bash
~$ docker exec -it cassandra bash
```

And, once inside the container, run `cqlsh`:

```bash
root@cd23aed9e11b:/# cqlsh                                        
Connected to Test Cluster at 127.0.0.1:9042.
[cqlsh 5.0.1 | Cassandra 3.11.4 | CQL spec 3.4.4 | Native protocol v4]
Use HELP for help.
cqlsh>
```

To test Cassandra, I'm going to list all keyspaces executing the following query:

```bash
cqlsh> SELECT * FROM system_schema.keyspaces;

 keyspace_name      | durable_writes | replication
--------------------+----------------+-------------------------------------------------------------------------------------
        system_auth |           True | {'class': 'org.apache.cassandra.locator.SimpleStrategy', 'replication_factor': '1'}
      system_schema |           True |                             {'class': 'org.apache.cassandra.locator.LocalStrategy'}
 system_distributed |           True | {'class': 'org.apache.cassandra.locator.SimpleStrategy', 'replication_factor': '3'}
             system |           True |                             {'class': 'org.apache.cassandra.locator.LocalStrategy'}
      system_traces |           True | {'class': 'org.apache.cassandra.locator.SimpleStrategy', 'replication_factor': '2'}
```

## Data Model

KillrVideo is a website for sharing videos. It has the following features:

* Videos
* User Accounts
* User Ratings
* Movies/TV Shows
* Search
* Playback
* Comments

There are some problems KillrVideo faces:

* Scalability: constantly adds users and videos
* Reliability: must always be available
* Easy to use: must be easy to manage and mantain

But, Why Cassandra?

* Peers instead of master/slave
* Linear scale perfomance
* Always on reliability
* Data can be stored geographically close to clients

### Keyspace

It is a top-level namespace/container, similar to a relational database schema. Let's create our keyspace:

```bash
cqlsh> CREATE KEYSPACE killrvideo WITH replication = { 'class':'SimpleStrategy','replication_factor':1};
```

Once we've created the keyspace, we are going to move to the keyspace:

```bash
cqlsh> USE killrvideo;
cqlsh:killrvideo>
```

### Tables

Let's create our first table, but before we are going to copy a video.csv file into the container:

```bash

```bash
cqlsh:killrvideo>
```
