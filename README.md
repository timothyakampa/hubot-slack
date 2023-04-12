hubot-slack
==============

This is a docker image repo for hubot push train running with a [hubot-slack](https://github.com/slackhq/hubot-slack) adapter.

# Acknowledgements

Forked from [jordan/hubot-slack](https://github.com/jjethwa/hubot-slack) and based on [hubot-rocketchat](https://github.com/RocketChat/hubot-rocketchat) 

# Automated build

```
docker pull timothyakampa/hubot-slack:1.0.0
```

# Image details

1. Based on [node:12.22.9-alpine3.15](https://hub.docker.com/_/node/)
1. Hubot + hubot-slack adapter
1. Supply HUBOT_SLACK_TOKEN or you won't get too far :)
1. hubot might take a few minutes to connect to slack as it pulls the necessary node.js modules at startup
1. hubot must be invited to channels
1. Official hubot script repo: [https://github.com/hubot-scripts](https://github.com/hubot-scripts)

# Usage

You must first add the Hubot Slack app to your team to obtain a token.  Search for it here [https://slack.com/apps](https://slack.com/apps)

## Start hubot-slack with your own [scripts](https://github.com/github/hubot/blob/master/docs/scripting.md)
```
docker run -d --name "hubot" -e HUBOT_SLACK_TOKEN=MY_HUBOT_SLACK_TOKEN -v /path/to/hubot/volume:/home/hubot/scripts jordan/hubot-slack:latest
```

## Start hubot-slack with the help and [pugme](https://github.com/hubot-scripts/hubot-pugme) scripts
```
docker run -d --name "hubot" -e HUBOT_SLACK_TOKEN=MY_HUBOT_SLACK_TOKEN -e EXTERNAL_SCRIPTS=hubot-help,hubot-pugme jordan/hubot-slack:latest
```

# Environment variables
```
HUBOT_SLACK_TOKEN - Your hubot slack token
ENV HUBOT_NAME - myhubot (default)
ENV HUBOT_OWNER - none (default)
ENV HUBOT_DESCRIPTION - Hubot (default)
ENV EXTERNAL_SCRIPTS - hubot-help,hubot-pushbot (default).  Do not add hubot-slack to this list as it is already installed and enabled in the container.
```

# Volumes
```
/etc/hubot/scripts
```
