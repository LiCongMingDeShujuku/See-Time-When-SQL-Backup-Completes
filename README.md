![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 参阅备份完成时的时间
#### See Time When SQL Backup Completes
**发布-日期: 2014年05月21日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
这是一个可以用它来查看备份或还原操作完成的确切时间（或根据sql server估计的时间）的快速脚本。当备份设置完成时，这将为你提供所用时间（更精确）的提示。我使用它并将其合并到各种其他非独立作业中，以便在这些操作完成时或之前执行。


## English
Here’s a quick script you can use to see exactly when ( or estimated time according to sql server ) that a backup, or restore operation will complete. This will give you a good indication of a certain time ( with more precision ) when a backup is set to complete. I use this and incorporate it into various other dependent jobs to execute at or around the time when these operations would finish.

---
## Logic
```SQL
use master;
set nocount on
select
'command' = sder.command
, 'percent_complete' = convert(numeric(6,2),sder.percent_complete)
, 'completion_time' = convert(char, dateadd(n,(sder.estimated_completion_time /60/1000),getdate()), 9) from
sys.dm_exec_requests sder
where
command in ('backup database', 'backup log', 'restore database')


```



[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

