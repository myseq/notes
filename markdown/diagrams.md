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
    A[client] -- 8080/tcp --> A[client]
    A[client] ---- B[firewall] -- 22/tcp --> C[ssh_server]
    C -- 8080/tcp --> D[target_svr]

```


## SSH Local Port Forwarding

SSH local port forwarding allows you to securely access a service running on a remote server through an encrypted SSH tunnel.

```mermaid
graph LR
    A[Your Local Machine] -->|1. SSH Connection| B[Remote Server]
    B -->|2. Local Port Forwarding| C[Service:localhost:8080]
```
