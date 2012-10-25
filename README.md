###tm4julia: a partial preview for developers
<small>Jeffrey A. Sarnoff (2012-Oct-24)</small>

> **Pre-Release caution**: *pervasive operational correctness not assured.*
>
> This pre-release offers developers access to the ymdhms_tz 64 bitstype, and essential methods (to-be-exported).




#####To input a date+time+zone

The cannonical date+time+zone entry: d"[-]YYYY-MM-DD hh:mm:ss tzname [G,J]"

* where tzname is the IANA standard timezone name
  * if omitted, the local timezone (e.g. from getenv("TZ")) is used.
  * use the tzname "UTC" to input date+time in Universal Coordinated Time
  * use the tzname "TAI" to input date+time in International Atomic Time
      * avoid using TAI times unless your work involves TAI valued data
  * use the tzname "GMT" to input date+time in leapsecond-free pseudotime
      * disrecommended: only for coordinating with temporally unkempt systems
* [G(regorian),J(ulian)] defaults to G: proleptic Gregorian with a year zero.
* the year is given with four digits (leading '0's are used as appropriate)
  * prefix '-' to years preceeding year zero ('+' may prefix nonnegative years)
* all other date and time elements are given with two digits ('01', '59').

The cannonical date+zone entry: d"[-]YYYY-MM-DD tzname [G,J]"

* the entry itself is aware that the time-of-day has not been specified
* if required (e.g. for subtraction), the time-of-day will be 11:59:59.875
* (» internally, (7//8)*(10^3) and (7//8)*(2^10) are integral subseconds «)




```
# September 14th, 2009 at 3:30pm in Cambridge
JuliaGetsAbstract = d"2009-09-14 15:30:00 America/New_York"

# September 3rd, 1783 at 10:30:00am in Paris
SignTreatyOfParis = d"1783-09-03 Europe/Paris"

# IANA standard timezone city names are unique;
# one may name the city to indicate its timezone.

JuliaGetsAbstract = d"2009-09-14 15:30:00 New_York"
SignTreatyOfParis = d"1783-09-03 Paris"

```

