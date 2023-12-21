# Survey: Atomatic Generation of Attack Trees and Attack Graphs

Alyzia-Maria Konsta, Alberto Lluch Lafuente, Beatrice Spiga, Nicola Dragoni,
Survey: Automatic Generation of Attack Trees and Attack Graphs,
Computers & Security,
2023,
103602,
ISSN 0167-4048,
https://doi.org/10.1016/j.cose.2023.103602.
(https://www.sciencedirect.com/science/article/pii/S0167404823005126)

License: CC-BY 4.0 DEED - https://creativecommons.org/licenses/by/4.0/

# Understanding

* Attack models comprised of Attack Trees and Attack Graphs
* Attack tree is a graphical representation of potential attacks on system Security
* Attack graph is a graphical representation that depicts all the possible paths an 
  attacker can follow to achieve their goal.
* The author notes differences between the attack graphs and trees however they are the same.
  While attack graphs could be cyclicle and have multiple paths the attack trees also produce multiple
  paths at the child node level.
* There are a number of proposed tools however they appear to mostly be past research projects, dated, or not 
  scalable to the rate at which networks are changing.
* To make the graphs and analysis useful manual processing or per-processing is needed in a large number of cases.
  This reduces the automated benefit of attack trees and graphs.
* Fault tree is an interesting topic. It would seem similar to understanding your attack map but could be useful in 
  automated analysis sections for operational or networking personel in making security related changes.
* 

# Topics / Keywords

* Graphical Security Models
* Attack Trees
* Attack Graphs
* Automatic Generation
* Threat Modelling
* Attack Models
  * Analysis Driven
  * Vulnerability Driven
  * Model Driven


# Implementation Ideas

1. Derive a map based on a nmap scan or zmap scanner
  * Scan common ports to reduce discovery time. 
2. Create logic or rules that understand the functionality of the
   node in the network. I.E a switch, dhcpd server, dns server, etc.
   * Would be best to filter out bogus vulnerabilities or ask for clarifying information
     such as installed version numbers.
3. Produce weights based on vulnerabilities and the functionality of the node.
  * Confirmed vulnerabilities or exploits would increase or lower risk
4. Attack Tree Analysis Tool(AT-AT)
  * https://github.com/yathuvaran/AT-AT
5. Create sqlite database with neo4j or networkx processing.
6. Order by analysis, Vulnerability, or Model
  * Create weights based on the users input
  * Tool that can be run for a security approval based on the proposed change.
  * Risk score or matrix
