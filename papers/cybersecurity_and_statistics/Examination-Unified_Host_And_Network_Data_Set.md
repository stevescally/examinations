# Unified Host And Network Data Set

Data Science for Cyber-Security, Chapter 1, pg. 1-22, November 2018

DOI: https://doi.org/10.1142/9781786345646_001
License: Public Domain

# Understanding

- Useful data sets for analysis are rarely available due to:
    - Organizational security
    - Data sensitivity
- Commonly available data sets are synthetically generated or dated
- This data set looks to provide an updated(2106) real network communication flow.
- Data has been anonymized.
- If most of the data is internal and using rfc1918 defined address space what is the 
  company concern? Is it payload data that could be leaked?
- Mapping bi-flow transactions is difficult with basic tools, additional processing will
  be needed.
- Host and end-point logs are needed along with network data as encryption obfuscates
  the payload data from inspection.
- Host and end-point logs however are in different formats and may require parsing or 
  alternative formatting.
- Anomaly detection has been on-going for 20+ years however most systems are rule or
  signature based.
- Statistical methods have trouble gaining adoption in operational use due to high false
  positive rates and clouded alert messaging.
- However, anomaly detection methods are suited for this type of work as they can keep pace
  with the increasing amount of network traffic and pin point new variants of known signatures.


# Topics / Keywords
- bi-flows
- Anomaly detection
- Rules and signatures
- Data sets
- Event mapping 

# Implementation Ideas

1. Create a data set site where people can upload anonymous flow data sets.
    - Provide an anonymizer and payload removal
    - All we care about is meta data, transaction times, port, protocols
    - IP Addresses could have made up names
2. Research in processes starts / stop
    - process trees
3. Map event IDs from multiple sources
    - Network event logged
    - Application log has event from observed IP address
    - Another system responds to a generated event.
