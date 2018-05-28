This project was forked from dockito/vault

# Why ONVAULT

### The problem

- During docker build we want to avoid exposing our private keys to the different layers
- Private key was already securely loaded from a secrets management service, and there's no use for a running vault server (as required in dockito/vault)

### Solution

Using `ONVAULT` before any command that requires our private keys, such as

    RUN ONVAULT npm install --unsafe-perm

The `ONVAULT` script automatically loads to private key from the variables and removes the configuration after the given command is finished

<br />

## Configuration

### Variables

* `SSH_PRIVATE_KEY`

### Adding a host to known hosts

use `--add-host [hostname]` after `ONVAULT` and before your command.


## Usage

### On Alpine Linux

    # installs ONVAULT utility
    # https://github.com/do87/onvault
    RUN apk add -Uuv bash curl && \
        curl -L https://raw.githubusercontent.com/do87/onvault/master/ONVAULT > /usr/local/bin/ONVAULT && \
        chmod +x /usr/local/bin/ONVAULT
