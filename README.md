# SSH port forwarding action

GitHub action to forward a remote connection to a local port over SSH. 

## Prerequisites

You must have a passwordless SSH key set up on the remote server.


## Github Action Inputs

| Variable      | Description     |
|---------------|-----------------|
| `ssh_key`     | SSH private key |
| `ssh_host`    | SSH host        |
| `ssh_port`    | SSH port        |
| `ssh_user`    | SSH user        |
| `local_port`  | Local port      |
| `remote_host` | Remote host     |
| `remote_port` | Remote port     |

## Example Usage

```
jobs:
  job_id:
    steps:
    - uses: 'actions/checkout@v4'

    - uses: stoneydavis/ssh-port-forward-action@v1.0.0
      with:
        ssh_key: ${{ secrets.SSH_KEY }}
        ssh_host: your-host.com
        ssh_port: 22
        ssh_user: username
        local_port: 6379
        remote_host: localhost
        remote_port: 6379
        
    - run: 'redis-cli -p 6379 ping'
```

