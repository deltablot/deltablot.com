---
title: "What's new in eLabFTW 4.0.0"
date: 2021-05-14T02:12:55+01:00
draft: false
tags:
  - "elabftw"
  - "release"
---

Please note: while this post is already published, version 4.0.0 is not yet released as a stable version!

I'm very pleased to announce that [eLabFTW](https://www.elabftw.net), the free and open source electronic lab notebook version 4.0.0 is now available for everyone!

This new version is PACKED with new features!

You can see the complete changelog on the [release page](https://github.com/elabftw/elabftw/releases/tag/4.0.0). This blog post is more about going into details for some of the changes.

# How to update

Update like usual: [see documentation](https://doc.elabftw.net/how-to-update.html).

# New features

## Users features

* Experiments/items can no have a visibility of "user only", previously this corresponded to owner + admin(s).
* Blockchain timestamping with [Bloxberg](https://bloxberg.org). Click the icon with blocks in view mode to certify your results into the blockchain. It will create a zip file attached to the experiment that contains the certified pdf along with a certificate. Note that this action can take up to 30 seconds. You can certify as many times as you want.

{{< image "/img/blockchain-export.jpg" "bloxberg certify" "50">}}

* Use "Ctrl-Shift-d" to add the date on cursor, select the date format from your profile.
* New API endpoint for templates, a contribution by @m6121.

* New way to display experiments in tabular form, a contribution by Manuel Lera-Ramirez:

![tabular mode](/img/tabular-show.png)

Go into your User Control Panel and change the Display mode.

* Json metadata. Ok so this is a big one, basically now experiments, items and their templates have an extra column in the database of type "json". You can add whatever you want in that column. But the interesting part is if you add a key "extra_fields". This special key will be read by eLabFTW and its content will be displayed to the user as extra input fields. To use this feature you must display the JSON editor (it's a setting in the user control panel). You now have a new button on the right side: "Load metadata". Once clicked, the content of the json/metadata column will be loaded into the editor. Click "Tree" and select "Code" to access the raw code editor. Try pasting this json as example:

~~~json
{
  "extra_fields": {
    "pressure": {
      "type": "number",
      "unit": "Pa",
      "required": true,
      "value": "10"
    },
    "magnification": {
      "type": "select",
      "required": true,
      "options": [
        "10X",
        "20X",
        "20X High N/A"
      ],
      "value": "10X"
    }
  }
}
~~~

Click the Save button and reload the page, you will see this appear:

![metadata extra fields](/img/extra-fields.png)

When the values are changed, the values in the json are directly updated.

* New user option to include attached PDFs into the generated PDF (a contribution by Marcel Bolten).
* Ownership of database items can now be transferred (a contribution by Marcel Bolten).
* Accessibility (based on WCAG 2.1 guidelines) has been improved (was already pretty good). This means more contrast for instance.
* Experiments now have rating like items.
* Items now have elabid like experiments (and a share link button).
* Uploaded files filenames can now be edited.
* Mathjax is now properly rendered in PDFs (contribution by Marcel Bolten).
* You can now select if you wish to show entries outside of your team.
* When selecting multiple tags, it acts with an AND logic.
* Google API for drawing the chart in profile has been removed in favor of a pure CSS solution.

## Admin features

* Admin can now delete templates.
* Admin can prevent database items deletion via general setting.
* Admin can prevent users from creating tags.

## Sysadmin features

* You can now clear the "banned users" (after too many login attempts) from the sysconfig page.
* The minimum number of characters changed to trigger a revision creation can now be adjusted, a contribution by @m6121.
* Add autologout setting to force logout after inactivity.
* When using external login, you can now define the behavior if the user doesn't exist locally.
* You can display an announcement only on the login page.


## Dev stuff

Internally, the codebase evolved and uses new PHP 8 features like typed properties or constructor promotion. Work has also been done to prepare for a better API (v2). Documentation for contributing has been improved. Password hashing is now done with bcrypt (previously was salted sha-512). Cypress is now used for end to end testing and many more little things :)


# Conclusion

I would like to thank all the people that contributed to the code, opened issues and tested this new release.

Special thanks to the [sponsors](https://github.com/sponsors/NicolasCARPi) and to Marcel Bolten for his continuous quality contributions!

Now go upgrade your instance and if you're not the sysadmin, ask your sysadmin to upgrade to benefit from these new features and all the bugfixes!
