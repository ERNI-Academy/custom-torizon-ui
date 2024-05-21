# Toradex Custom Web UI

This repository contains code for an example of a custom web user interface (UI) for the [Torizon](https://www.torizon.io/) [Web API](https://app.torizon.io/api/docs/) of [Toradex](https://www.toradex.com/).
The [torizon-openapi.yaml specification can be downloaded from here](https://app.torizon.io/api/docs/torizon-openapi.yaml).
This example application aims to show the key features of the [torizon api](https://app.torizon.io/api/docs/).

Like:
* Show all registered devices of your torizon repository
* Show device data
* Show device metrics
* Show all available packages for a device (OS, Bootloader, Application)
* Show how to perform an application update
> [!IMPORTANT]  
> If you want to test the application update, make sure that your torizon repository 
> provides the needed docker-compose files for the update.  
> [How to upload docker compose to torizon repository](https://developer.toradex.com/quickstart/torizon-platform/update-application/?module=verdin_imx8mp&carrier=yavia&host=linux&os=torizon&learning_path=torizon_lessons)  
> Toradex provides a [docker-compose.yml](https://docs.toradex.com/112746-quickstart-docker-compose-example-arm64.yml) file, which can be used for testing purpose.  
> And to switch the applications you can use [this](https://github.com/treyyoder/quakejs-docker) 


## Prerequisites

**This project depends on :**

* [nodejs](https://nodejs.org/en)

**Although any enviroment can be used, it is recommended to use the develpment setup**

* [vscode](https://code.visualstudio.com/)
* Ubuntu 20.x, or
* Windows (using WSL2 (Ubuntu 20.x)) \
(For a detailed description see: [WSL](https://learn.microsoft.com/de-de/windows/wsl/setup/environment) )

> [!TIP]  
> If you are facing [internet connection issues under WSL](https://stackoverflow.com/questions/62314789/no-internet-connection-on-wsl-ubuntu-windows-subsystem-for-linux) add "nameserver 8.8.8.8" to your /etc/resolv.conf
> or set "networkingMode=mirrored" to your [wslconfig](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#wslconfig)

### Torizon prerequisites

* minimum one device provisioned for torizon.io
  * [How-To provision a device](https://developer.toradex.com/torizon/torizon-platform/devices-fleet-management#provisioning-a-single-device)
* valid Torizon API token, which can be generated from a valid Torizon API Client
  * [How-To create an API client](https://developer.toradex.com/torizon/torizon-platform/torizon-api/#how-to-use-torizon-cloud-api)
  * [How-To get an API token](https://developer.toradex.com/torizon/torizon-platform/torizon-api/#get-a-token)

## Getting Started

To get started with the Toradex Custom Web UI, follow these steps:

1. Clone the repository:

   ```bash
   git clone git@github.com:ERNI-Academy/custom-torizon-ui.git
   ```

2. Install [node](https://nodejs.org/en/learn/getting-started/introduction-to-nodejs) and npm

   ```bash
    sudo apt install nodejs
    node -v  // has to be minimum > 14.x.   
    sudo apt install npm 
    npm -v  // has to be minimum 8.5.1
    ```

3. Install the dependencies via npm

   ```bash
   npm install & npm update
   ```

   This should install the following packages [expressjs](https://expressjs.com/en/starter/hello-world.html), [nunjucks](https://mozilla.github.io/nunjucks/getting-started.html), [axios](https://axios-http.com/docs/intro), [dotenv](https://github.com/motdotla/dotenv).


4. Create a `.env` file in the root directory of your project and add your torizon api token to it, using the following syntax:

   ```plaintext
   TORIZON_API_TOKEN=your_token
   ```

> [!IMPORTANT]  
> If your facing a 401 HTTP error. Ensure to have a valid API Bearer token.
> See [How-To get an API token](https://developer.toradex.com/torizon/torizon-platform/torizon-api/#get-a-token)

5. Start the app

    ```bash
    node run.js
    ```

6. Open your browser with [http://localhost:3000/](http://localhost:3000/)

## Directory layout

```plaintext
   .
   ├── __test__           # the tests
   ├── public             # all static resources for the web pages (e.g images, libs, ...) 
   ├── routes             # backend implementation, handle the requests and respond with html pages
   ├── utility            # helper modules
   ├── views              # html templates (the UI without data)
   ├── app.js             # defines the expressjs application, but does not start it
   ├── package.json       # root of every Nodejs project, info about app, modules and packages, defines all npm scripts
   |── README.md          
   ├── run.js             # starts the application 
   ├── torizon_api.js     # encapsuling a request client for the Torizon API
```

## Customization

You can add your own device images to the "public/img" folder and set the reference to your images via the "addDeviceImage()" function, which can be found in every HTML file.

   ```HTML
   <script>
      function addDeviceImage() {
            var deviceImage = document.getElementById("device_preview");
            var deviceImageSrc = "/public/img/robot_icon.png";  // TODO: replace with your device image
            ...
      }
   </script>
   ```

## Development

1. For the tests, you will need a node version > 14.x.
   Or you will see

   ```plaintext
   run.js:135 unexpected token if (error?.stack)"
   ```

   Install nvm, to update the nodejs version :

   ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
    //restart vscode 
    nvm install --lts //to download the latest long time supported nodejs version 
    nvm install node //to install the latest lts nodejs version 
   ```

2. For development run

   ```bash
    npm run development //to start with nodemon, to see real time changes 
   ```

3. For tests run

   ```bash
    npm test
   ```

4. For code coverage run

   ```bash
    npm run coverage
   ```

## Contributing

Please see our [Contribution Guide](CONTRIBUTING.md) to learn how to contribute.

## License

![MIT](https://img.shields.io/badge/License-MIT-blue.svg)

Copyright © 2024 [ERNI - Swiss Software Engineering](https://www.betterask.erni)

## Code of conduct

Please see our [Code of Conduct](CODE_OF_CONDUCT.md)

## Stats
![Alt](https://repobeats.axiom.co/api/embed/8e806e36a58323efc8f2eb4dc55757c0dd755ea4.svg "Repobeats analytics image")

## Follow us

[![Twitter Follow](https://img.shields.io/twitter/follow/ERNI?style=social)](https://www.twitter.com/ERNI)
[![Twitch Status](https://img.shields.io/twitch/status/erni_academy?label=Twitch%20Erni%20Academy&style=social)](https://www.twitch.tv/erni_academy)
[![YouTube Channel Views](https://img.shields.io/youtube/channel/views/UCkdDcxjml85-Ydn7Dc577WQ?label=Youtube%20Erni%20Academy&style=social)](https://www.youtube.com/channel/UCkdDcxjml85-Ydn7Dc577WQ)
[![Linkedin](https://img.shields.io/badge/linkedin-31k-green?style=social&logo=Linkedin)](https://www.linkedin.com/company/erni)

## Contact

📧 [esp-services@betterask.erni](mailto:esp-services@betterask.erni)
