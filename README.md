The outline below shows the TOC for a set of anchored tags within an operational/administrator reference guide topic. The reference could either contain a set of 8 topic pages, or a single reference page with each subsection anchored.


Ripple Server Configuration Guide

<ol>
  <li>Overview
  <ol>
     <li>About the Ripple Server Configuration File</li>
     <li>Configuration File Location</li>
     <li>Server Element Notation</li>
  </ol>
  </li>
  <li>Server instance settings - Defining your server instance 
     <ol>
       <li>Server Port Settings
         <ol type="A">
            <li>name</li>
            <li>ip</li>
            <li>port</li>
            <li>protocol</li>
         </ol>
        </li>
        <li>Client connection settings</li>
      </ol>
  </li>
  <li>Peer protocol settings - defining settings for transaction and validation of the Ripple Payment protocol
  
  
  
  </li>
</ol>




# 3. Ripple Protocol
# 4. HTTPS Client
# 5. Database
Overview
NodeDB Types and Settings
NuDB settings
RocksDB settings
# 6. Diagnostics
# 7. Voting
# 8. Example Settings


**Notes/Questions:**  

* For the protocol = [ http, https, peer ], shouldn't it be protocol = < http, https, peer >, since the protocol element is a required element?


* Peer Protocol section:

  * In the Network Time Protocol (NTP) [sntp] protocol, we only show NTP servers that are suitable for the US. Should we provide any international servers to that list?
  
  * In the [ips] section of the peer protocol section, is says that "A port **may must** be specified after adding a space to the address". Which one is correct? From the examples (example one specifically), it looks like the correct statement is **may**, but I wanted to check to make sure.  
Examples:  
192.168.0.1  
192.168.0.1 3939  
r.ripple.com 51235



* Database section

  * In the DB section, NuDB and RocksDB are described and from the file, it makes it seem like these are the only DBs you can set up with a Ripple server. 
  Are these enterprise-ready DBs or meant for testing purposes? 
  Can a server admin connect a different database such as Oracle or Postgres or Mongodb to Ripple? 
