# UTSA-2021-Low-rate-DoS-Attack Dataset
As we are interested in the detection of very low-rate attacks that include incomplete (SYN floods) and completed (HTTP slow-read) attack
flows, we generated benign and attack traffic flows with various rates using a software-defined networking testbed. The attacks include TCP SYN
floods and HTTP Slow READs and Slow GETs. The SYN floods are launched at various rates with short durations of attack, generating bursts at first 0.1s of every second for 100s, and long durations of quietness of 100s (absolutely no attack).

Traffic in this dataset.
  Syn25 through Syn300 denote traffic with benign flows and TCP SYN floods. 
  Slowread denotes the traffic with benign flows and Slow Read attack flows. 
  Benign denotes traffic with only benign flows. 
There are two types of benign traffic scenarios. 
  1-client scenario where a web client downloads a file from a web server back to back. 1Client_PCAPs.zip has pcap files related to 1-client scenario.
  8-client scenario, eight web clients download files from two web servers back to back, but at a slower rate owing to contention. This is a python program   
  communicating with two webservers with ports 5050 and 5060. PCAP_1.zip through PCAP_3.zip are pcap files related to attack cases in 8-client scenario. 
Attack traffic is collect using _hping3_ for SYN floods and _slowhttptest_ tool for Slow Read attacks.  
The traffic is collected as pcap files at the incoming interface of the switch from the client and attacker as the benign and attack traffic interfere at the switch. The experiments were run for 90 mins for each attack case running client(s) and attack simultaneously. However, benign only without any attack is collected with the experiments run for 150mins and 30 mins respectively with 8-client scenario. Benign_Only.zip has all benign traffic.

An experimental testbed used to collect the benign and attack traffic consists of four Linux machines. One machine runs vSwitch as OpenFlow switch and Pox
controller as OpenFlow controller to create an SDN environment. The southbound interface is a TCP channel with 1Gbps bandwidth and OpenFlow (OF) protocol v1.0 used for communication between switch and the controller. Two client machines, one is used as a benign client and the other as an attacker, and one as web server are connected to the OF switch.
