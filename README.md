## General `cron` considerations

- The user the job runs under might not be who you think it is. If you're
  unsure, create a cron job like this, and check the output:
  - `* * * * * whoami > /tmp/whoami`
- The environment variables (including `PATH)` probably aren't what you think
  they are
- The shell probably isn't what you think it is, so don't assume that everything
	that works in `bash` will work in your script
- Variable assignments in the `crontab` probably don't work the way you think,
  so don't rely on variables defined in the `crontab` to actually work

## When writing scripts that you want to run via cron

- ALWAYS specify the shell you want the script to run under via
  `#!/path/to/shell/` at the top of your script
- If your script is written in a scripting language like perl, ruby, or python
  (to name a few), don't assume that the environment in which you develop your
  scripts is the same environment in which the script will run -- expect the
  script to break unless you're explicit about the things the script depends
  upon, especially the value of environment variables
