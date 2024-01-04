# SonnenBatterie Control Flows with Node-RED

This repository contains Node-RED control flows I use for controlled charging and discharging, in my case with the help of Tibber dynamic pricing.

### Prerequisites

[Node-RED](https://nodered.org/) works on a variety of systems, with a variety of [installation options](https://nodered.org/docs/getting-started/) (as system service, as a docker container [I prefer [Podman](https://podman.io/), by the way], etc.)

For those of you who don't really care (or don't have experience with any of these steps, which is completely fine...) and just want to run this flow, I put together a little intro on how to  
Step 1) [Setup a Raspberry Pi for this](./docs/setup/pi/install-pi.md)  
Step 2) [Install Node-RED on that Raspberry](./docs/setup/nodered/install-nodered.md)  
Step 3) [Install the Flow](./docs/setup/flow/import-flow.md)  

It's really quite straightforward and easy to do. 


## The Node-RED Flow

You can start with some background information, motivation and general ideas, then look at how "cheap Hours" are calculated (when does it make sense to charge or discharge) and then how this thing is configured...

Or you can jump directly to the [Overview](./docs/overview.md) and read up on the details later

1) [Background](./docs/background.md)
2) [How do we calculate what is "cheap"](./docs/calculation.md)
3) [Controlling Charging and Discharging](./docs/charging-discharging.md)
4) [Configuration (Tibber and SonnenBatterie)](./docs/configuration.md)


Have fun - and leave an issue or a note (in discussions) if you have a problem or an idea how things could be improved. Or, fork it and create a PR.

Either way - enjoy.

Cheers,

Markus






