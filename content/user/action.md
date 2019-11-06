---
title: "Action Layer"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 4
summary: Different option to log and help your documentation
---

LeL gives you a few tools to track certain activities:

- CLI tracking
- Milestone tracking
- Screen tracking

## CLI tracking

Inside the `_lel-simple-logger` folder you'll find the `logger.src.sh` script. This simple logger provides mainly three functions, which were explained below.

In order to enable the logger simply specify the following environment variables and source the file. This can also be done in the respective `.bashrc`, `.zshrc`, `~/.config/fish/config.fish` or `$HOME/.profile` file.

```bash
export MISATO_LOGDIR="<log-dir>"
export MISATO_LOGGER="<arbitrary-non-empty-value>"
source logger.src.sh
```

If enabled all commands will be logged into the specified `MISATO_LOGDIR` in json, including the terminal, user and timestamp information. The current status if the logging is enabled or not can easily be identified through the terminal prefix. If you want to toggle the logger the function `toggle_misato` can be used.

![pic](/user/pic_logging.png)

Additionally the logger and also be configured to log requests to LeL (remote). If not all commands should be sent to the server, then `MISATO_FILTER` value can be set, which acts as a regex begin filter. In the following setting only commands will be sent to LeL if the command begins with proxychains4.

The endpoint can be specified via the `MISATO_OPERATORAPI` variable.

```bash
 export MISATO_OPERATORKEY="<generated-uuid>"
 export MISATO_OPERATORAPI="https://127.0.0.1:8888"
 # can be used to send only commands, which begins with "proxychains4
 export MISATO_FILTER="proxychains4"

```

**Note**: Currently `MISATO_OPERATORKEY` is not used, but authentication is planned in the upcoming v0.0.2 version.

The local directory can be specified in LeL. This allows the search within the commands and is very helpful if passwords or commands are used in a team environment.

Similar to the `Content-Search` the operator is able to search for a specific previously logged command via the command search.

![pic](/user/pic_command-search.png)

## Milestone tracking

During assessments it is often the case that something you tried is not working, but when it does you are thrilled and often go inside the rabbithole until you noticed - wait ?! What did i do and how did i come this far !

Therefore milestones are introduced. Milestones is an event, which contains a message and a timestamp. These milestones (similar to bread crumbs) can help you to answer the question how you move from a to z. To create a new milestone the function `milestone_log` can be executed, once the logger is sourced.

![pic](/user/pic_milestone-log.png)

**Examples**:

- Finding a SQL-Injection: Great! `sql-injection:www.example.com`
- Begin password spraying: `spray:Spring2019`
- RDP to a system: `rdp:example.com`
- Code review: `deser-potential:readObject:/src/code/api.java:AllowRequest:34`

LeL got you covered through the `Chronic` view, when trying to visualize these data.

![pic](/user/pic_chronic.png)

If a day is selected all milestones are displayed for this specific day in a chronological order. This helps tremendously if a client/managment ask, what activities were done and what results were achieved.

![pic](/user/pic_milestone.png)

Since both cli and milestone logs contain the timestamp they can easily be correlated. Through clicking the little icon the `Commands` view appear, showing all commands after/before a specific milestone including the operator.

![pic](/user/pic_commands.png)

## Screen tracking

**Note**: While it technically works the screen tracking needs to be optimized first. Hopefully this can be achived in the `v0.0.2` release.

The final option of tracking is the screen recording via LeL.

![pic](/user/pic_settings.png)

In the settings tab of the main menu several options are available, which allow you to start/stop the recording, specifying the framerate, as well as the interval of the video.

This is important to keep and sync small videos (which can be deleted if nothing happened) and still is able to reproduce and see all activities for the assessment.

Previously inside the `Milestone` view, each link can be clicked, which jumps to the specific point, when the milestone happened. This led you easily see what happened at the milestone. Documentation done _drops mic_

![pic](/user/pic_video.png)

But test it for your own :)
