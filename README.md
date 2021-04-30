# AccessBot

AccessBot is a chatbot that manages access to strongDM (SDM) resources, initially via Slack

## Table of Contents
* [Installation](#installation)
* [Getting Started](#getting-started)
* [Contributing](#contributing)
* [Support](#support)

## Installation
In order to install AccessBot you need to provide -at least- the following required variables:
* **SLACK_TOKEN**. Slack Bot User OAuth Token
* **SDM_ADMINS**. List of Slack admins, although it's not required, this users are usually SDM admins too  
* **SDM_API_ACCESS_KEY**. SDM API Access Key
* **SDM_API_SECRET_KEY**. SDM API Access Key Secret

For a full list of configuration variables please read: [Configure AccessBot](docs/CONFIGURE_ACCESSBOT.md)

Detailed instructions about how to configure Slack and SDM for AccessBot can be found here:
* [Configure Slack](docs/CONFIGURE_SLACK.md)
* [Configure SDM](docs/CONFIGURE_SDM.md)

For starting the bot enter all required variables in [docker-compose.yaml](docker-compose.yaml) and execute:
```
./docker-start.sh
```

The bot would start running in the background. In order to check logs.
```
docker logs accessbot_accessbot_1
```

If you want to install and execute the bot locally, please refer to: [Configure Local Environment](docs/CONFIGURE_LOCAL_ENV.md)

## Getting Started
Once AccessBot is up and running, you can add it as an app or to a channel and start using it!

First, check the bot and Slack interconnectivity state:

![image](docs/img/health-check.gif)

You would expect to see no error in your logs and the messages **Yes I am alive** and plugin available.

If that's the case, enter any of the following commands:
* `help`. Show available commands help
* `show available resources`. Show all available resources
* `access to resource-name`. Grant access to a resource

For example:

![image](docs/img/main-commands-tutorial.gif)

## Optional access configuration

1. Set `SDM_AUTO_APPROVE_ALL=true` to disable approval entirely.
2. Use the strongDM CLI or SDK to add the following tags to individual resources:
      - `SDM_AUTO_APPROVE_TAG=auto-approve` -- automatic approval for this resource
      - `SDM_HIDE_RESOURCE_TAG=hide-resource` -- resource is not displayed via `show` command; any access request auto-fails

For more information, please refer to the [detailed guide for access configuration](docs/ACCESS_CONFIGURATION.md).

## Troubleshooting

A list of typical issues and resolutions can be found [here](docs/TROUBLESHOOTING.md).

## Contributing
In case you want to contribute to the project, please check our [guidelines](CONTRIBUTING.md).

## Support
In case you need support, please check our [support](SUPPORT.md) document.
