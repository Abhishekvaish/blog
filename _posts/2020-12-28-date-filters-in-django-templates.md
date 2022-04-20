---
layout: post
title: "Date Filter in Django Templates"
tags: "python,django templates,date filter"
---
#### Common date filter in Django Templates

| Format character	 | Description | Example output |
|:-------:|-------|:-------:|
||||
||**Day**||
|d|Day of the month, 2 digits with leading zeros.|01 to 31|
|j|Day of the month without leading zeros.|1 to 31|
|S|English ordinal suffix for day of the month, 2 characters.|st, nd, rd or th|
||||
||**Month**||
|m|Month, 2 digits with leading zeros.|01 to 12|
|n|Month without leading zeros.|1 to 12|
|b|Month, textual, 3 letters, lowercase.|jan|
|M|Month, textual, 3 letters.|Jan|
|F|Month, textual, long.|January|
||||
||**Year**||
|y|Year, 2 digits.|99|
|Y|Year, 4 digits.|1999|
||||
||**Week**||
|D|Day of the week, textual, 3 letters.|Fri|
|l|Day of the week, textual, long.|Friday|
||||
||**Hours**||
|G|Hour, 24-hour format without leading zeros.|0 to 23|
|H|Hour, 24-hour format.|00 to 23|
|g|Hour, 12-hour format without leading zeros.|1 to 12|
|h|Hour, 12-hour format.|01 to 12|
|a|a.m. or p.m.|a.m.|
|A|AM or PM.|AM|
||||
||**Minutes**||
|i|Minutes.|00 to 59|
||||
||**Seconds**||
|s|Seconds, 2 digits with leading zeros.|00 to 59|
||||

<br>


**Example**
```py
{% raw %} 
{{date_string|date:'F m, Y'}}
{% endraw %} 
# which gives the same date format as in this website
```