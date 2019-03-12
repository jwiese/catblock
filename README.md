CatBlock
========
[![Build Status](https://travis-ci.org/CatBlock/catblock.svg?branch=master)](https://travis-ci.org/CatBlock/catblock)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/cc8d000f77bb427caa8b0293d9b5d225)](https://www.codacy.com/app/tomastaro/catblock?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=CatBlock/catblock&amp;utm_campaign=Badge_Grade)
[![GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://github.com/CatBlock/catblock/blob/master/LICENSE.txt)

## Overview
CatBlock (previously known as "AdBlock with CatBlock") is like an ad blocking extension, but instead of blocking ads it shows you pictures of cats by default (configurable).

You can also disable replacing ads by cats, so CatBlock can work as a standard ad blocking extension (useful for when you're doing presentations anywhere!)

If you want to find out the history of this extension, you can check it out [here](https://github.com/CatBlock/catblock/wiki/History).

## Goals
This project aims at maintaining and improving the original [CatBlock](http://catblock.getadblock.com) project by Michael Gundlach (the creator of [AdBlock](https://getadblock.com) and CatBlock), which is built on top of the AdBlock code.

AdBlock has recently switched to the Adblock Plus codebase in version 3.0, but instead of importing those changes to CatBlock, we think it would be better to improve the original codebase.

## Installation
CatBlock is available in [Chrome Web Store](https://chrome.google.com/webstore/detail/catblock/mdcgnhlfpnbeieiiccmebgkfdebafodo),
[Opera Extensions Store](https://addons.opera.com/sk/extensions/details/catblock/?display=en) and [Firefox Addons Store](https://addons.mozilla.org/en/firefox/addon/adblock-with-catblock/).

Right now, CatBlock is not available in the [Safari Extensions Store](https://safari-extensions.apple.com), or in the [Windows Store](https://www.microsoft.com/en-us/windows/windows-10-apps), but we are looking into releasing CatBlock there as well!

If you can't wait for an official release of CatBlock on Windows Store, [find out](https://github.com/CatBlock/catblock/wiki/Building-the-extension#in-microsoft-edge) how to sideload CatBlock on Edge right now.

## Supported browsers
CatBlock is compatible with following browsers:
- Chrome: 49+
- Opera: 35+
- Safari: 6+
- Firefox: 48+
- Edge: Windows 10 Anniversary - version 1607

## Tools we use
We use many different services to help keep CatBlock working! We use [Travis](http://travis-ci.org) to build new versions automatically for us.

We also have Travis connected to <a href="https://browserstack.com"><img src="https://bstacksupport.zendesk.com/attachments/token/q3lgvdc6t3gMJfqDUFkqsMgrP/?name=Logo-01.svg" alt="BrowserStack" width=70 href="https://browserstack.com"/></a>, to run a few automated unit tests for us. If "builds:passing" shows at the top of this README, then it's probably working fine, otherwise the current version of the code might not work so well.

## Developers

## Overview of additional modifications
The original Catblock has been modified with changes for use in biomedical informatics research. Major changes include:

- Improved display of ads. Ads are limited and restricted to try to fit more naturally into a given space than what catblock does.
- Clicking an ad now redirects to a page. Photos to display are pulled from a Flickr photostream which accepts the image title as the target URL for redirection.
- Added support for gif images
- Analytics to monitor research
- Various minor tweaks and adjustments to suit Catblock for this purpose.

### Settings
There have been 3 items added to the settings menu. These are:
 - User ID - Unique user identifier for analytics use
 - Total ads to display per page - Limits the total number of ads per page to this amount
 - Ads per ad group to display - Limits the number of ads per block

### Analytics

Implemented are some basic analytics that log which ads are shown and which the user clicks on. This is currently done using AWS to intercept and log requests.

The target URL's are located in `/catblock/contentscript.js:499`, for a displayed ad, and `312` for a clicked ad. These requests send a JSON POST request with a body of:
```
{
	"display_time": String,
	"user": String,
	"url": String
}
```
### Notes
- Chrome is the only supported browser
- Flickr image resizing is no longer functional. This means that images will need to be uploaded to Flickr in the desired size to work properly. This was disabled to allow gifs, which Flickr doesn't resize and will just return a static image. This can be changed back if needed in `catblock/channels.js`.


### How to build the extension or create a development environment?
The [development guide](https://github.com/CatBlock/catblock/wiki/Building-the-extension) will make your life easier if you need to build CatBlock or create an unpacked development environment and change the source code.

### Do you want to contribute?
If you want to contribute any improvements to the code, please go ahead and send us a pull request from a fork of this repo!

If we see that you are a dedicated contributor, we may provide you with contributor permissions.
The people to contact for this project are [@kpeckett](https://github.com/kpeckett) and [@tomasko126](https://github.com/tomasko126).

### Do you want to know more about our project?
If you want to keep an eye on CatBlock or even know more about it, check out our [Wiki page](https://github.com/CatBlock/catblock/wiki), where you can find all important information.

## Get in touch with us
[![Slack](http://catblock-slackin.herokuapp.com/badge.svg)](http://catblock-slackin.herokuapp.com)

We use Slack a lot - make an account at <http://catblock-slackin.herokuapp.com> and log in at <https://catblock.slack.com>. You can ask questions there (the main contributors are all in Europe, so anyone in Australia should expect a bit of a wait).
