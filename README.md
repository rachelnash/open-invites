# Slash command (with interactive message) blueprint

Use a slash command to create a helpdesk ticket in a 3rd-party system. Once it has been created, send an interactive message to the user with information about their ticket and a dropdown they can use to update the priority.

![image]()

## Setup

#### Create a Slack app

1. Create an app at api.slack.com/apps
1. Navigate to the OAuth & Permissions page and add the following scopes:
    * `commands`
    * `users:read`
    * `users:read:email`
1. Click 'Save Changes' and install the app

#### Run locally or [![Remix on Glitch](https://cdn.glitch.com/2703baf2-b643-4da7-ab91-7ee2a2d00b5b%2Fremix-button.svg)](https://glitch.com/edit/#!/remix/slack-slash-command-blueprint)
1. Get the code
    * Either clone this repo and run `npm install`
    * Or visit https://glitch.com/edit/#!/remix/slack-slash-command-blueprint
1. Set the following environment variables to `.env` (see `.env.sample`):
    * `SLACK_TOKEN`: Your app's `xoxp-` token (available on the Install App page)
    * `PORT`: The port that you want to run the web server on
    * `SLACK_VERIFICATION_TOKEN`: Your app's Verification Token (available on the Basic Information page)
1. If you're running the app locally:
    1. Start the app (`npm start`)
    1. In another window, start ngrok on the same port as your webserver (`ngrok http $PORT`)

#### Add a Slash Command
1. Go back to the app settings and click on Slash Commands.
1. Click the 'Create New Command' button and fill in the following:
    * Command: `/helpdesk`
    * Request URL: Your ngrok or Glitch URL + /commands
    * Short description: `Create a helpdesk ticket`
    * Usage hint: `[description of your problem]`
1. Save and reinstall the app

#### Enable Interactive Messages
1. Go back to the app settings and click on Interactive Messages.
1. Set the Request URL to your ngrok or Glitch URL + /interactive-message