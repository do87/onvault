This project was forked from dockito/vault

# Why OnVault

### The problem

- During docker build we want to avoid exposing our private keys to the different layers
- Private key was already loaded from a secrets management service

### Solution

Using `ONVAULT` before any command that requires our private keys, such as

    RUN ONVAULT npm install --unsafe-perm


## Configuration

### Environment variables

* `SSH_PRIVATE_KEY`
* `SSH_KNOWN_HOSTS`
