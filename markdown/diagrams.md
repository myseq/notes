## Diagrams

```mermaid
graph TD
    cli_1[client:8080]
    cli_2[client:9090]
    fw1{{firewall_1}}
    fw2{{firewall_2}}
    sshd1["  web1:22
           web1:8080"]
    sshd2["ssh_server2:22"]
    web2["web2:9090"]
 
    subgraph main[Local Port Forwarding]
      

        subgraph local[Home]
        cli_1 -.-> |dport:8080| cli_1
        end

        subgraph local[Home]
        * -.-> |dport:9090| cli_2
        end
             
        subgraph remote[Datacenter]
        cli_1 === |22/tcp| fw1 ==> |dport:22| sshd1
        sshd1 -.-> |dport:8080| sshd1
        end

        subgraph remote[Datacenter]
        cli_2 === |22/tcp| fw2 ==> |dport:22| sshd2
        sshd2 -.-> |dport:9090| web2
        end

      

    end 

    classDef title font-size:20px,color:#f66
    classDef padding stroke:none,fill:none
    classDef title2 color:#0ff

    class main title
    class remote title2

    style local color:#0f0
    
```


## SSH Local Port Forwarding

SSH local port forwarding allows you to securely access a service running on a remote server through an encrypted SSH tunnel.

```mermaid
graph LR
    A[Your Local Machine] -->|1. SSH Connection| B[Remote Server]
    B -->|2. Local Port Forwarding| C[Service:localhost:8080]
```

## SSH Remote Port Forwarding

SSH remote port forwarding allows you to access a service running on your local machine from a remote server through an encrypted SSH tunnel.

```mermaid
graph LR
    A[Your Local Machine] -->|1. SSH Connection| B[Remote Server]
    B -->|2. Remote Port Forwarding| C[Service:localhost:8080]
```

