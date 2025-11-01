+++
date = '2025-11-01T10:45:04+08:00'
draft = true
title = 'Using Cron to Schedule a Linux_Machine'
+++

## Cron: linux basic settings

Cron is a time-based job scheduler. You can set some commands to be done at a certain time or by a certain interval by installing and configuring it on a linux machine.

### Syntax

The stars **\*** (asterisks) and commands on the header is the format of each cron task that you will create. It consists mainly of six parts, with the first five parts determine the job timing (reference [here](https://pimylifeup.com/cron-jobs-and-crontab/)).

| * | * | * | * | * |  Command |
|----|----|----|----|----|----|
|Minute(0-59)|Hour(0-23)|Day of the Month(1-31)|Month(1-12)|Day of the week(0-6)|command to run|


### Examples

You can use `crontab -e` to select an editor and start edit the crontab list.

- Run every minute on each day

    ```bash
    * * * * * [command]
    ```
- Run every Monday, Wednesday, Friday at midnight
    ```bash
    0 0 * * 1,3,5 [command]
    ```

- More at [here](https://pimylifeup.com/cron-jobs-and-crontab/).


### Editing and generating configuration

[The pimylifeup site ](https://pimylifeup.com/cron-jobs-and-crontab/) provides a crontab generator which you can use to create your own configuration and has more detailed guides and examples.

