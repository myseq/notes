## Diagrams

```mermaid
  graph LR;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
```

```mermaid
graph LR
    A[Start] --> B[Process 1]
    B --> C[Process 2]
    C --> D[End]
```

```mermaid
graph LR
    A[client] --> |dport:8080| A
    A ---- B[firewall] --> |dport:22| C[ssh_server]
    C --> |dport:8080| D[target_svr]
```

```mermaid
graph LR
    A[client] --> |dport:8080| A
    A ---- B[firewall] --> |dport:22| C[ssh_server]
    C --> |dport:8080| C

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

