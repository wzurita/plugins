# FileBot Docker

## filebot

The [`filebot`](https://www.filebot.net/cli.html) command-line tool.

```
docker run -it -v $PWD:/volume1 -v data:/data rednoah/filebot -script fn:sysinfo
```


## filebot-watcher

The filebot-watcher command-line tool watches a given folder and executes the [amc script](https://www.filebot.net/forums/viewtopic.php?f=4&t=215) on newly added files.

```
docker run -it -v $PWD:/volume1 -v data:/data -v watch:/watch -v output:/output rednoah/filebot:watcher
```

The first argument `$1` is the watch folder. The remaining arguments are [amc script](https://www.filebot.net/forums/viewtopic.php?f=4&t=215) options.
