---
layout: post
title:  "Python grab me a Cartoon"
subtitle: "Scrapping the satire"
date:   2016-04-29 12:29:11
categories: [python]
---

Everyone Loves Cartoons/Comics,eh? When it comes from [political satire](http://www.theonion.com/article/north-korea-celebrates-as-kim-jong-un-becomes-firs-31085) most of  you won't say a No.[Like this ](http://media.townhall.com/Townhall/Car/b/bg042916dAPR20160429064519.jpg), you won't be laughing again in life. Fortunately, I had a nice night scraping up the Cartoon-scape from India's century old newspaper [The Hindu](http://www.thehindu.com/) once which renowned cartoonists like [R. K. Laxman](https://en.wikipedia.org/wiki/R._K._Laxman), [K. Shankar Pillai](https://en.wikipedia.org/wiki/K._Shankar_Pillai) were ruling the pen.


What?
----


Scrapping up all visible cartoon-scape images in (.jpg format)from the English Hindu Website and stores them in a folder with the naming convention of the respective dates.


Why?


It's a fun to to know about the missed cartoons, a small portable  image column in a corner of the fresh newspaper but will divulge the nation's hot topic or a minimal blow in the asses of something/someone caused the unconvincing situation on the last daylight. Persuading with the the knowledge you are gaining is a ecstasy and a chance to test your skills.

One of my [Drona](https://en.wikipedia.org/wiki/Drona), mentioned about the book [in his blog here](http://www.kirang.in/2015/12/29/books-i-read-in-2015/) made me addicted back to Cartoon/comic crazy again.


How?

Below is the gist containing the code. It's Python, so nothing more to explain of the plain-sight Pizza.

{% gist 5d4cc11ce8b6a198cb81aec8de0676ef %}

 




Interestingly, I have never used the mechanize module much as I curled under Invisble cloak of requestes/bs4. But mechanize has certain much needed/minimal features like listing the current page's urls with regex filtering options like *url_regex*, *text_regex* etc. It eased the job with few lines of code (w.r.t my knowledge).


Reference:



 1. Interestingly, when searching google for any projects/codes done before on scraping The Hindu came across [This one.](http://www.thehindu.com/thehindu/2003/05/26/stories/2003052600100200.htm) . 
 2. [@2020saurav's](https://github.com/2020saurav/random-scripts/blob/master/the-hindu-scrap.py) random script repo has one script but outdated.

<center>&copy; *Nobody*
