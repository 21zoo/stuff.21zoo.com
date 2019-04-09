---
title: "Crontab - run a command every 5 minutes"
date: 2018-09-25T10:40:22-04:00
draft: false
description: "a quick explainer"
---
To run a command via cron every 5 minutes: <br>
<center>
<b><span style="font-size:larger;"><pre>*/5 * * * *</pre></span> </b>
</center>
The fields are minute, hour, day (of the month), month, day of the week (dotw).
<br><br>
Other options:<br>

```
*	any value
,	value list separator
-	range of values
/	step values
```

<br>
<b>For example</b>
<br>
Run at 15 and 45 past the hour, every hour:<br>
`15,45 * * * *`


<br>
Run at noon, once a day:<br>
`0 12 * * *`

<br>
Run at 2pm, every Monday (dotw == 1):<br>
`0 2 * * 1`
