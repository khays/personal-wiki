---
layout: post
title: User Management
tags: users groups umask unix
---

## Adding a user example

This is useful for adding a *git* user

    useradd -m git
    passwd git
    groupadd git #this might not be nesseary
    # now create a place to store the repo
    cd /
    mkdir shared/; mkdir shared/repos
    chmod ...; chgrp...; # make is to that the git group can rwx


## Add an existing user to an existing group

This will add khays to the group `corp_tech` (supplementary/secondary group)

    usermod -a -G corp_tech khays

## umask setting

This will make so that everytime you create a file it will make 770 which is what I want

    umask 007

If you drop this into the `~/.profile` file, than you should be good everytime something loads.
