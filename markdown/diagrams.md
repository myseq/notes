## SSH Local Port Forwarding

SSH local port forwarding allows you to securely access a service running on a remote server through an encrypted SSH tunnel.

```mermaid
graph TD
    cli_1[client:8080]
    cli_2[client:9090]
    fw1{{firewall_1}}
    fw2{{firewall_2}}
    sshd1["web1:8080
             web1:22"]
    sshd2["ssh_server2:22"]
    web2["web2:9090"]
 
    subgraph main[Local Port Forwarding]
      

        subgraph local[Home]
        cli_1 -.-> |dport:8080| cli_1
        * -.-> |dport:9090| cli_2
        end
             
        subgraph remote[Datacenter]
        cli_1 === |22/tcp| fw1 ==> |dport:22| sshd1
        sshd1 -.-> |dport:8080| sshd1

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

```mermaid
graph BT
  ssh_1(["ssh_svr:22
        web1:8080"])
  fw_1{{firewall}}
  cli_1((client:8080))
  cli_2((client:9090))
  fw_2{{firewall}}
  ssh_2["ssh_svr:22"]
  web2(["web2:9090"])


  
  subgraph main[Local Port Forwarding]
    direction BT

    subgraph DC[Datacenter]
      direction BT 
      fw_1 ==> |dport:22| ssh_1
      ssh_1 -.-> |dport:8080| ssh_1

      fw_2 ==> |dport:22| ssh_2
      ssh_2 -.-> |dport:9090| web2
    end 

    subgraph Home[Remote]
      direction BT
      cli_1 === |22/tcp| fw_1
      cli_1 -.-> |dport:8080| cli_1

      cli_2 === |22/tcp| fw_2 
      * -.-> |dport:9090| cli_2
    end
  
  end

  linkStyle default stroke-width:4px,stroke:yellow
  linkStyle 0 stroke-width:4px,stroke:blue
  linkStyle 1 stroke-width:5px,stroke:red
  linkStyle 2 stroke-width:4px,stroke:blue
  linkStyle 3 stroke-width:4px,stroke:red
  linkStyle 4 stroke-width:4px,stroke:blue
  linkStyle 5 stroke-width:4px,stroke:red
  linkStyle 6 stroke-width:4px,stroke:blue
  linkStyle 7 stroke-width:4px,stroke:red

  classDef main font-size:20px,color:#f66
  classDef Group1 color:#0ff
  classDef Group2 color:#0f0

  class main main
  class DC Group1
  class Home Group2
```

## SSH Remote Port Forwarding

SSH remote port forwarding allows a remote server to access a service running on local machine/network through an encrypted SSH tunnel.

```mermaid
graph LR
    A[Your Local Machine] -->|1. SSH Connection| B[Remote Server]
    B -->|2. Remote Port Forwarding| C[Service:localhost:8080]
```

