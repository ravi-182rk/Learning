# Networking

## Troubleshooting
Let's say we are getting a connection timeout error while accessing a URL.
This could happen due to a variety of reasons:
- Issue with the local interface, not being able to connect to the network.
- Host not able to resolve the IP addr.
- Issue with the route to the server
- It could be an issue with the server itself.
### Troubleshooting steps:
1. **IP Link**:</br>
      Check the IP connectivity and check the primary interface is UP.
        ```
        ip link
        ```
      <img width="825" height="243" alt="image" src="https://github.com/user-attachments/assets/5b2b539a-5670-487c-8e66-eddecff49434" />
  Here you can see interface **`enp1s0f1`** is **`UP`**
2. **nslookup**:</br>
      Check if the hostname resolves to a IP address.  
      Run `nslookup <hostname>` and makesure it resolving to a valid IP.
      <img width="548" height="226" alt="image" src="https://github.com/user-attachments/assets/b4c9097f-afff-45be-a4e7-63ddefee6407" /> </br></br>
    
      nsloop command reaches out to the DNS server and requests for the IP address of the hostname
      <img width="1047" height="345" alt="image" src="https://github.com/user-attachments/assets/7cfa618c-2fe9-4fe7-ba4d-905d07ca1210" /></br></br>

3. **ping**:</br>
        **`ping`** the remoteserver, and check if you are getting any response. Observer if any packet loss.
        <img width="808" height="192" alt="image" src="https://github.com/user-attachments/assets/724660ff-5e53-4363-adfd-d0da3ea6e4d0" /></br></br>
        <img width="1346" height="706" alt="image" src="https://github.com/user-attachments/assets/1193522b-73ea-4804-9b8d-88f3c3e25e07" /></br></br>

  > [!NOTE]
  > Ping is often not the best tool to check connectivity, as many networks would have disabled it.

4. **traceroute**:</br>
        `traceroute <ip_address>` will show the no.of hops or devices b/w host and remote server.
         It will also show if there is any problem with any devices in the network route.</br></br>
         <img width="627" height="206" alt="image" src="https://github.com/user-attachments/assets/ad451c94-03d7-426f-9f7c-c67dc6fb6301" /></br></br>
         From the Image we can see there two routers and both are fine.
         But the connection is timeout b/w second router and the server.
         <img width="1346" height="610" alt="image" src="https://github.com/user-attachments/assets/a902433b-77cd-4581-a14f-ffe18d64ce03" /></br></br>
         It seems the issue is with remote server, let's  troubleshoot from otherend.

5. **Checks on Remote Server**:</br>
        **netstat**:
        Use below command to check if HTTP port is running on port 80 on remote server.</br>
        `netstat -an  | grep 80 | grep -i LISTEN`
        <img width="916" height="132" alt="image" src="https://github.com/user-attachments/assets/4271e481-d80a-46e6-8ebb-da6963351c1b" /></br></br>
        **`netstat`**:</br>
        command used to print the information of network connections, routing talbes and several other network statistics.</br>
        In this case, command shows information of active ports in the system, and we are looking specifically to see if port 80 is listening server.
        That means the webserver is good.</br>
        **Ip link**:</br>
        To inspect the interfaces using `ip link` command.
        We can see the interface down.
        <img width="798" height="218" alt="image" src="https://github.com/user-attachments/assets/09d0dbe6-2846-4861-b98c-e186d3175890" /></br></br>
        Bring the interface up by below command.  
        `ip link set dev enp1s0f1 up`
        <img width="785" height="43" alt="image" src="https://github.com/user-attachments/assets/2253ed41-1714-4876-a3bd-b26e0e806fbb" />


         

          
        

   
     
