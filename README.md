The outline below shows the TOC for a set of anchored tags within an operations/administrator's reference guide topic. The reference could either contain a set of 8 topic pages, or a single reference page with each subsection anchored.

You'll note that the section numbers are off from the config files section numbers. I added an overview section to this topic/page and that shifted the number (in my outline at least) ahead one from the config file comments.


Ripple Server Configuration Guide

<ol>
  <li>Overview
  <ol>
     <li>About the Ripple Server Configuration File - rippled.cfg</li>
     <li>Configuration File Location</li>
     <li>Server Element Notation</li>
  </ol>
  </li>
  <li>Server instance settings - Defining your server instance 
     <ol>
       <li>Server port settings
         <ol>
            <li>name</li>
            <li>ip</li>
            <li>port</li>
            <li>protocol</li>
         </ol>
        </li>
        <li>Client connection settings
            <ol>
            <li>limit</li>
            <li>user/password</li>
            <li>admin - admin command access ips</li>
            <li>admin_user/admin_password</li>
            <li>secure_gateway - ip settings</li>
            <li>ssl_key</li>
            <li>ssl_cert</li>
            <li>ssl_chain</li>
            <li>ssl_ciphers</li> 
            <li>send_queue_limit</li>
          </ol>
        </li>
        <li>WebSocket protocol settings
          <ol>
            <li>permessage_deflate</li>
            <li>client_max_window_bits</li>
            <li>server_max_window_bits</li>
            <li>client_no_context_takeover</li>
            <li>server_no_context_takeover</li>
            <li>compress_level</li>
            <li>memory_level</li>
            <li>websocket_ping_frequency</li>
          </ol>
        </li>
        <li>RPC settings        
        </li>
      </ol>
  </li>
  <li>Peer protocol settings
     <ol>
        <li>Overview - These settings control security and access attributes of the Peer to Peer server section of the rippled process. Peer Protocol implements the Ripple Payment protocol. It is over peer connections that transactions and validations are passed from to machine to machine, to determine the contents of validated ledgers.</li>
        <li>ips</li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
     </ol>
  </li>  
  <li>Ripple Protocol
     <ol>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
     </ol>  
  </li>
  <li>HTTPS Client
     <ol>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
     </ol>
  </li>
  <li>Database settings
     <ol>
        <li>Overview</li>
        <li>NodeDB Types and Settings</li
        <li>NuDB settings</li>
        <li>RocksDB settings</li>
     </ol>
  </li>
  <li>Diagnostics settings
     <ol>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
     </ol>
  </li>
  <li>Voting settings
     <ol>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
     </ol>
  </li>
  <li>Example Settings
       <ul>
        <li>Server settings</li>                 
        <li>Other Ripple config settings</li>
      </ul>
   </li>
</ol>

**Notes/Questions:**  

* For the protocol = [ http, https, peer ], shouldn't it be protocol = < http, https, peer >, since the protocol element is a required element?


* Peer Protocol section:

  * In the Network Time Protocol (NTP) [sntp] protocol, we only show NTP servers that are suitable for the US. Should we provide any international servers to that list?
  
  * In the [ips] section of the peer protocol section, is says that "A port **may must** be specified after adding a space to the address". Which one is correct? From the examples (example one specifically), it looks like the correct statement is **may**, but I wanted to check to make sure.  
Examples:  
192.168.0.1  
192.168.0.1 3939  
r.ripple.com 51235

  * By convention, if known, IPs are listed in from most to least trusted.  
The sentence should say "...listed in order, from most to least trusted.", right?



* Database section

  * In the DB section, NuDB and RocksDB are described and from the file, it makes it seem like these are the only DBs you can set up with a Ripple server. 
  Are these enterprise-ready DBs or meant for testing purposes? 
  Can a server admin connect a different database such as Oracle or Postgres or Mongodb to Ripple? 
