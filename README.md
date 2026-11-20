# TinyRASP
Forked from: https://github.com/chenlvtang/TinyRASP

## Background
Traditional web application protection technologies, such as WAF (Web Application Firewall), often fail to cope with various coded or modified attacks because they intercept based on established rules. At the same time, the quality of the rules has a significant impact on the underreporting and false alarm rates, and it is impossible to defend against vulnerabilities with undisclosed exploitation methods.

Therefore, this paper designs and implements a vulnerability protection system for Java based on the emerging RASP technology. By embedding RASP probes on the key functions of the vulnerability exploit, real-time detection and logging are achieved at runtime. While the vulnerability can be detected and the warning page can be redirected, the ELK (Elasticsearch, Logstash, Kibana) architecture is used to visually manage attacker information for traceability analysis. Finally, the experimental results show that the system designed in this paper has good interception effect and compatibility, and has certain application scenarios.

### Keywords
RASP; vulnerability protection; Java Web; detection and interception; ELK; log visualization

## Results and prospects
✔ Vulnerability protection:
RCE
Arbitrary file reading
SQL Injection
Deserialization
JNDI Injection
SpEL expression injection
✔ compatibility:

Spring Boot、Tomcat
Java17、Java8
High and low versions of Servlet (the package name in the high version is Jakarta instead of Javax)

✔ Attack log visualization management:
Total log browsing
Attack Information Visualization

❌Protection rules still need to be improved (ORZ, currently very simple, in a hurry later, most of the JRASP rules are used, hahaha, Sorry
❌The coverage of vulnerabilities is low, and six types of vulnerabilities have been completed
❌Missing a user-configured read module, can only hardcode rules
❌As I was doing this, I found that Byte Buddy actually seems to be more useful than Javassit, haha, but I don't want to refactor


## Installation

1. Preparation:
```
git clone https://github.com/chenlvtang/TinyRASP.git
```
Download elasticsearch-8.7.0, kibana-8.7.0, logstash-8.6.2, mysql, and put the configuration files in the Config directory into the corresponding components. Manually open the service in sequence, or use run.bat to open in batches. Create a spring user in MySQL with spring as the default password, create a spring database, and import the foo.sql file into the Spring database.

2. Agent compilation:
```
mvn install
mvn clean package shade:shade
```

3. JDK17 starts SpringVulTest, JDK8 starts TomcatVulTest, and adds JVM startup parameters:
```
 -javaagent:/path/to/Agent.jar
```

Run test environment

## Acknowledgements
Thank you to all the masters for your generous technical blogs and open source projects, thank you ChatGPT, JRASP, OpenRASP, thank you thank you (●ˇ∀ˇ●)

## References

- http://www.jrasp.com/
- https://github.com/jvm-rasp/jrasp-agent
- https://github.com/baidu/openrasp
- https://www.cnblogs.com/bitterz/p/15152287.html
- https://www.cnblogs.com/Zzang/p/14845578.html
- https://javasec.org/java-rasp/Hook.html

  
