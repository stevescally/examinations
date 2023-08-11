# Implementation and evaluation of secure and scalable anomaly-based network intrusion detection

Mieden, P. (2018). 
Implementation and evaluation of secure and scalable anomaly-based network intrusion detection.[bachelor thesis] 
Munich: the Ludwig maximilians university, institute fur informatics.
https://dreadl0ck.net/papers/mied18.pdf

# Understanding

* Current IDS/IPS systems designed in low level languages which suffer from manual memory management issues.
    * Buffer overflow, Off-by-One, Use-after-free,etc.
* Attacker can exploit this and look to disable the detection / prevention capabilities
* Additionally IDS/IPS systems are fixed in the data exporting capabilities and are not considering how the collected
  data could be used in other systems for processing or detection.
* Paper proposes a _"research framework for collecting traffic features implemented in a memory-safe language"_
    * Network traffic is stored as a type-safe structured data
    * Generates audit records in platform neutral format
    * Output is compressed to save on storage space requirements
* Implemented in Go
* Can process live capture traffic or read PCAP/PCAPNG files
* _Can create labelled datasets for supervised machine learning_
* Signature based detection suffers from zero-day attacks which are previously unknown
* Anomaly detection suffers from poor training data
* Attackers have a large amount of dwell time once inside the network
* Reported vulnerabilies are medium or high severity
    * The low severity items may also eventually become medium or highs if not addressed.
    * Note that severities don't have insight into defense-in-depth layers or the industry the
      software is being used in.
* SIEM systems struggle to organize and provide information from varying input sources and formats.
* Main Problems
    * Increasing volumes of data to process:
        * high resolution video
        * large file transfers
        * video conferencing
    * Attacks against the monitoring system itself
        * DoS
        * training data tainting
    * Sensors written in low-level systems programming languages
    * Most common data format, comma seperated values (CSV) does not preserve data types or provide structure
      to the data.
    * Internet and intranet traffic is encrypted, reducing the effectiveness of signatures that analyze payloads
    * Tooling doesn't allow for experimentation, requires fixed preperation.
* Goal
    * Implement a modern, systematic approach to access network protocol specific information for the purpose of
      research on anomaly based intrusion detection strategies.
    * Modern Attributes:
        * Suitable programming language
        * Supports major platforms
        * Memory safe, type safety, data structure integrity
        * Support utilizing multiple processing cores
        * Well documented
        * Live and offline dump file processing
        * Provide as much data at the lowest level of network, prior to generating abstractions
            * This may require more storage space.

# Implementation Ideas

1. Service that implements creates reliable training data. (NETCAP Cloud)
   - Get or provide honeypot data
   - Does having a known service like this attract attackers that would taint training data
     in their favor? I.e a week before a planned attack, submit data to the honey pots to 
     make it so their attacks are part of the accepted network flow.

2. Service that provides analysis of submitted data (NETCAP Cloud)
   - Provides best features to analyze
   - Provides some percentage of success rate / reporting
   - Determine when recalibration is needed

3. Suricata eve.json
    - See if eve.json file can be utilized with label extraction.

4. OpenArgus
    - Sensor / Collector
    - Would the collected data allow for feature extraction by Netcap?
    - Is this too little data if its expecting a pcap or the entire flow?

5. Jupyter
    - Could we run netcap as a built-in with a go kernel in a notebook
    - Import .pcap, csv, json and have features determined to then apply
      to the current dataset.
    - Jupyter allows wget/curl of data from another API endpoint.
    - Myabe this is only useful for initial EDA / PCA 



