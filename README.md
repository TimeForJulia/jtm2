###tm4julia: a partial preview for developers
<small>Jeffrey A. Sarnoff (2012-Oct-24)</small>

> **Pre-Release caution**: *pervasive operational correctness not assured.*
>
> This pre-release offers developers access to the ymdhms_tz 64 bitstype, and essential methods (to-be-exported).




#####To input a date+time+zone


```

# September 14th, 2009 at 3:30pm in Cambridge
JuliaGetsAbstract = d"2009-09-14 15:30:00 America/New_York"

# local threshold of the new millenium
AuldLangSygne = d"2001-01-01 00:00:00"

# September 3rd, 1783 in Paris
SignTreatyOfParis = d"1783-09-03 Europe/Paris"

# IANA standard timezone city names are unique;
# one may name the city to indicate its timezone.

JuliaGetsAbstract = d"2009-09-14 15:30:00 New_York"
SignTreatyOfParis = d"1783-09-03 Paris"

```


##### some IANA timezone names

<table>

  <tr>
    <th>America</th>
    <th>Asia</th>
    <th>Europe</th>
    <th>Australia</th>
  </tr>

   <tr>  <td>"America/Chicago"</td>      <td>"Asia/Dubai"</td>      <td>"Europe/Berlin"</td>    <td>"Australia/Adelaide"</td>  </tr>
   <tr>  <td>"America/Denver"</td>       <td>"Asia/Hong_Kong"</td>  <td>"Europe/Helsinki"</td>  <td>"Australia/Darwin"</td>    </tr>
   <tr>  <td>"America/Los_Angeles"</td>  <td>"Asia/Jerusalem"</td>  <td>"Europe/London"</td>    <td>"Australia/Hobart"</td>    </tr>
   <tr>  <td>"America/New_York"</td>     <td>"Asia/Seoul"</td>      <td>"Europe/Madrid"</td>    <td>"Australia/Perth"</td>     </tr>
   <tr>  <td>"America/Mexico_City"</td>  <td>"Asia/Shanghai"</td>   <td>"Europe/Moscow"</td>    <td>"Australia/Brisbane"</td>  </tr>
   <tr>  <td>"America/Sao_Paulo"</td>    <td>"Asia/Singapore"</td>  <td>"Europe/Paris"</td>     <td>"Australia/Melbourne"</td> </tr>
   <tr>  <td>"America/Toronto"</td>      <td>"Asia/Tokyo"</td>      <td>"Europe/Stockholm"</td> <td>"Australia/Sydney"</td>    </tr>

</table>


<p></br></p>



#####d" year-mo-dy hr:mi:cs tzname "


* The common date+time+zone entry: d"YYYY-MM-DD hh:mm:ss tzname"

  * where tzname is the IANA standard timezone name
     * if omitted, the local timezone (e.g. from getenv("TZ")) is used.
  * use the tzname "UTC" to input date+time in Universal Coordinated Time
  * use the tzname "GMT" to input date+time in leapsecond-free pseudotime
     * disrecommended: only for coordinating with temporally unkempt systems

<p></br></p>

* The cannonical date+time+zone entry: d"[-]YYYY-MM-DD hh:mm:ss tzname [G,J]"

  * the year is given with four digits (leading '0's are used as appropriate)
     * prefix '-' to years preceeding year zero ('+' may prefix nonnegative years)
  * all other date and time elements are given with two digits ('01', '59')
  * [G(regorian),J(ulian)] defaults to G: proleptic Gregorian with a year zero.
     * at present, the Julian calendar option is an inactive placeholder

<p></br></p>

* The cannonical date+zone entry: d"[-]YYYY-MM-DD tzname [G,J]"

  * the entry itself is aware that the time-of-day has not been specified
  * if required (e.g. for subtraction), the time-of-day will be 11:59:59.875
     * with 10 subsecond bits: (7//8)*(1000) == 875 and (7//8)*(1024) == 896

<p></br></p>
