## Aidos's Awesome Capstone
=========================

### Project Overview

Traditional security solutions such as firewalls, antivirus software, and cryptography systems have long been the cornerstone of cybersecurity strategies.
However, these solutions are no longer sufficient to address the evolving threats in today's cyber landscape. The key challenges:

**Static Defence.** Traditional security measures operate on a static basis, often relying on predefined rules and signatures to detect and mitigate threats. This approach fails to adapt to the dynamic nature of modern cyber threats, making it easier for attackers to evade detection.

**Limited Visibility.** Traditional solutions offer limited visibility into network traffic and user behavior, making it challenging to detect and respond to sophisticated attacks that may go unnoticed for extended periods.

**Lack of Advanced Threat Detection.**  Lack of Advanced Threat Detection: Traditional solutions are not equipped to detect and defend against advanced threats such as zero-day exploits, polymorphic malware, and targeted attacks. As a result, cybercriminals can exploit vulnerabilities in legacy security systems to infiltrate networks and compromise sensitive data.

#### Leveraging Data Science to Identify DDoS Attacks
DDoS attacks pose a significant threat to organizations, disrupting services and causing downtime. Data science techniques offer effective means to detect and mitigate these attacks.

* **Anomaly Detection.** Data science algorithms can analyze network traffic patterns and identify anomalies indicative of DDoS attacks, such as sudden spikes in traffic or unusual patterns of requests.
* **Behavioral Analysis.** Data science enables the analysis of user behavior and interaction patterns to distinguish between legitimate users and malicious bots involved in DDoS attacks.
* **Network Flow Analysis.** Data science techniques, such as flow-based analysis, can examine network flow data to identify abnormal traffic patterns associated with DDoS attacks, such as TCP SYN floods or UDP amplification attacks.
* **Collaborative Defense.** Data science allows for the integration of multiple data sources, including network logs, sensor data, and threat intelligence feeds, to enhance DDoS attack detection and response capabilities.

#### Impact of Implementing Data Science for DDoS Attack Detection
Implementing data science solutions for DDoS attack detection can have a significant impact on enhancing cybersecurity defenses and mitigating the effects of DDoS attacks.

* **Improved Threat Detection.** By leveraging advanced analytics and machine learning algorithms, organizations can enhance their ability to detect DDoS attacks in real-time, minimizing the impact of these attacks on their systems and services.
* **Reduced Downtime.** Early detection of DDoS attacks enables organizations to initiate timely response measures, such as traffic rerouting or mitigation strategies, to minimize service disruptions and reduce downtime for users.
* **Enhanced Resilience.** Data science solutions can help organizations build more resilient networks and systems capable of withstanding DDoS attacks, thereby maintaining continuous service availability and reliability for users.
* **Cost Savings.** By reducing the duration and impact of DDoS attacks, organizations can avoid potential revenue losses associated with downtime and service disruptions, leading to cost savings in terms of operational and reputational damage.
* **Proactive Defense.** Data science enables organizations to adopt a proactive approach to DDoS attack mitigation, allowing them to anticipate and prepare for potential attacks before they occur, thereby strengthening their overall cybersecurity posture.


... 
...
...

### Walkthrough Demo

...
...
...

### Project Flowchart
![Alt Text](https://github.com/aidos-askhatuly/DDos_attack_detection/blob/main/pics/Capstone%20Flowchart.drawio.png)

### Project Organization

* `datasets` 
    - contains link to copy of the ataset (stored in LFS)
    - data dictionary
    - saved copy of aggregated / processed data as long as those are not too large (> 10 MB)

* `model`
  - TBD

* `notebooks`
    - contains all final notebooks involved in the project

* `reports`
    - contains final report which summarises the project

* `references`
    - contains papers / tutorials used in the project

* `src`
    - Will contain the project source code (refactored from the notebooks)

* `.gitignore`
    - Part of Git, includes files and folders to be ignored by Git version control

* `capstine_env.yml`
    - Conda environment specification

* `Makefile`
    - Automation script for the project

* `README.md`
    - Project landing page (this page)

* `.gitattributes`
    - contains a reference to the dataset stored in LFS

### Dataset
The dataset is coming from the open source network analyzing software "Wireshark". The dataset contains information about network packets travelling between client, server and network devices in between such as routers and swithces. "Network packet" or "packet" is a unit of data that is transmitted over a network. It's the basic unit of communication in network protocols such as the Internet Protocol. A packet typically consists of two main parts: the header and the payload. The header contains control information such as the source and destination addresses, protocol information, packet sequence number, and error detection codes. The payload contains the actual data being transmitted. The dataset does not contain information about header and payload due to privacy.

The dataset also contains information about whether the network packets have been normal or non-normal, i.e. used to perform network attack.
* Source: Network traffic analyzing tool Wireshark.
* Shape: 2 160 668 * 28.
* Concerns: imbalanced data 90*10, IP address and hostnames are anonymized, data entry errors. Target value - Packet class: {Normal-10%, UDP-flood-9%, HTTP-flood, Smurf, SIDDOS}
* Data is clean: no null values, no duplicates

#### Data Dictionary

| Attributes        | Description                                                | Additional Information                                                                                               | Data type |
|-------------------|------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|-----------|
| SRC_ADD           | Source IP address                                          | Due to sensitivity, IP address is encrypted                                                                          | Object    |
| DES_ADD           | Destination IP address                                     | Due to sensitivity, IP address is encrypted                                                                          | Object    |
| PKT_ID            | Unique identifier for each network packet                  |                                                                                                                     | Numeric   |
| FROM_NODE         | Identifier for the source node in the network              |                                                                                                                     | Numeric   |
| TO_NODE           | Identifier for the destination node in the network         |                                                                                                                     | Numeric   |
| PKT_TYPE          | Packet type                                                | Common packet types: <br>1. TCP (Transmission Control Protocol). TCP is a connection-oriented protocol used for reliable and ordered data transmission. <br>2. UDP (User Datagram Protocol). UDP is a connectionless protocol used for fast and lightweight data transmission. <br>3. ICMP (Internet Control Message Protocol). ICMP is a network-layer protocol used for error reporting and diagnostics. <br>Common packet types associated with ICMP include: <br>- Echo request and reply: Used for ping tests to check network connectivity. | Object    |
| PKT_SIZE          | Packet size                                                 | Size of the network packet in bytes                                                                                  | Numeric   |
| FLAGS             | TCP flags or control bits associated with a TCP packet     | TCP uses a set of control flags to indicate various aspects of packet behavior, such as the SYN (synchronize), ACK (acknowledge), FIN (finish), RST (reset), and others | Object    |
| FID               | Flow Identifier                                            | A unique identifier associated with a flow of network traffic. A flow is a unidirectional sequence of packets between a specific source and destination, typically identified by their IP addresses and port numbers. | Numeric   |
| SEQ_NUMBER        | Sequence Number                                            | Sequence number of a TCP packet within a TCP connection. TCP uses sequence numbers to ensure the ordered delivery of data segments and to detect and recover from packet loss or reordering. | Numeric   |
| NUMBER_OF_PKT     | Number of Packets                                          | The total number of packets transmitted within a flow or connection.                                                  | Numeric   |
| NUMBER_OF_BYTE    | Number of Bytes                                            | The total number of bytes transmitted within a flow or connection.                                                    | Numeric   |
| NODE_NAME_FROM    | Node name from which package is sent                       | Name or identifier of the network node from which the packets originate. May contain the name, hostname, IP address, or other identifier of the originating node.         | Object    |
| NODE_NAME_TO      | Node name where package is sent to                         | The name or identifier of the network node to which the packets are sent. May contain the name, hostname, IP address, or other identifier of the destination node.       | Object    |
| PKT_IN            | Time packet sent from specific node                        | The time when a packet was sent by the specific node in the network.                                                  | Numeric   |
| PKT_OUT           | Time packet received by specific node                      | The time when a packet was received by the specific node in the network.                                               | Numeric   |
| PKT_R             | ?????                                                      | Values close to Packet_Receved_Time                                                                                   | Numeric   |
| PKT_DELAY_NODE    | Travel time to a specific node                             | The delay experienced by packets at a specific node in the network.                                                    | Numeric   |
| PKT_RATE          | Packet transmission rate                                   | Packet transmission rate, measured in packets per second (pps) or packets per unit time                               | Numeric   |
| BYTE_RATE         | Byte Rate                                                  | The rate at which bytes are transmitted or received over the network within a specific time interval. Expressed in bytes per second (B/s)                                       | Numeric   |
| PKT_AVG_SIZE      | Average size of data in each packet                        | The average amount of data (in bytes) contained in each packet exchanged between network nodes.                        | Numeric   |
| UTILIZATION       | Utilization of a network link or resource                  | The degree to which the network link or resource is being used, expressed as a percentage.                             | Numeric   |
| PKT_DELAY         | Total packet travel time from source to destination        | The total delay experienced by packets from the time they are transmitted until they are received at the destination node.                                                         | Numeric   |
| PKT_SEND_TIME     | Packet Send Time                                           | The timestamp indicating the time at which a packet was sent from the source node or device.                            | Numeric   |
| PKT_RECEIVED_TIME | Packet Received Time                                       | The timestamp indicating the time at which a packet was received at the destination node or device.                     | Numeric   |
| FIRST_PKT_SENT    | Time of the first packet sent                              | The timestamp indicating the time when the first packet in a network communication session was sent from the source node or device.                                                | Numeric   |
| LAST_PKT_RECEIVED | Time of the last packet received                           | The timestamp indicating the time when the last packet in a network communication session was received at the destination node or device.                                            | Numeric   |
| PKT_CLASS         | Packet Class                                               | Target value indicating class of the packet.                                                                         | Object    |



...
...
...

### Credits & References

...
...
...

--------
