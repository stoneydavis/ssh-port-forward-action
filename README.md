# SSH port forwarding action

GitHub action to forward a remote connection to a local port over SSH. 

## Prerequisites

You must have a passwordless SSH key set up on the remote server.


## Github Action Inputs

| Variable      | Description     |
|---------------|-----------------|
| `ssh-key`     | SSH private key |
| `ssh-host`    | SSH host        |
| `ssh-port`    | SSH port        |
| `ssh-user`    | SSH user        |
| `local-port`  | Local port      |
| `remote-host` | Remote host     |
| `remote-port` | Remote port     |

## Example Usage

```
jobs:
  job_id:
    steps:
    - uses: 'actions/checkout@v3'

    - uses: selfagency/ssh-port-forward-action@v1.0.1
      with:
        ssh-key: ${{ secrets.SSH_KEY }}
        ssh-host: your-host.com
        ssh-port: 22
        ssh-user: username
        local-port: 6379
        remote-host: localhost
        remote-port: 6379
        
    - run: 'redis-cli -p 6379 ping'
```

