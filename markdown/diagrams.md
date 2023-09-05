## SSH Local Port Forwarding

SSH local port forwarding allows you to securely access a service running on a remote server through an encrypted SSH tunnel.

```mermaid
%%{init: {'theme': 'dark', "flowchart" : { "curve" : "basis" } } }%%
graph 
  fw1{{fw_allow}}
  fw2{{fw_block}}

  subgraph main[Prerequisite: Firewall Requirement]
    direction RL
 
    subgraph grant[Success: Allow incoming SSH port]
      direction LR
      client1 --> |22/tcp| fw1 --> |dport:22| sshd1
    end

    subgraph fail[FAIL: incoming SSH port is blocked]
      direction LR
      client2 --> |22/tcp| fw2 --> sshd2
    end

  end

  linkStyle default stroke-width:4px
  linkStyle 0 stroke:yellow
  linkStyle 1 stroke-width:3px,stroke:green
  linkStyle 2 stroke:yellow
  linkStyle 3 stroke:red

  classDef Allow color:#0ff
  classDef Block color:#f00

  class grant Allow
  class fail Block

```

```mermaid
graph BT
  ssh_1(["web1:9090
        ssh_svr:22"])
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
graph 
  direction LR
  sshd(["sshd:22
        fport:80"])
  client(["client"])
  demo["web:8080"]
  remote((remote))

  subgraph main[Network Access: remote -> web:8080]
         
    subgraph intra[Intranet]
      client --> |8080/tcp| demo
    end

    subgraph cloud[Internet]
      sshd
      remote --> |80/tcp| sshd
    end

    client --> |22/tcp| sshd    
    
  end

  linkStyle default stroke-width:4px
  linkStyle 0 stroke:yellow
  linkStyle 1 stroke:yellow
  linkStyle 2 stroke:blue

  classDef Block color:#0ff
  classDef Title color:#f66

  class main Title
  class cloud,intra Block
  
```

## SSH Dynamic Port Forwarding

```mermaid

```
