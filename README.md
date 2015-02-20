# slack-oldbot

A Slack bot that warns you when a link has already been posted.

![screenshot](https://github.com/kewah/slack-oldbot/raw/master/screenshot.png)

### Scripting

Local scripts must be included at `scripts/*.coffee`.  
[Scripting Guide](https://github.com/github/hubot/blob/master/docs/scripting.md)

### hubot-scripts

To enable scripts from the hubot-scripts package, add the script name with
extension as a double quoted string to the `hubot-scripts.json` file in this
repo.

### external-scripts

Hubot is able to load scripts from third-party `npm` package. Check the package's documentation, but in general it is:

1. Add the packages as dependencies into your `package.json`
2. `npm install` to make sure those packages are installed
3. Add the package name to `external-scripts.json` as a double quoted string

You can review `external-scripts.json` to see what is included by default.

### Testing your bot locally

```
HUBOT_SLACK_TOKEN=xoxb-YOUR-SLACK-TOCKEN ./bin/hubot --adapter slack
```
[source](https://github.com/slackhq/hubot-slack/blob/master/README.md#testing-your-bot-locally)

## Deploying to Heroku

This is a modified set of instructions based on the [instructions on the Hubot wiki](https://github.com/github/hubot/blob/master/docs/deploying/heroku.md).

- Follow the instructions above to create a hubot locally
- Edit your `Procfile` and change it to use the `slack` adapter:

```
web: bin/hubot --adapter slack
```

- Install [heroku toolbelt](https://toolbelt.heroku.com/) if you haven't already.
- `heroku create my-company-slackbot`
- `heroku addons:add redistogo:nano`
- Activate the Hubot service on your ["Team Services"](http://my.slack.com/services/new/hubot) page inside Slack.
- Add the [config variables](#adapter-configuration). For example:

```
% heroku config:add HEROKU_URL=http://my-company-slackbot.herokuapp.com
% heroku config:add HUBOT_SLACK_TOKEN=xoxb-1234-5678-91011-00e4dd
```

- Deploy and start the bot:

```
% git push heroku master
% heroku ps:scale web=1
```

[source](https://github.com/slackhq/hubot-slack/blob/master/README.md#deploying-to-heroku)

## Restart the bot

You may want to get comfortable with `heroku logs` and `heroku restart`
if you're having issues.

## Guides

- [Hubot docs](https://github.com/github/hubot/tree/master/docs)
- [Hubot slack](https://github.com/slackhq/hubot-slack)
