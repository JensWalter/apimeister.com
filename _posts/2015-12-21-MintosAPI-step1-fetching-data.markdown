---
layout: post
title:  "Mintos API step1 fetching data"
date:   2015-12-21 18:34:54
tags: api101 mintosAPI
---
For some reason, the data export for Mintos is password protected. So first things first, authenticate with Mintos. (I attached the whole bash script at the end of the post)

After logging in, I found some downloads which could export Mintos data into Excel sheets.

The first is the download of the complete loan book.
(https://www.mintos.com/en/loan-book/download"|https://www.mintos.com/en/loan-book/download")

Additional to that I wanted to download the actual primary and secondary market data.
Both are easily accessible through the HTML form.

Primary market
(https://www.mintos.com/en/market/primary/list.xlsx|https://www.mintos.com/en/market/primary/list.xlsx)

Secondary market
(https://www.mintos.com/en/market/secondary/list.xlsx|https://www.mintos.com/en/market/secondary/list.xlsx)

{% highlight bash%}
#!/bin/bash
#first fetch the csrf token and store it as bash variable
VAL=`wget --keep-session-cookies --save-cookies cookies -O - "https://www.mintos.com/en/" | grep csrf | grep -o 'value="[^"]*"'`
wget --load-cookies cookies --keep-session-cookies --save-cookies cookies -O - --post-data "_csrf_token=${VAL:7:43}&_username=<username>&_password=<password>" --keep-session-cookies https://www.mintos.com/en/login/check;
wget --content-disposition --load-cookies cookies --keep-session-cookies "https://www.mintos.com/en/loan-book/download";
wget --content-disposition --load-cookies cookies --keep-session-cookies --post-data "secondary_market_filter%5Bmin_interest%5D=&secondary_market_filter%5Bmax_interest%5D=&secondary_market_filter%5Bmin_ltv%5D=&secondary_market_filter%5Bmax_ltv%5D=&secondary_market_filter%5Bmin_term%5D=&secondary_market_filter%5Bmax_term%5D=&secondary_market_filter%5Bissued_from%5D=&secondary_market_filter%5Bissued_till%5D=&secondary_market_filter%5Bwith_buyback%5D=&secondary_market_filter%5Bmin_amount%5D=&secondary_market_filter%5Bmax_amount%5D=&secondary_market_filter%5Bloan_id%5D=&secondary_market_filter%5Binvested_in%5D=&secondary_market_filter%5Bmin_ytm%5D=&secondary_market_filter%5Bmax_ytm%5D=&secondary_market_filter%5Bmin_premium%5D=&secondary_market_filter%5Bmax_premium%5D=&secondary_market_filter%5Bsort_field%5D=ytm&secondary_market_filter%5Bsort_order%5D=DESC&secondary_market_filter%5Bmax_results%5D=20&secondary_market_filter%5Bpage%5D=1" 'https://www.mintos.com/en/market/secondary/list.xlsx';
wget --content-disposition --load-cookies cookies --keep-session-cookies --post-data "primary_market_filter%5Bmin_interest%5D=&primary_market_filter%5Bmax_interest%5D=&primary_market_filter%5Bmin_ltv%5D=&primary_market_filter%5Bmax_ltv%5D=&primary_market_filter%5Bmin_term%5D=&primary_market_filter%5Bmax_term%5D=&primary_market_filter%5Bissued_from%5D=&primary_market_filter%5Bissued_till%5D=&primary_market_filter%5Bwith_buyback%5D=&primary_market_filter%5Bmin_amount%5D=&primary_market_filter%5Bmax_amount%5D=&primary_market_filter%5Bloan_id%5D=&primary_market_filter%5Binvested_in%5D=&primary_market_filter%5Bsort_field%5D=available_for_investment&primary_market_filter%5Bsort_order%5D=DESC&primary_market_filter%5Bmax_results%5D=20&primary_market_filter%5Bpage%5D=1" 'https://www.mintos.com/en/market/primary/list.xlsx';
{% endhighlight %}
