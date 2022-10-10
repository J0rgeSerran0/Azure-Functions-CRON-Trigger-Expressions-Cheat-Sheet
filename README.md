# Introduction
> This cheat sheet, is about CRON expressions used in the time triggers for Azure Functions

# Format
The CRON format for Azure Functions is as:

```
{second} {minute} {hour} {day} {month} {day of the week}
```

|Format|Allowed Values|Description|
|--|--|--|
|{second}|`0-59` `*`|second when the trigger will be executed|
|{minute}|`0-59` `*`|minute when the trigger will be executed|
|{hour}|`0-23` `*`|hour when the trigger will be executed|
|{day}|`1-31` `*`|day when the trigger will be executed|
|{month}|`1-12` `*`|month when the trigger will be executed|
|{day of the week}|`0-6` `MON-SUN` `*`|day of the week when the trigger will be executed|

## Special Characters

|Character|Description|
|--|--|
|`*`|Executed on tick of every time unit. `{minute} as *` means that is executed every minute of the hour|
|`-`|Identify a range. `{month} as 3-5` means March, April and May|
|`,`|Set the exact values. `{month} as 3,5` means March and May|
|`/`|Defines an increment `{hour} as */2` means every two hours|

# Samples
|CRON Expression|Human Readable|
|--|--|
|`0 * * * * *`|Every minute|
|`0 */5 * * * *`|Every 5 minutes|
|`0 0 * * * *`|Every hour|
|`0 0 0 * * *`|Every day|
|`0 0 3 * * *`|Every day at 3 AM|
|`0 0 */2 * * *`|Every 2 hours|
|`0 0 7-18 * * *`|Every hour from 7 AM to 6 PM|
|`0 0 7,18 * * *`|Every hour at 7 AM and 6 PM|
|`0 0 6 * * *`|Every day at 6 AM|
|`0 30 7 * * *`|Every day at 7:30 AM|
|`0 0 2 * * 1,4`|At 2 AM only the Monday and Thursday|
|`0 30 7 * * 1-5`|At 7:30 AM from Monday to Friday|

# Resources
- [CRON Expresion Descriptor (*describes CRON expressions as human readable text*)](https://bradymholt.github.io/cron-expression-descriptor/)
- [Wikipedia - CRON information](https://en.wikipedia.org/wiki/Cron)
