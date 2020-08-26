---
title: "What's new in eLabFTW 3.5.0"
date: 2020-08-25T02:12:55+01:00
draft: false
tags:
  - "elabftw"
  - "release"
---

I'm very pleased to announce that eLabFTW version 3.5.0 is available for everyone!

This new version contains a lot of new things and a few fixes and improvements from the previous version. All users should upgrade!

You can see the complete changelog on the [release page](https://github.com/elabftw/elabftw/releases/tag/3.5.0). This blog post is more about going into details for some of the changes.

# How to update

Update like usual: [see documentation](https://doc.elabftw.net/how-to-update.html).

# New features

## Enforce read/write permissions by admin

The Admin of a team can now enforce read and write permissions for experiments of users in their team.

![enforce permissions](/img/permissions-enforce.png)

This setting is available from the Admin panel, first tab. Use it if you wish to make sure users can't change permissions on experiments.

## Show unfinished steps on Todolist

The Todolist is now displaying any unfinished steps you might have in experiments. This is useful to get an instant view on what needs to be done for several experiments.

![unfinished steps](/img/unfinished-steps.png)

Note that you can finish the steps (check the box) from the Todolist or from the view mode of an experiment (previously it was only possible from edit mode).

## Steps editing and reordering

Steps can now be edited and reordered. To edit a step, simply click on its text in edit mode. To reorder, grab it by the reorder icon and move it around.

{{< video "step-edit-reorder" >}}

## Pinned experiments/items

You can now "pin" a favourite entry to make sure it's always visible in show mode.

From the view mode, click the "pin" icon on the top right:

{{< video "toggle-pin" >}}

Now go back to show mode and you will see your pinned experiments (works also for items) on top of the list:

![pinned experiments](/img/pinned-experiments.png)

## Generate a single PDF from multiple selection

Thanks to a contribution from Marcel Bolten, it is now possible to make a single PDF from a selection of several experiments/items.

Select the entries you would like to export from show mode and select PDF from the Export menu.

Note that it is now also possible to export as JSON from this Export menu.

## Allow file upload with copy/paste

Thanks to a contribution from Sherjeel Shabih, you can upload a file by simply pasting it in the text editor!

## Show related items directly

Another contribution from Marcel Bolten: display the related experiments from the view and edit mode of an item:

![show related](/img/show-related.png)

## Add template permissions

Thanks to a contribution from Max Schröder and Farrukh Faizy, the templates now also have their permission system and you can decide which template you want to show to the world and which you wish to keep secret.

{{< video "template-perm" >}}

Notice how the template submenu has been improved, with a real Create new button and bigger click zones for templates! :)

# Improvements

This release contains multiple little improvements/bugfixes here and there, see the complete changelog on the [release page](https://github.com/elabftw/elabftw/releases/tag/3.5.0) for a complete list.

# Stuff for sysadmins

This will only interest Sysadmin users.

## Breaking change with the logs (only for Docker)

Previously the access and error logs from the webserver (nginx) were stored in the container (in /var/log/nginx). This was a problem because unless you mounted these folders as a volume, logs were lost on container change.

Now the logs are sent to stdout and stderr and to access them you can use `docker logs elabftw` (assuming your container is named elabftw). This is considered as best practice in the container world.

To filter out the access logs and focus on the notice/warning/error messages, use this: `docker logs -f elabftw 1>/dev/null`. The `-f` flag will follow output and display it when it arrives. See the [docker logs documentation](https://docs.docker.com/engine/reference/commandline/logs/) to learn more about this command.

## Fix the SAML logout

The logout button now will properly make a SAML logout request if the user is logged through SAML.

## Add external authentication support

Thanks to a contribution from Emmanuel Dreyfus, it is now possible to allow the webserver to provide authentication information. Check out these new settings from the Sysadmin panel.

## Add possibility to configure a user and group for nginx

Thanks to a contribution from François Prud'homme, the docker image can be configured to enforce a particular user/userid (and group/groupid) for the nginx user. This is useful if you're using a server picky about users (using NFSv4 for instance).

# Conclusion

As you can see, this release is full of new things and improvements asked by the community of users.

I would like to thank all the people that contributed to the code, opened issues and tested this new release.

Special thanks to the [sponsors](https://github.com/sponsors/NicolasCARPi)! ;)

Now go upgrade your instance and if you're not the sysadmin, ask your sysadmin to upgrade to benefit from these new features!
