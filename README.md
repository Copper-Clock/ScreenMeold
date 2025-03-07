[![balena deploy button](https://www.balena.io/deploy.svg)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/Copper-Clock/ScreenMe&defaultDeviceType=raspberrypi3)

# Screenly OSE - Digital Signage for the Raspberry Pi

[Which Screenly version is right for me?](https://www.screenly.io/screenly-ose-vs-pro/)

**PLEASE NOTE:** Screenly OSE and the commercial version of Screenly (formerly known as Screenly Pro) are **two completely separate products**. They **do not share any code base and behave very differently** both with regards to management and performance. Hence do not use one to evaluate the other.

Want to help OSE thrive? Support us using [GitHub Sponsor](https://github.com/sponsors/Screenly).

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=Copper-Clock/ScreenMe&type=Date)](https://star-history.com/#Copper-Clock/ScreenMe&Date)


## Disk images

~~The recommended installation method is to grab the latest disk image from [here](https://github.com/Copper-Clock/ScreenMe/releases).~~

## Installing on Raspbian/Raspberry Pi OS

The tl;dr for installing Screenly OSE on [Raspberry Pi OS](https://www.raspberrypi.com/software/) Bullseye Lite is:

```
$ bash <(curl -sL https://install-ose.srly.io)
```

**This installation will take 15 minutes to several hours**, depending on variables such as:

 * The Raspberry Pi hardware version
 * The SD card
 * The internet connection

During ideal conditions (Raspberry Pi 3 Model B+, class 10 SD card and fast internet connection), the installation normally takes 15-30 minutes. On a Raspberry Pi Zero or Raspberry Pi Model B with a class 4 SD card, the installation will take hours. As such, it is usually a lot faster to use the provided disk images.

## Installing with Balena

While you can deploy to your own Balena fleet, the easiest way to deploy using [Balena OpenFleets](https://hub.balena.io/organizations/screenly_ose/fleets).

## Upgrading on Screenly OSE

The releases are based on the [Sprints](https://github.com/Copper-Clock/ScreenMe/projects). At the end of each sprint, we merge the master branch (also known as the developer version), into the production branch and generate a new disk image.

Should you want to upgrade to the latest development version (for instance if you want to try a bug-fix), you can do this by simply re-running the installation script and select that you want to install the development version. Re-running the installation script should normally not take more than a few minutes (depending on how much changed).

To learn more about Screenly, please visit the official website at [Screenly.io](http://www.screenly.io).

[![An introduction to digital signage with Screenly OSE](http://img.youtube.com/vi/FQte5yP0azE/0.jpg)](http://www.youtube.com/watch?v=FQte5yP0azE)

Quick links:

 * [FAQ](https://support.screenly.io/hc/en-us/categories/360002606694-OSE)
 * [Screenly OSE Forum](https://forums.screenly.io/c/screenly-ose)
 * [Screenly OSE Home](https://www.screenly.io/ose/)
 * [Live Demo](https://ose.demo.screenlyapp.com/)
 * [QA Checklist](https://github.com/Copper-Clock/ScreenMe/blob/master/docs/qa-checklist.md)
 * [API Docs](https://ose.demo.screenlyapp.com/api/docs/)
 * [Developer Documentation](https://github.com/Copper-Clock/ScreenMe/blob/master/docs/developer-documentation.md)

Screenly OSE works on all Raspberry Pi versions, including Raspberry Pi Zero, Raspberry Pi 3 Model B, and Raspberry Pi 4 Model B.

## Dockerized Development Environment

To simplify development of the server module of Screenly OSE, we've created a Docker container. This is intended to run on your local machine with the Screenly OSE repository mounted as a volume.

Assuming you're in the source code repository, simply run:

```
$ docker-compose -f docker-compose.dev.yml up
```

## Running the Unit Tests

Start the containers.

```bash
docker-compose -f docker-compose.test.yml up -d
```

Run the unit tests.

```bash
docker-compose -f docker-compose.test.yml exec -T srly-ose-test bash ./bin/prepare_test_environment.sh -s
docker-compose -f docker-compose.test.yml exec -T srly-ose-test nosetests -v -a '!fixme'
```
