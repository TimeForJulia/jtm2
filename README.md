###tm4julia: a partial preview for developers
<small>Jeffrey A. Sarnoff (2012-Oct-24)</small>

> **Pre-Release caution**: *pervasive operational correctness not assured.*
>
> This pre-release offers developers access to the ymdhms_tz 64 bitstype, and essential methods (to-be-exported).




#####To input a date+time+zone

The cannonical date+time+zone entry: d"[-]YYYY-MM-DD hh:mm:ss tzname [G,J]"

* where tzname is the IANA standard timezone name,
* [G(regorian),J(ulian)] defaults to G: proleptic Gregorian with a year zero.
* the year is given with four digits (preceeded by '-' if it preceeds year zero),
* all other date and time elements are given with two digits (use a leading '0').




```
# January 5th, 2010 at 8:30am in Chicago
whenwhere = d"2010-01-22 08:30:00 America/Chicago"

# October 30th, 1865 at 11:59:59pm in Paris
whenwhere = d"1865-10-30 11:59:59 Europe/Paris"

# IANA standard timezone city names are unique;
# one may name the city to indicate its timezone.
#
# whenwhere = d"2010-01-22 08:30:00 Chicago"
# whenwhere = d"1865-10-30 11:59:59 Paris"

```

