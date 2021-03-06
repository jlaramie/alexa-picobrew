# alexa-picobrew
All you need to integrate your [PicoBrew Zymatic](https://picobrew.com/Store/products/zymatic.cshtml) (and Pico?) with the Amazon Echo (Alexa)

**DISCLAIMER: I am not in any way affiliated with PicoBrew Inc. This is an UNSUPPORTED, UNOFFICIAL application written because I wanted it.**

# Usage
    You: "Alexa, ask PicoBrew..."

## Current Status
        "...what the current state is"
        "...what's the status"
        "...what it's doing"
        "...what the status is"

    Alexa: "Your machine is currently brewing 'Beer Name'. The current step is 'Step Name'"
    Alexa: "Your machine is currently Cleaning. The current step is 'Heat Water'"
    Alexa: "Your machine is idle"

## Time Left
        "...how much time is left"
        "...when this brew will end"
        "...when it will be finished"

    Alexa: "You are not currently brewing"
    Alexa: "You have been brewing for about 2 hours and 10 minutes. You have approximately 1 hour and 47 minutes left"

*NOTE: This is a rough estimate and doesn't take into account pauses, etc.*

## Last Brew

    "...when my last brew was"
    "...when the last brew was"
    "...when's the last time I brewed"
    "...when did I brew last"

    Alexa: "You have never brewed on this machine"
    Alexa: "Didn't you know? Your machine is currently brewing 'Hop Bomb 5000'. The current step is 'Dough In'"
    Alexa: "The last time you brewed was Last Wednesday at 4:36pm. It was called 'Nasty Boh'"
    Alexa: "The last time you brewed was December 25th, 2016 at 11:07am. It was called 'Meister Chow'"

## Did I Rinse?
    "...if I rinsed after my last brew"
    "...did I rinse after my/the last brew?"
    "...if I rinsed"

    Alexa: "No, You did NOT rinse after your last brew"
    Alexa: "You are brewing now. Though after your previous brew you did. Don't forget to rinse this time!"
    Alexa: "No you didn't, but you cleaned, so you're OK"

## Brews Since Cleaning
    "...how many times I have brewed since the last clean(ing)"
    "...how many brews since it was cleaned"
    "...how many brews I've done since it was cleaned"
    "......when it was last cleaned"

    Alexa: "You have never cleaned or brewed on this machine"
    Alexa: "You last cleaned Last Friday at 8:05pm. You have brewed one time since then"

## Future Features:

    **more to come**

# Limitations
**WARNING: This only works for Zymatics and only if you have ONE Zymatic**

I personally own a single Zymatic and zero Picos.
Therefore, I don't have the ability to work with/test a situation with more than one Zymatic or any Picos.

If you have more than one Zymatic, it will just pick the first one returned from the picobrew website.

If anyone out there wants to help me with that, please contact me by email: *tommck at gmail dot com*

# How it works
TODO

# Setup

## Building the code

* Install NodeJS (latest LTS is probably fine, though Amazon currently uses 4.2)
* Either download the code or use `git` if you're familiar.
* In the `alexa-picobrew` folder run `npm install` -- This will install all the dependencies
* Edit the `src/config.ts` file to the following fields:
  * appId - your Amazon Skill ID - **can be fake to start with, but will need to be updated before deploying to AWS**
  * picobrew.auth.user - the ID you use to login to the PicoBrew website
  * picobrew.auth.pass - the password for that ID
* run `npm run build` -- This should result in no errors
* run `npm run test` -- this will run unit tests (not real connection)

## Testing the code
In order to test everything **without** Alexa involved, you can run things from your own machine.

To do this, edit the `spec/picobrew-service.spec.ts` file and change the following line near the top of the file

```js
    var USE_FAKE_CALLS = true;
```
to
```js
    var USE_FAKE_CALLS = false;
```

This will cause the 'test' code to actually make calls to the PicoBrew website instead.

Now, if you run `npm run test`, all the tests will actually hit PicoBrew's servers.

## Create the Alexa Skill
TODO

## Create the AWS Lambda Function
TODO

## Connect the Skill -> Lambda
TODO

# TroubleShooting
First recommendation is to follow the instructions in the "Testing the code" section above to run then locally on your machine.

TODO: More Info

# Technologies
This is written using TypeScript and NodeJS.

# Acknowldgements
Thanks to the following for inspiring this project:
* [Ryan Graciano](http://ryangraciano.com) and his [echo-sonos](https://github.com/rgraciano/echo-sonos) project, and
* Todd Quessenberry and his [whatspicobrewing](https://github.com/toddq/whatspicobrewing) project
