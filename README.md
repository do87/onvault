This project was forked from dockito/vault

# Why ONVAULT

### The problem

- During docker build we want to avoid exposing our private keys to the different layers
- Private key was already securely loaded from a secrets management service, and there's no use for a running vault server (as required in dockito/vault)

### Solution

Using `ONVAULT` before any command that requires our private keys, such as

    RUN ONVAULT npm install --unsafe-perm

The `ONVAULT` script automatically loads to private key from the environment and removes the configuration after the given command is finished

<br />
## Configuration

### Environment variables

* `SSH_PRIVATE_KEY`
* `SSH_KNOWN_HOSTS`
