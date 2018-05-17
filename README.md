# callfinder

Bash script for finding asterisk cdr calls and viewing corresponding full logs for a selected call

### Prerequisites

A running Asterisk instance with full log turned on with ISO datetime format.
Ensure that these lines are present and uncommented in your /etc/asterisk/logger.conf

```
dateformat = %F %T.%3q   ; ISO 8601 date format with milliseconds
full => notice,warning,error,verbose,dtmf,fax
```

### Installing

Put the `callfinder` bash script in your preferred location that is included in the `$PATH` variable

### Usage examples

Default invocation lists all available calls in /var/log/asterisk/cdr-csv/Master.csv and searches /var/log/asterisk/full for full logs.

All calls matching the supplied parameters are displayed with basic CDR data - if a full log for that call can be displayed,
the call will be highlighted and numbered. Typing in the number of the desired call displays all lines from the full log that correspond to that call.

Finding all calls made today from a number partially matching the supplied value

```
callfinder 555555 today
```

Finding alls call made this week to SIP device 300

```
callfinder "SIP/300" this_week
```

Finding all calls made on a specific date from an alternative CDR file with a number partially matching the supplied value

```
callfinder -d 2017-05-02 -c /var/log/asterisk/cdr-csv/Custom.csv 555555
```

Finding all calls made after a specific date

```
callfinder -a 2017-05-02
```

## Authors

* **Krunoslav Pavic** - *Initial work* - [dirgim](https://github.com/dirgim)

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details
