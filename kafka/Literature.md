# Kafka: The Definitive Guide

![Kafka: The Definitive Guide.png](img/Kafka:%20The%20Definitive%20Guide.png)

## Chapter 1

---

### Exchange of messages by type "publication/subscription"

Exchange of "publish/subscribe" messages (publish/subscribe (pub/sub) messaging) - a design pattern that differs from
the sender (publisher) of the data element (message) does not send it to the particular consumer. Instead, he somehow
classifies-Messages, and the consumer (subscriber) subscribes to certain of them classes. In systems of the type "
publish/subscribe" to simplify these actions often include a broker - the central point of publication of messages.

Apache Kafka was developed as a messaging system by the "publish/subscribe" principle. It is often referred to as a
distributed streaming platform.

Kafka data is stored long, orderly and can be read whenever you want. In addition, it can be distributed by the system
is not only being used as an additional means of protection against failure, but also for the sake of improving
performance.

The data unit used in Kafka is called a **message**. From the Kafka point of view, a message is simply an array
bytes, so it doesn’t have any format or meaning for the data in it. The message may be an additional metadata fragment
called a key. It is also a byte array and, like the message, makes no sense to Kafka. Keys used when needed to better
manage the recording messages in sections.

For greater efficiency, messages in Kafka are written in packages (batch). is a simple set of messages, related to the
same topic and section.

Although messages for Kafka are only opaque byte arrays, it is recommended to superimpose the content of messages
An additional structure - a scheme that would allow them to be easily disassembled. There are many options for setting
up a message scheme depending on the needs of the particular application.

- **JSON**
- **String**
- **Double**
- **Integer**
- **Float**
- **Long**
- **bytes (base64)**
- Protobuf
- Protobuf Apicurio (deprecated)
- Avro
- Avro (Record Strategy)
- Avro (Topic-Record Strategy)
- Avro Legacy

Kafka needs a uniform data format, because it allows to separate the code of writing and reading messages.

---

### Topics and partition

Messages in Kafka are distributed across topics. The closest analogy would be a database table or a file system
directory. Topics, in turn, are divided into partitions.
If we return to the description of the commit log, a partition represents a separate log. Messages are written to it
by appending to the end and read sequentially from the beginning to the end. Since a topic typically consists of
multiple partitions, message ordering is not guaranteed across the entire topic—only within individual partitions.
Thanks to partitions, Kafka also ensures redundancy and scalability. Any partition can be placed on a separate server,
allowing the system to scale horizontally across multiple servers, achieving performance far beyond the capabilities
of a single server. Additionally, partitions can be replicated so that copies of the same partition are stored on
different servers in case one server fails.

---

### Producers and consumers

Kafka users are divided into two main types: producers and consumers. Producers generate new messages.

Message producers create messages for specific topics. By default, a producer will distribute messages evenly across
all partitions of a topic. In some cases, it directs a message to a specific partition. This is usually achieved using
a message key and a Partitioner object, which generates a hash of the key and maps it to a specific partition.

Consumers read messages. A consumer subscribes to one or more topics and reads messages in the order they were created
within each partition. It keeps track of which messages it has already read by recording the message offset.
An offset is a continuously incrementing integer value—another metadata element that Kafka adds to each message upon
creation. Offsets within a specific partition are unique, and the next message has a higher offset (though not
necessarily monotonically increasing).

By storing the next possible offset for each partition (usually within Kafka’s own storage), a consumer can pause and
resume processing without losing track of where it left off.
Consumers operate as part of consumer groups—one or more consumers working together to process a topic. Group
organization ensures that each partition is read by only one member of the group.

---

### Brokers and clusters

A single Kafka server is called a broker. It receives messages from producers, assigns offsets to them, and writes the
messages to disk storage. It also serves consumers by responding to fetch requests from partitions and returning
published messages. Depending on the hardware and its performance, a single broker can easily handle thousands of
partitions and millions of messages per second.

Kafka brokers are designed to operate as part of a cluster. One of the brokers in the cluster functions as the cluster
controller, which is automatically elected from the active members of the cluster. The cluster controller is responsible
for administrative tasks, including partition distribution among brokers and monitoring broker failures.

Each partition is owned by one broker in the cluster, known as the leader. Additional brokers, called followers,
replicate the leader’s data. All producers must connect to the leader to publish messages, but consumers can retrieve
messages either from the leader or one of the followers.

A key feature of Apache Kafka is its ability to retain data for extended periods. Kafka brokers include a default
retention policy for topics, which can be configured either for a specific time period (e.g., seven days) or until a
partition reaches a certain size in bytes (e.g., 1 GB). Messages exceeding these limits become invalid and are deleted.

Retention settings can also be customized for individual topics to retain messages only as long as they are needed.
Additionally, topics can be configured with log-compacted storage. In this case, Kafka retains only the latest message
for a given key. This is useful for data like change logs, where only the most recent update is relevant.

### Multiple Clusters

Multiple Clusters

As Kafka deployments grow, having multiple clusters can be beneficial. Here are a few reasons why:
  - Separation of data types.
  - Isolation to meet security requirements.
  - Multiple data centers (disaster recovery).

When working with multiple data centers, there is often a need to replicate messages between them.

Kafka’s replication mechanisms are designed to operate within a single cluster, and replication between clusters is not
natively supported.

The Kafka project includes a utility called MirrorMaker for replicating data to other clusters. Essentially, this is a
Kafka consumer and producer combined into a pipeline. The utility consumes messages from one Kafka cluster and publishes
them to another.

