# Forthscale SSH
`fssh` is wrapper above `ssh` binary that allows easy ssh to AWS and Digital Ocean instances.
## Configuration
#### SSH Options
By default in `fssh` each SSH session starts with 2 SSH options: `-o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no`. This can be overridden using `FSSH_OPTIONS` environment variable.
#### SSH
`fssh` is using default SSH binary located at `/usr/bin/ssh`. This binary can be overridden by using `FSSH_SSH` environment variable.
#### Debug mode
By setting `FSSH_DEBUG` environment variable `fssh` will work in debug mode.
## AWS
### Configuration
#### AWS Profile
`fssh` in AWS mode works using [Named Profiles](http://docs.aws.amazon.com/cli/latest/userguide/cli-multiple-profiles.html), make sure to configure profile.
#### SSH Keys
`fssh` look for pem keys using *key name* that configured for each instance. The key should exists in global path that can be configured with `FSSH_KEY_DIR` environment variable (default is `~/.ssh/pem/`) and under directory with AWS Profile name with read only permissions.

### Limitations
AWS search is only using instance ID.

### Usage
```
fssh aws [profile_name] [region_name] [instance_id]
```

## Digital Ocean
### Configuration
#### SSH keys
Digital Ocean mode currently works with default user private key. Make sure servers in DO have correct computer public key.
#### Digital Ocean API
`fssh` uses Digital Ocean API to find servers. Set `DO_API_KEY` environment variable with correct API key.
### Limitations
Digital Ocean currently can discover `coreos` user and the fallback is local machine user.

### Usage
```
fssh do [instance_tags]
```
