# Task 2: Rough outline for the beginning of an Operations/Administrator's Reference Guide

The outline below shows the TOC for a set of anchored tags within an operations/administrator's reference guide topic. The reference could either contain a set of topic pages, or a single reference page with each subsection anchored. 

I'd likely place the configuration file sub-parameters that are listed in this outline in bullets into tables with 
parateter name - required/optional - and description/example in the columns. 

You'll note that the section numbers are off from the config files section numbers. I added an overview section to this topic/page and that shifted the number (in my outline at least) ahead one from the config file comments.

I've added a few sections to the end of the reference guide: Securing Ripple Servers, Starting/Stopping Ripple Servers, Clustering Ripple Servers, Adding a Ripple Server to your cluster, Configuration file loading errors, Troubleshooting/Common Problems.

Some questions at the end. With more time, I'd have a few more. 

There were a lot of weirdly constructed comments that I would rewrite when placing into the reference guide, and then I'd place notes for the developer or QA person (SME) to review during documentation review. 

There was also a lack of default values for almost every parameter. I'd likely just install my own Ripple Server, and make a note of the default values, and then check with the SME on this. As an administrator, I'd want to know what the default value is for all parameters that are set by the Ripple Server, even if I never had to change them. Administrators like to fine-tune their servers, and just knowing the default value for a parameter can give a certain amount of peace of mind. I'm also thinking that business owners would want to have an idea how and where to set minimum/maximum settings based on their expected transactional input/output.


# Ripple Server Operations/Administrator's Reference Guide

<ol>
  <li>Overview Section
  <ol>
     <li>About the Ripple Server Configuration File - rippled.cfg</li>
     <li>Configuration File Location</li>
     <li>Server Element Notation</li>
     <li>Short overview/ bullet list of all setting types (at a high level, hyperlinked to each section) that are required/optional for the Ripple Configuration File, why the configuration file is needed, and how to secure the configuration file (if possible)</li>
  </ol>
  </li>
  <li>Server instance settings - Defining your server instance and listening ports 
     <ol>
       <li>Server port settings
         <ul>
            <li>name</li>
            <li>ip</li>
            <li>port</li>
            <li>protocol</li>
         </ul>
        </li>
        <li>Client connection settings
            <ul>
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
          </ul>
        </li>
        <li>WebSocket protocol settingsfw
          <ul>
            <li>permessage_deflate</li>
            <li>client_max_window_bits</li>
            <li>server_max_window_bits</li>
            <li>client_no_context_takeover</li>
            <li>server_no_context_takeover</li>
            <li>compress_level</li>
            <li>memory_level</li>
            <li>websocket_ping_frequency</li>
          </ul>
        </li>
        <li>RPC settings        
        </li>
      </ol>
  </li>
  <li>Peer protocol settings
     <ol>
        <li>Overview - These settings control security and access attributes of the Peer to Peer server section of the rippled process. Peer Protocol implements the Ripple Payment protocol. It is over peer connections that transactions and validations are passed from to machine to machine, to determine the contents of validated ledgers.</li>
        <li>Peer connection/server settings - Production settings
           <ul>
             <li>ips|ips_fixed</li>
             <li>peer_private - peer server privacy settings</li>
             <li>peers_max - peer connection limits</li>
             <li>node_seed - set priority order of your peer nodes</li>
             <li>cluster_nodes - extend trust to multiple nodes</li>
             <li>sntp_servers - Network Time Protocol server addresses</li>
             <li>overlay - settings related to the peer to peer overlay</li>
          </ul>
        </li>
        <li>Transaction Queue Settings - Beta/Experimental - do not use on production configuration files. Set of key/value parameters to tune the performance of the transaction queue.
          <ul>
             <li>ledgers_in_queue</li>
             <li>minimum_queue_size</li>
             <li>retry_sequence_percent</li>
             <li>multi_txn_percent</li>
             <li>minimum_escalation_multiplier</li>
             <li>minimum_txn_in_ledger</li>
             <li>minimum_txn_in_ledger_standalone</li>
             <li>target_txn_in_ledger</li>
             <li>maximum_txn_in_ledger</li>
             <li>maximum_txn_per_account</li>
             <li>minimum_last_ledger_buffer</li>
             <li>zero_basefee_transaction_feelevel</li>
           </ul>          
        </li> 
     </ol>
  </li>  
  <li>Ripple Protocol settings
    <ul>
      <li>Overview
     <ul>
        <li>node_size - tune the size of your server</li>
        <li>ledger_history - amount of ledgers to acquire in server memory on startup and maintain while operating</li>
        <li>fetch_depth - amount of ledgers to serve to peers that request it</li>
        <li>validation_seed - used to generate the validation public/private key pair</li>
        <li>validator_token - alternative to validation_seed for performing validation without storing keys on the network</li>
        <li>validator_key_revocation - tells peers not to trust a particular key in the peer to peer network</li>
        <li>validators_file - place where list of validators to trust is stored</li>
        <li>path_search - I don't quite understand this element and sub-elements</li>
        <li>path_search_fast</li>
        <li>path_search_max</li>
        <li>path_search_old</li>
       <li>fee_default - Sets the base cost of a transaction in drops of network connection and server has no basis for fee info</li>
       <li>workers - configurable set of threads to run</li>
     </ul>
     </li>
    </ul>  
  </li>
  <li>HTTPS Client settings
     <ul>       
        <li>ssl_verify</li>
        <li>ssl_verify_file</li>
        <li>ssl_verify_dir</li>
     </ul>
  </li>
  <li>Database settings - node_db
     <ul>
       <li>Overview</li>
       <li>node_db - Types and Settings
          <ul>
            <li>NuDB settings
            <ul>
              <li>NuDB Instance Required Keys
                <ul>
                  <li>type=nudb</li>
                  <li>path - path to DB</li>
                </ul>
             </li>    
             <li>NuDB Instance Optional Keys
                <ul>
                   <li>online_delete</li>
                   <li>advisory_delete</li>
                   <li>earliest_seq</li>
                </ul>
            </li> 
            </ul>
            </li>
            <li>RocksDB settings
              <ul>
                <li>RocksDB Instance Required Keys
                <ul>
                  <li>type=rocksdb</li>
                  <li>path - path to DB</li>
                  <li>max_size_gb</li>         
                </ul>
             </li>    
             <li>RocksDB Instance Optional Keys
                <ul>
                   <li>compression</li>
                   <li>online_delete</li>
                   <li>advisory_delete</li>
                   <li>earliest_seq</li>
                </ul>
            </li> 
              </ul>
            </li> 
            <li>node_db general settings
             <ul>
               <li>import_db</li>
               <li>database_path</li>  
               <li>shard_db</li>
             </ul>
            </li>            
         </ul>
      </li> 
       <li>General node_db Database Configuration Settings
         <ul>
           <li>online_delete</li>
           <li>advisory_delete</li>
           <li>earliest_seq</li>
         </ul>
       </li>
     </ul>
  </li>
  <li>Diagnostics settings
     <ul>
        <li>debug_logfile - location for the server debugging log file</li>
        <li>insight - location where to send server instrumentation metrics</li>
        <li>perf - location and configuartion for performance logging</li>
     </ul>
  </li>
  <li>Voting settings - Settings used during voting ledgers
     <ul>
        <li>reference_fee</li>
        <li>account_reserve</li>
        <li>owner_reserve</li>
     </ul>
  </li>
  <li>Example Settings
       <ul>
        <li>Server settings</li>                 
        <li>Other Ripple config settings</li>
      </ul>
  </li>
  <li>Ripple Server Administration Tasks
    <ul>
    <li>Setting up your Ripple Peer to Peer Server</li>
    <li>Securing a Ripple Server</li>
    <li>Starting/Stopping Ripple Servers
      <ul>
        <li>From the command line</li>
        <li>From the admin console</li>
     </ul>
    </li>
    <li>Clustering Ripple Servers
      <ul>
        <li>When to cluster Ripple Servers (Example with Diagram)</li>
        <li>Setting up a Ripple Server cluster</li>
        <li>Adding a Ripple Server to your cluster</li>
        <li>Defining node seeding order when clustering Ripple Servers</li>
        <li>Administering a cluster of Ripple Servers</li>
        <li>Starting/Stopping Ripple Servers in a cluster</li>
        <li>Securing a Ripple cluster</li>
     </ul>
   </li>
      <li>Ripple Server failover(?)</li>
      <li>Setting up your Database</li>
      <li>Fine tuning your Ripple Server - Setting up diagnostics
         <ul>
           <li>Setting up server debugging location</li>
           <li>Setting up server instrumentation logging and data collection</li>
           <li>Setting up server performance logging</li>
        </ul>
      </li>
      <li>Transaction settings - Setting up your reserves</li>
    </ul>
   <li>Configuration/Administration errors</li>
   <li>Troubleshooting/Common Problems</li>
 </li>
</ol>



**Notes/Questions for SME:**  
  
* In the overview, notation section, the or operand "|" is described, but it's never used again within the document. I'd either take that out of the notation description, or add some examples within the documentation that actually use that operator


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

* Ripple Protocol section   
What are the relative sizes of load and expected memory use for each of these, and how would I make these guesses: By the amount of transactions that are in flight, and the size of the ledgers I'm loading into memory for comparison? I guess to start, it might make sense to just set it to tiny and then scale up as the load and memory requirements for my server increase, but Id want some ballpark figures, as most admins don't like to guess on these types of things. 
  * tiny  
  * small 
  * medium 
  * large 
  * huge  
Tune the servers based on the expected load and available memory. Legal sizes are "tiny", "small", "medium", "large", and "huge". We recommend you start at the default and raise the setting if you have extra memory. The default is "tiny".

  * I'd want to get a coffee with an engineer or other SME to learn more about path_search and what it actually means. I'm not sure how the aggressiveness number works, along with the follow-on elements around path search.


* Database section

  * In the DB section, NuDB and RocksDB are described and from the file, it makes it seem like these are the only DBs you can set up with a Ripple server. 
  Are these enterprise-ready DBs or meant for testing purposes? 
  Can a server admin connect a different database such as Oracle or Postgres or Mongodb to Ripple? 


* Voting Section

  * What's the default configured amount for all parameters within the voting section?  
  reference_fee  
  account_reserve  
  owner_reserve  
  
