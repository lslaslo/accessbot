# Configure AccessBot

There are multiple variables you could use for configuring AccessBot.

## Required configuration
* **SLACK_TOKEN**. Slack Bot User OAuth Token
* **SDM_ADMINS**. List of Slack admins, although it's not required, this users are usually SDM admins too
* **SDM_API_ACCESS_KEY**. SDM API Access Key
* **SDM_API_SECRET_KEY**. SDM API Access Key Secret

## Internal configuration
* **LOG_LEVEL**. Logging level. Default = INFO
* **SDM_DOCKERIZED**. Logging type. Default = true (_when using docker_), meaning logs go to STDOUT

## Bot configuration
The following variables can be changed at runtime via slack -by an SDM_ADMIN- using the `plugin config AccessBot` command:
* **SDM_ADMIN_TIMEOUT**. Timeout for a request to be manually approved. Default = 30 sec
* **SDM_SENDER_NICK_OVERRIDE**. Nickname to be used for all requests. Default = None (_useful for testing_)
* **SDM_SENDER_EMAIL_OVERRIDE**. Email to be used for all requests. Default = None (_useful for testing_)
* **SDM_AUTO_APPROVE_ALL**. Flag to enable auto-approve for all resources. Default = false
* **SDM_AUTO_APPROVE_TAG**. Tag to be used for auto-approve resources. Default = None
* **SDM_HIDE_RESOURCE_TAG**. Tag to be used for hidden resources. Default = None

See image below for more information:

![image](img/bot-config.gif)

### Some tricks
* Use `plugin config AccessBot {}` for setting config to initial state
* Use `plugin info AccessBot` for showing all configurations

### Known issues
* When using `plugin config` from a Mac, you would need to disable: 
`System Preferences > Keyboard > Text > Uncheck "Use smart quotes and dashes`. The `config` command fails to understand quotes as unicode characters.
* While waiting for manual approvals, any admin command (e.g. `plugin config`) will hang until the `ADMIN_TIMEOUT` expires ([issue #45](https://github.com/strongdm/accessbot/issues/45))