# Simple Home Assistant CLI-client

Copy the file ha-cmd.yaml.dist to ha-cmd.yaml and insert the correct base-url to your server and a valid token

# Usage

ha-cmd [-h] [--no-validate] {check,restart,reload,reboot,upgrade,stop} ...

    check               Validate config
    restart             Restart HA
    reload              Reload dynamic config. 
    reboot              Reboot HA-container (using docker-compose)
    upgrade             Reboot HA-container and pull new version (using docker-compose)
    stop                Stop HA

You can reload parts of the config (just like in the web ui)

Without an additional argument, _reload_ reloads all the parts.
Or you can specify

    automations         Reload automations
    scripts             Reload scripts
    groups              Reload groups
    customizations      Reload customizations
    core                Reload core (same as customizations)

optional arguments:

    -h, --help            show this help message and exit
    --no-validate         Skip config-validation

## Example

Validate the current config

    ha-cmd check

Reload (some of) the config (scripts, automatons, groups and customizations)

    ha-cmd reload 

Reload scripts only

    ha-cmd reload scripts

Upgrade to the latest docker image without first validating the current config

    ha-cmd upgrade --no-validate

This will work even if the current instance of HA has crashed or the UI is unavailable

