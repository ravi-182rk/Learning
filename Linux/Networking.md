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
  <img width="548" height="226" alt="image" src="https://github.com/user-attachments/assets/b4c9097f-afff-45be-a4e7-63ddefee6407" />  

    nsloop command reaches out to the DNS server and requests for the IP address of the hostname
    <img width="1047" height="345" alt="image" src="https://github.com/user-attachments/assets/7cfa618c-2fe9-4fe7-ba4d-905d07ca1210" />

3. **ping**:</br>
    **`ping`** the remoteserver, and check if you are getting any response. Observer if any packet loss.
    <img width="808" height="192" alt="image" src="https://github.com/user-attachments/assets/724660ff-5e53-4363-adfd-d0da3ea6e4d0" />

  > [!CAUTION]
  > Ping is often not the best tool to check connectivity, as many networks would have disabled it.

   
     
