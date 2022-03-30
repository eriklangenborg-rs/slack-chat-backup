# slack-chat-backup
Backup your Slack chat messages (direct messages, group messages, joined channels) to your local computer without any extra permissions or apps.

# REQUIREMENTS

* BASH (`/bin/bash`)
* jq
* GNU's date
  - MacOS: `brew install coreutils`

# CONFIGURATION

By default, the program uses config file named `config.sh` in the program directory. There is a sample config file named `config_sample.sh`. You must fill `config.sh` file with proper settings for the program to work by following the steps below:

1. Login to your Slack workspace on your browser.

2. Enable `Web Developer >> Network` tool and refresh the workspace.

3. Copy the values for needed settings from browser to `config.sh` file.

![Configuration 1](images/configuration-1.png)
![Configuration 2](images/configuration-2.png)

*NOTE:* If config values are misapplied, be sure to clear the cookie .jar file cached on disk via `rm -rf cookies/*.jar`

# USAGE

```
./run.sh -h
Usage: ./run.sh [command] [options]

COMMAND:
    boot        Download account info and related users profile (meta data)
    sync        Download all messages (requires existing meta data)
    all         Perform all commands above in listed order
    test        Attempt to check system compatibility *DEFAULT*

OPTIONS:
    -c|--config Path to config file. Default: config.sh
    -d|--debug  Enable debug. Extremely verbose.
    -h|--help   Print this help
```

# HOW IT WORKS

The program uses provided Slack cookie and token and other variables to connect directly to Slack servers, retrieve chat messages and store in local directory in JSON format.
