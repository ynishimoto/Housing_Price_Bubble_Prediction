Bubble Research
================

Summary of Project Proposal
---------------------------

The average price of homes in the Greater Toronto Area has increased substantially in recent years, from about $465,000 in 2013 to about $761,000 in 2017 (64 per cent increase) \[see Chart 1 below\]. The large increase over a relatively short period has prompted many to suggest that the market is undergoing a 'bubble', which may eventually lead to a rapid price decline. However, the trend in average prices alone is a relatively crude and imprecise indicator of housing price bubbles. Average price tends would not describe non-bubble scenarios, such as a price 'adjustment' due to an undervalued market prior to 2013.

![](Chart%201%20-%20Average%20House%20Prices.png)

Ohnishi et. al. demonstrate a robust method of identifying housing market bubbles in their study, 'The Evolution of House Price Distribution' (Univ. of Tokyo, 2011). The study found that, under normal market conditions, house prices in the Greater Tokyo Area followed a normal distribution, similar to other international jurisdictions where prices were stable. However, an analysis of historic data showed that, during the bubble era, the distribution had a distinct fat upper (right) tail compared to a normal distribution.

Their method, which analyzes the entire cross-sectional price distribution rather than changes in the mean alone, could be used to robustly determine whether Toronto's housing market is experiencing a bubble. The insight gained would be useful to prospective home buyers in particular, who may be unsure whether to postpone their purchase (and wait for a price drop), or buy now (as prices will likely remain at current levels or continue to rise). With respect to data, Ohnishi et. al. had access to over a million listings from a real estate publication in Tokyo, spanning 20 years. The proposed Toronto study would source data online by scraping a widely used real estate listing website. While there are many such listing services, presumably their content is similar, given that they generally subscribe to the same 'Multiple Listing Service' database.

Initial analysis shows using the above methodology shows that Toronto likely is not experiencing a housing price bubble. Chart 2 \[see below\] shows that the distribution of house prices (solid line) is not skewed to the right, and is in fact slightly skewed to the left compared to the normal distribution (dotted line). This suggests that the market is currently undervalued and that prices may continue to rise indefinitely. The distribution shown represents quality-adjusted prices, and is controlled for certain exogenous characteristics affecting individual house prices, such as its size (sqft), the number of bedrooms, and the number of bathrooms.

![](Chart%202%20-%20Distribution%20of%20House%20Prices.png)

A more robust study in the future could control for additional characteristics such as the location of individual properties; further, the study could be expanded to include other residential property types, such as condominiums.

Sample Housing Price Data
-------------------------

Toronto housing prices by type of property:

``` r
prices <- read.csv("data/toronto_data.csv")

tmp <- gsub("^(.*)_HPI$", "\\1", names(prices))
names(prices) <- gsub("_", " ", tmp)
kable(prices[1:20,],"html", caption="Toronto Housing Prices") %>%
  kable_styling(bootstrap_options = c("striped", "hover", "condensed",  font_size = 8))
```

<table class="table table-striped table-hover table-condensed" style="margin-left: auto; margin-right: auto;">
<caption>
Toronto Housing Prices
</caption>
<thead>
<tr>
<th style="text-align:left;">
Date
</th>
<th style="text-align:right;">
Composite
</th>
<th style="text-align:right;">
Single Family
</th>
<th style="text-align:right;">
One Storey
</th>
<th style="text-align:right;">
Two Storey
</th>
<th style="text-align:right;">
Townhouse
</th>
<th style="text-align:right;">
Apartment
</th>
<th style="text-align:right;">
Composite Benchmark
</th>
<th style="text-align:right;">
Single Family Benchmark
</th>
<th style="text-align:right;">
One Storey Benchmark
</th>
<th style="text-align:right;">
Two Storey Benchmark
</th>
<th style="text-align:right;">
Townhouse Benchmark
</th>
<th style="text-align:right;">
Apartment Benchmark
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Jan 2005
</td>
<td style="text-align:right;">
100.0
</td>
<td style="text-align:right;">
100.0
</td>
<td style="text-align:right;">
100.0
</td>
<td style="text-align:right;">
100.0
</td>
<td style="text-align:right;">
100.0
</td>
<td style="text-align:right;">
100.0
</td>
<td style="text-align:right;">
304000
</td>
<td style="text-align:right;">
344600
</td>
<td style="text-align:right;">
304900
</td>
<td style="text-align:right;">
358400
</td>
<td style="text-align:right;">
221900
</td>
<td style="text-align:right;">
199800
</td>
</tr>
<tr>
<td style="text-align:left;">
Feb 2005
</td>
<td style="text-align:right;">
100.9
</td>
<td style="text-align:right;">
101.2
</td>
<td style="text-align:right;">
101.7
</td>
<td style="text-align:right;">
101.1
</td>
<td style="text-align:right;">
100.2
</td>
<td style="text-align:right;">
100.1
</td>
<td style="text-align:right;">
306700
</td>
<td style="text-align:right;">
348700
</td>
<td style="text-align:right;">
310100
</td>
<td style="text-align:right;">
362300
</td>
<td style="text-align:right;">
222300
</td>
<td style="text-align:right;">
200000
</td>
</tr>
<tr>
<td style="text-align:left;">
Mar 2005
</td>
<td style="text-align:right;">
101.9
</td>
<td style="text-align:right;">
102.4
</td>
<td style="text-align:right;">
102.3
</td>
<td style="text-align:right;">
102.4
</td>
<td style="text-align:right;">
100.6
</td>
<td style="text-align:right;">
100.7
</td>
<td style="text-align:right;">
309700
</td>
<td style="text-align:right;">
352800
</td>
<td style="text-align:right;">
312000
</td>
<td style="text-align:right;">
367000
</td>
<td style="text-align:right;">
223200
</td>
<td style="text-align:right;">
201200
</td>
</tr>
<tr>
<td style="text-align:left;">
Apr 2005
</td>
<td style="text-align:right;">
102.7
</td>
<td style="text-align:right;">
103.3
</td>
<td style="text-align:right;">
103.4
</td>
<td style="text-align:right;">
103.3
</td>
<td style="text-align:right;">
101.3
</td>
<td style="text-align:right;">
101.2
</td>
<td style="text-align:right;">
312200
</td>
<td style="text-align:right;">
356000
</td>
<td style="text-align:right;">
315300
</td>
<td style="text-align:right;">
370200
</td>
<td style="text-align:right;">
224700
</td>
<td style="text-align:right;">
202200
</td>
</tr>
<tr>
<td style="text-align:left;">
May 2005
</td>
<td style="text-align:right;">
103.5
</td>
<td style="text-align:right;">
104.1
</td>
<td style="text-align:right;">
104.7
</td>
<td style="text-align:right;">
103.9
</td>
<td style="text-align:right;">
101.9
</td>
<td style="text-align:right;">
102.1
</td>
<td style="text-align:right;">
314600
</td>
<td style="text-align:right;">
358700
</td>
<td style="text-align:right;">
319300
</td>
<td style="text-align:right;">
372400
</td>
<td style="text-align:right;">
226100
</td>
<td style="text-align:right;">
204000
</td>
</tr>
<tr>
<td style="text-align:left;">
Jun 2005
</td>
<td style="text-align:right;">
104.0
</td>
<td style="text-align:right;">
104.6
</td>
<td style="text-align:right;">
104.6
</td>
<td style="text-align:right;">
104.5
</td>
<td style="text-align:right;">
102.7
</td>
<td style="text-align:right;">
102.4
</td>
<td style="text-align:right;">
316100
</td>
<td style="text-align:right;">
360400
</td>
<td style="text-align:right;">
319000
</td>
<td style="text-align:right;">
374500
</td>
<td style="text-align:right;">
227800
</td>
<td style="text-align:right;">
204600
</td>
</tr>
<tr>
<td style="text-align:left;">
Jul 2005
</td>
<td style="text-align:right;">
104.1
</td>
<td style="text-align:right;">
104.7
</td>
<td style="text-align:right;">
104.8
</td>
<td style="text-align:right;">
104.6
</td>
<td style="text-align:right;">
103.0
</td>
<td style="text-align:right;">
102.8
</td>
<td style="text-align:right;">
316400
</td>
<td style="text-align:right;">
360800
</td>
<td style="text-align:right;">
319600
</td>
<td style="text-align:right;">
374900
</td>
<td style="text-align:right;">
228500
</td>
<td style="text-align:right;">
205400
</td>
</tr>
<tr>
<td style="text-align:left;">
Aug 2005
</td>
<td style="text-align:right;">
104.4
</td>
<td style="text-align:right;">
104.9
</td>
<td style="text-align:right;">
105.6
</td>
<td style="text-align:right;">
104.7
</td>
<td style="text-align:right;">
103.3
</td>
<td style="text-align:right;">
103.1
</td>
<td style="text-align:right;">
317300
</td>
<td style="text-align:right;">
361500
</td>
<td style="text-align:right;">
322000
</td>
<td style="text-align:right;">
375200
</td>
<td style="text-align:right;">
229200
</td>
<td style="text-align:right;">
206000
</td>
</tr>
<tr>
<td style="text-align:left;">
Sep 2005
</td>
<td style="text-align:right;">
104.7
</td>
<td style="text-align:right;">
105.2
</td>
<td style="text-align:right;">
105.9
</td>
<td style="text-align:right;">
104.9
</td>
<td style="text-align:right;">
103.8
</td>
<td style="text-align:right;">
103.6
</td>
<td style="text-align:right;">
318300
</td>
<td style="text-align:right;">
362500
</td>
<td style="text-align:right;">
322900
</td>
<td style="text-align:right;">
376000
</td>
<td style="text-align:right;">
230300
</td>
<td style="text-align:right;">
207000
</td>
</tr>
<tr>
<td style="text-align:left;">
Oct 2005
</td>
<td style="text-align:right;">
105.1
</td>
<td style="text-align:right;">
105.6
</td>
<td style="text-align:right;">
106.3
</td>
<td style="text-align:right;">
105.4
</td>
<td style="text-align:right;">
104.1
</td>
<td style="text-align:right;">
103.7
</td>
<td style="text-align:right;">
319500
</td>
<td style="text-align:right;">
363900
</td>
<td style="text-align:right;">
324200
</td>
<td style="text-align:right;">
377700
</td>
<td style="text-align:right;">
231000
</td>
<td style="text-align:right;">
207200
</td>
</tr>
<tr>
<td style="text-align:left;">
Nov 2005
</td>
<td style="text-align:right;">
105.2
</td>
<td style="text-align:right;">
105.8
</td>
<td style="text-align:right;">
106.0
</td>
<td style="text-align:right;">
105.8
</td>
<td style="text-align:right;">
104.2
</td>
<td style="text-align:right;">
103.5
</td>
<td style="text-align:right;">
319800
</td>
<td style="text-align:right;">
364600
</td>
<td style="text-align:right;">
323200
</td>
<td style="text-align:right;">
379200
</td>
<td style="text-align:right;">
231200
</td>
<td style="text-align:right;">
206800
</td>
</tr>
<tr>
<td style="text-align:left;">
Dec 2005
</td>
<td style="text-align:right;">
105.3
</td>
<td style="text-align:right;">
105.6
</td>
<td style="text-align:right;">
106.0
</td>
<td style="text-align:right;">
105.4
</td>
<td style="text-align:right;">
104.5
</td>
<td style="text-align:right;">
104.9
</td>
<td style="text-align:right;">
320100
</td>
<td style="text-align:right;">
363900
</td>
<td style="text-align:right;">
323200
</td>
<td style="text-align:right;">
377700
</td>
<td style="text-align:right;">
231800
</td>
<td style="text-align:right;">
209600
</td>
</tr>
<tr>
<td style="text-align:left;">
Jan 2006
</td>
<td style="text-align:right;">
105.9
</td>
<td style="text-align:right;">
106.3
</td>
<td style="text-align:right;">
106.3
</td>
<td style="text-align:right;">
106.3
</td>
<td style="text-align:right;">
104.5
</td>
<td style="text-align:right;">
104.9
</td>
<td style="text-align:right;">
321900
</td>
<td style="text-align:right;">
366300
</td>
<td style="text-align:right;">
324200
</td>
<td style="text-align:right;">
381000
</td>
<td style="text-align:right;">
231800
</td>
<td style="text-align:right;">
209600
</td>
</tr>
<tr>
<td style="text-align:left;">
Feb 2006
</td>
<td style="text-align:right;">
106.7
</td>
<td style="text-align:right;">
107.3
</td>
<td style="text-align:right;">
107.4
</td>
<td style="text-align:right;">
107.2
</td>
<td style="text-align:right;">
104.7
</td>
<td style="text-align:right;">
105.8
</td>
<td style="text-align:right;">
324300
</td>
<td style="text-align:right;">
369700
</td>
<td style="text-align:right;">
327500
</td>
<td style="text-align:right;">
384200
</td>
<td style="text-align:right;">
232300
</td>
<td style="text-align:right;">
211400
</td>
</tr>
<tr>
<td style="text-align:left;">
Mar 2006
</td>
<td style="text-align:right;">
107.8
</td>
<td style="text-align:right;">
108.6
</td>
<td style="text-align:right;">
109.2
</td>
<td style="text-align:right;">
108.4
</td>
<td style="text-align:right;">
105.7
</td>
<td style="text-align:right;">
106.1
</td>
<td style="text-align:right;">
327700
</td>
<td style="text-align:right;">
374200
</td>
<td style="text-align:right;">
333000
</td>
<td style="text-align:right;">
388500
</td>
<td style="text-align:right;">
234500
</td>
<td style="text-align:right;">
212000
</td>
</tr>
<tr>
<td style="text-align:left;">
Apr 2006
</td>
<td style="text-align:right;">
108.7
</td>
<td style="text-align:right;">
109.5
</td>
<td style="text-align:right;">
109.6
</td>
<td style="text-align:right;">
109.5
</td>
<td style="text-align:right;">
106.7
</td>
<td style="text-align:right;">
107.1
</td>
<td style="text-align:right;">
330400
</td>
<td style="text-align:right;">
377300
</td>
<td style="text-align:right;">
334200
</td>
<td style="text-align:right;">
392400
</td>
<td style="text-align:right;">
236700
</td>
<td style="text-align:right;">
214000
</td>
</tr>
<tr>
<td style="text-align:left;">
May 2006
</td>
<td style="text-align:right;">
109.4
</td>
<td style="text-align:right;">
110.3
</td>
<td style="text-align:right;">
110.9
</td>
<td style="text-align:right;">
110.1
</td>
<td style="text-align:right;">
107.2
</td>
<td style="text-align:right;">
107.2
</td>
<td style="text-align:right;">
332500
</td>
<td style="text-align:right;">
380100
</td>
<td style="text-align:right;">
338200
</td>
<td style="text-align:right;">
394600
</td>
<td style="text-align:right;">
237800
</td>
<td style="text-align:right;">
214200
</td>
</tr>
<tr>
<td style="text-align:left;">
Jun 2006
</td>
<td style="text-align:right;">
109.3
</td>
<td style="text-align:right;">
110.1
</td>
<td style="text-align:right;">
110.8
</td>
<td style="text-align:right;">
109.9
</td>
<td style="text-align:right;">
107.7
</td>
<td style="text-align:right;">
107.4
</td>
<td style="text-align:right;">
332200
</td>
<td style="text-align:right;">
379400
</td>
<td style="text-align:right;">
337900
</td>
<td style="text-align:right;">
393900
</td>
<td style="text-align:right;">
238900
</td>
<td style="text-align:right;">
214600
</td>
</tr>
<tr>
<td style="text-align:left;">
Jul 2006
</td>
<td style="text-align:right;">
109.3
</td>
<td style="text-align:right;">
109.9
</td>
<td style="text-align:right;">
110.7
</td>
<td style="text-align:right;">
109.6
</td>
<td style="text-align:right;">
108.2
</td>
<td style="text-align:right;">
107.7
</td>
<td style="text-align:right;">
332200
</td>
<td style="text-align:right;">
378700
</td>
<td style="text-align:right;">
337600
</td>
<td style="text-align:right;">
392800
</td>
<td style="text-align:right;">
240000
</td>
<td style="text-align:right;">
215200
</td>
</tr>
<tr>
<td style="text-align:left;">
Aug 2006
</td>
<td style="text-align:right;">
109.2
</td>
<td style="text-align:right;">
109.7
</td>
<td style="text-align:right;">
110.5
</td>
<td style="text-align:right;">
109.5
</td>
<td style="text-align:right;">
108.3
</td>
<td style="text-align:right;">
107.6
</td>
<td style="text-align:right;">
331900
</td>
<td style="text-align:right;">
378000
</td>
<td style="text-align:right;">
337000
</td>
<td style="text-align:right;">
392400
</td>
<td style="text-align:right;">
240300
</td>
<td style="text-align:right;">
215000
</td>
</tr>
</tbody>
</table>
Sample Real Estate Listings
---------------------------

You can also embed plots, for example:

<table class="table table-striped table-hover table-condensed" style="margin-left: auto; margin-right: auto;">
<caption>
Toronto Real Estate Listings
</caption>
<thead>
<tr>
<th style="text-align:left;">
id
</th>
<th style="text-align:left;">
adr
</th>
<th style="text-align:left;">
cty
</th>
<th style="text-align:right;">
pr
</th>
<th style="text-align:right;">
bd
</th>
<th style="text-align:right;">
bat
</th>
<th style="text-align:right;">
sq
</th>
<th style="text-align:left;">
url
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
E4105229
</td>
<td style="text-align:left;">
7 Coe Drive
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
769900
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
2250
</td>
<td style="text-align:left;">
E4105229/7-coe-drive-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4105147
</td>
<td style="text-align:left;">
17 Locker Drive
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
674900
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
E4105147/17-locker-drive-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4104691
</td>
<td style="text-align:left;">
6 Mary Street
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
671790
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
E4104691/6-mary-street-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4104338
</td>
<td style="text-align:left;">
23 Ventura Lane
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
484900
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
E4104338/23-ventura-lane-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4103148
</td>
<td style="text-align:left;">
63 Coe Drive
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
729000
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
2250
</td>
<td style="text-align:left;">
E4103148/63-coe-drive-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4102770
</td>
<td style="text-align:left;">
49 Glynn Road
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
560000
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1300
</td>
<td style="text-align:left;">
E4102770/49-glynn-road-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4100518
</td>
<td style="text-align:left;">
56 Longstaff Drive
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
569900
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
E4100518/56-longstaff-drive-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4098046
</td>
<td style="text-align:left;">
39-62 Abela Lane
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
449900
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1100
</td>
<td style="text-align:left;">
E4098046/39-62-abela-lane-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4097020
</td>
<td style="text-align:left;">
33 Noake Crescent
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
599000
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
E4097020/33-noake-crescent-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4095659
</td>
<td style="text-align:left;">
28 George Street
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
430000
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
E4095659/28-george-street-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4096200
</td>
<td style="text-align:left;">
35 Bondsmith Street
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
649900
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
1750
</td>
<td style="text-align:left;">
E4096200/35-bondsmith-street-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4096839
</td>
<td style="text-align:left;">
62-76 Harwood Avenue
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
849900
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
2250
</td>
<td style="text-align:left;">
E4096839/62-76-harwood-avenue-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4094242
</td>
<td style="text-align:left;">
13 Chadwick Drive
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
719900
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
2250
</td>
<td style="text-align:left;">
E4094242/13-chadwick-drive-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4095595
</td>
<td style="text-align:left;">
24 Perfitt Crescent
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
699900
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
E4095595/24-perfitt-crescent-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4091671
</td>
<td style="text-align:left;">
16 Pennefather Lane
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
475000
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1500
</td>
<td style="text-align:left;">
E4091671/16-pennefather-lane-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4094084
</td>
<td style="text-align:left;">
69 Perfitt Crescent
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
689900
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
1750
</td>
<td style="text-align:left;">
E4094084/69-perfitt-crescent-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4093112
</td>
<td style="text-align:left;">
18 Mcgonigal Lane
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
480000
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
1300
</td>
<td style="text-align:left;">
E4093112/18-mcgonigal-lane-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4092285
</td>
<td style="text-align:left;">
30 Keeble Crescent
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
929900
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
5
</td>
<td style="text-align:right;">
2250
</td>
<td style="text-align:left;">
E4092285/30-keeble-crescent-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4076844
</td>
<td style="text-align:left;">
26 Holmes Crescent
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
739900
</td>
<td style="text-align:right;">
5
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
2750
</td>
<td style="text-align:left;">
E4076844/26-holmes-crescent-ajax-on
</td>
</tr>
<tr>
<td style="text-align:left;">
E4072771
</td>
<td style="text-align:left;">
710-167 Harwood Avenue
</td>
<td style="text-align:left;">
Ajax
</td>
<td style="text-align:right;">
299900
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
550
</td>
<td style="text-align:left;">
E4072771/710-167-harwood-avenue-ajax-on
</td>
</tr>
</tbody>
</table>
