---
title: "eLabFTW 3.4.0 is out!"
date: 2020-03-02T02:12:55+01:00
draft: false
tags:
  - "elabftw"
  - "release"
---

I'm very pleased to announce that eLabFTW version 3.4.0 is finally available for everyone!

This new version contains a lot of new things and a few fixes and improvements from the previous version. All users should upgrade!

This version took a long time to get out because it involved a lot of work to make some major changes. I'm hoping now to have much more frequent releases.

**WARNING**: to update, you need to call the `db:updateTo34` command once the container is updated (or the new files are pulled).

~~~bash
# Docker users (assuming the container is called elabftw)
docker exec -it elabftw bin/console db:updateTo34

# Non Docker users (from the elabftw folder)
php bin/console db:updateTo34
~~~

Note that for users with a recent install, just doing the normal `db:update` command will also work fine. But just to be sure, execute the `updateTo34` command.

You can see the complete changelog on the [release page](https://github.com/elabftw/elabftw/releases/tag/3.4.0). This blog post is more about going into details for some of the changes.

# Improvements

## Allow users to be in several teams

This feature was probably the most asked off all time! It is now possible to have users belonging to several teams. If a user is part of more than one team, upon login, the user will be asked in which team they want to be logged in.

Only Sysadmins can edit the teams of users as of now.

![many teams](/img/many-teams.png)

You can also add someone from another team in a team group!

## Permission system

The permission system now properly separates the reading rights, and the writing rights. And you can adjust it for each individual experiment/database item.

![edit permissions](/img/edit-permissions.png)

## Scheduler upgrade

The scheduler has been improved, with colors for the booked items and the possibility to link an experiment to a scheduled event!

## JSON editor

A JSON editor was added, it is disabled by default, so go into your Settings to enable it! This is a contribution from @shabihsherjeel :)

![json editor](/img/json-editor.png)

## Miscellaneous

* Sysadmin can restrict the email domain on registration.
* A new API endpoint was added to make a ZIP backup of experiments on a time period.
* The TODO list was improved
* and a lot of other changes...

# Developer corner

## Switch to Typescript

All the javascript has been converted to Typescript, a superset of JavaScript that allows strict typing. Here is how it works now:

* The Typescript code is in _src/ts_ folder
* When the build command is called, _tsc_ is executed to convert the _.ts_ files in _.js_ files
* Then _webpack_ is bundling the files together
* And finally, _babel_ is making sure that all the code is compatible with older browsers

The webpack build has also been improved. There is probably room for improvements but things are getting better at each release!

A new yarn command has been added:

~~~bash
# build and watch the changes
yarn watchjs
~~~

## Use SCSS for CSS

The CSS is now produced from several _.scss_ files located in _src/scss_. This allow the use of variables, loops and other things that were missing from plain CSS.

New yarn command:

~~~bash
# build the CSS and watch the changes
yarn watchcss
~~~

## Test setup

Now the acceptance and unit tests are run in temporary Docker containers that will install eLabFTW from scratch, run all the tests with Chrome and clean up everything upon exit.

## API testing

Before, the API was tested with a custom bash script, now it is using the API suite from Codeception (the testing framework used), and this allows much better testing!

The API tests are located in the _tests/api_ folder.
