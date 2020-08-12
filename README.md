# Some background image rotation tool

This tools help to set up a backround rotation constantly using the current top image posts from a given subreddit,
giving a similar effect as you know it for example from a chromecast. I personally like the balance of repition and
variety over time which emerges from this, but you can change it by playing around with some parameters.

This is a simple tool I made for myself, so don't expect a very detailed documentation or even technical support from 
me. Just read the source files if you want to know more.

There are three files:

* `getsfwporn` is a script which queries the top page of any given subreddit and (if present) downloads any media 
  (reddit hosted only). The names comes from reddits "SFW Porn Network" which is a network of photography related subs
  like [/r/EarthPorn](https://reddit.com/r/EarthPorn) (SFW, as the name implies). It downloads files which don't exist
  and links them into a rotation/ directory. This means the base directory is a cache to avoid multiple downloading of
  the same file, and the rotation directory is the actual directory containing (symlinks to) the current top posts of
  the given subreddit.
* `update-bg-dir` is a helper which runs `getsfwporn` within a given directory, and cleans up old cache files. This is
  suited for example to be run hourly by a cron job.
* `bgdaemon` is a tool you run for a given directoy and sets a random background from any jpg files every minute using
  `feh`. Suports multiple monitors. 
