---
title: mongoexport
date: 2023-08-23 09:28:54
tags: server
---




 mongoexport  mongodb://192.168.2.115/beike_house --collection beike_house_chengjiao  --type=csv  --fields title  house_url title price average property property2 unit complete_time address want_sell days_to_sell fetch_time--out beike_chengjiao.csv


 mongoexport -h 192.168.2.116  -d beike_house  -c beike_house_chengjiao