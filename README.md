###tm4julia: a partial preview for developers
<small>Jeffrey A. Sarnoff (2012-Oct-24)</small>

> **Pre-Release caution**: *pervasive operational correctness not assured.*
>
> This pre-release offers developers access to the ymdhms_tz 64 bitstype, and essential methods (to-be-exported).




#####To input a Date+Time+Zone


The cannonical date+time+zone entry follows this pattern:


"[-]YYYY-MM-DD hh:mm:ss tzname"


where tzname is the IANA standard timezone name,


the year is given with four digits (preceeded by '-' if it preceeds year zero),
all other date and time elements are given with two digits (use a leading '0').


```
# January 5th, 2010 at 8:30am in Chicago
when_and_where = d"2010-01-22 08:30:00 America/Chicago"

# October 30th, 1865 at 11:59:59pm in Paris
when_and_where = d"1865-10-30 11:59:59 Europe/Paris"
```

