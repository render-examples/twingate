# Twingate on Render
This repository demonstrates how to deploy the [Twingate Zero Trust solution](https://www.twingate.com) on the Render cloud. By using Twingate, you'll be able to directly access private resources that aren't exposed to the public web, such as [Render Private Services](https://render.com/docs/private-services) or [Render PostgreSQL](https://render.com/docs/databases) instances.

Twingate themselves have created [an easy video walkthrough](https://www.youtube.com/watch?v=fUukhwxKDoc) of deploying a Twingate connector into Render that's worth checking out if you'd like more information.

## Example Deployment
- _Log into_ your Twingate admin panel.
- _Create a network_ (**Network > Remote Networks** _(right sidebar)_ **> Add**) to continue. In the "type" dropdown select "Other" and name it `Render` (or whatever is meaningful to you).
- Click **Deploy Connector** in the right sidebar to..._deploy the connector_!
  - Select **Docker**, and _leave other settings as default_.
  - Click **Generate Tokens**, which will prompt you to re-authenticate your Twingate account.
  - You'll now have an `Access Token` and a `Refresh Token`. _Keep these handy_.
- Let's _launch this into Render_! <a href="https://render.com/deploy?repo=https://github.com/render-examples/twingate/tree/main"><img src="https://render.com/images/deploy-to-render-button.svg" alt="Deploy to Render"></a>
  - **One note:** for business continuity and source code control purposes, you might want to fork this repository, in which case you'd want to go to [Render Deploy](https://render.com/deploy) instead and specify your forked repo.
  - You'll be asked to input a few things:
    - Your Twingate account URL, e.g. _https://renderexamples.twingate.com_
    - Your access token, from the above step
    - Your refresh token, from the above step
- Now, once this is live, you'll have a Twingate connector and two services. _Connect to Twingate now_ by following the instructions in [the Twingate docs](https://docs.twingate.com/docs/connect-to-twingate).
- In the [Render dashboard](https://dashboard.render.com/), _navigate to the service you'd like to expose via Twingate_.
  - Beneath the name of the service, you should see **Service Address**, which will be something like `twingate-private-service-a1b2:80`; click the Copy button next to this.
  - Open a new tab in your browser, type `http://`, and paste in the address.
- Similarly, you can connect to a Render PostgreSQL instance.
  - On the PostgreSQL service page, under **Connections**, you'll find the **Hostname** for the PostgreSQL instance.
