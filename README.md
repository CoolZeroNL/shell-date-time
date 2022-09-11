# shell-date-time
```
#! /bin/bash

# An overly obvious reference for most commonly requested bash timestamps
# Now all you Mac fags can stop pestering me.

cat << EOD
        Format/result           |       Command              |          Output
--------------------------------+----------------------------+------------------------------
YYYY-MM-DD_hh:mm:ss             | date +%F_%T                | $(date +%F_%T)
YYYYMMDD_hhmmss                 | date +%Y%m%d_%H%M%S        | $(date +%Y%m%d_%H%M%S)
YYYYMMDD_hhmmss (UTC version)   | date --utc +%Y%m%d_%H%M%SZ | $(date --utc +%Y%m%d_%H%M%SZ)
YYYYMMDD_hhmmss (with local TZ) | date +%Y%m%d_%H%M%S%Z      | $(date +%Y%m%d_%H%M%S%Z)
YYYYMMSShhmmss                  | date +%Y%m%d%H%M%S         | $(date +%Y%m%d%H%M%S)
YYYYMMSShhmmssnnnnnnnnn         | date +%Y%m%d%H%M%S%N       | $(date +%Y%m%d%H%M%S%N)
YYMMDD_hhmmss                   | date +%y%m%d_%H%M%S        | $(date +%y%m%d_%H%M%S)
Seconds since UNIX epoch:       | date +%s                   | $(date +%s)
Nanoseconds only:               | date +%N                   | $(date +%N)
Nanoseconds since UNIX epoch:   | date +%s%N                 | $(date +%s%N)
Z-notation UTC timestamp        | date --utc +%FT%TZ         | $(date --utc +%FT%TZ)
Z-notation UTC timestamp + ms   | date --utc +%FT%T.%3NZ     | $(date --utc +%FT%T.%3NZ)
ISO8601 UTC timestamp           | date --utc +%FT%T%Z        | $(date --utc +%FT%T%Z)
ISO8601 UTC timestamp + ms      | date --utc +%FT%T.%3N%Z    | $(date --utc +%FT%T.%3N%Z)
ISO8601 Local TZ timestamp      | date +%FT%T%Z              | $(date +%FT%T%Z)
YYYY-MM-DD (Short day)          | date +%F\(%a\)             | $(date +%F\(%a\))
YYYY-MM-DD (Long day)           | date +%F\(%A\)             | $(date +%F\(%A\))
EOD
```

If executed, it will produce the (obvious) output:

```
        Format/result           |       Command              |          Output
--------------------------------+----------------------------+------------------------------
YYYY-MM-DD_hh:mm:ss             | date +%F_%T                | 2020-09-09_11:17:10
YYYYMMDD_hhmmss                 | date +%Y%m%d_%H%M%S        | 20200909_111710
YYYYMMDD_hhmmss (UTC version)   | date --utc +%Y%m%d_%H%M%SZ | 20200909_021710Z
YYYYMMDD_hhmmss (with local TZ) | date +%Y%m%d_%H%M%S%Z      | 20200909_111710JST
YYYYMMSShhmmss                  | date +%Y%m%d%H%M%S         | 20200909111710
YYYYMMSShhmmssnnnnnnnnn         | date +%Y%m%d%H%M%S%N       | 20200909111710866549239
YYMMDD_hhmmss                   | date +%y%m%d_%H%M%S        | 200909_111710
Seconds since UNIX epoch:       | date +%s                   | 1599617830
Nanoseconds only:               | date +%N                   | 873291281
Nanoseconds since UNIX epoch:   | date +%s%N                 | 1599617830874893393
Z-notation UTC timestamp        | date --utc +%FT%TZ         | 2020-09-09T02:17:10Z
Z-notation UTC timestamp + ms   | date --utc +%FT%T.%3NZ     | 2020-09-09T02:17:10.878Z
ISO8601 UTC timestamp           | date --utc +%FT%T%Z        | 2020-09-09T02:17:10UTC
ISO8601 UTC timestamp + ms      | date --utc +%FT%T.%3N%Z    | 2020-09-09T02:17:10.881UTC
ISO8601 Local TZ timestamp      | date +%FT%T%Z              | 2020-09-09T11:17:10JST
YYYY-MM-DD (Short day)          | date +%F\(%a\)             | 2020-09-09(水)
YYYY-MM-DD (Long day)           | date +%F\(%A\)             | 2020-09-09(水曜日)
```

Note that the last two, short and long day-of-week are dependent on the environment variable LANG. After setting LANG=en_US we wind up with the following:

```
YYYY-MM-DD (Short day)          | date +%F\(%a\)             | 2020-09-09(Wed)
YYYY-MM-DD (Long day)           | date +%F\(%A\)             | 2020-09-09(Wednesday)
```
