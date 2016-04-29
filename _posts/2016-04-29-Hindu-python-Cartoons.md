---
layout: post
title:  "Python grab me a Cartoon"
subtitle: "Scrapping the satire"
date:   2016-04-29 12:29:11
categories: [python]
---

Everyone Loves Cartoons/Comics,eh? When it comes from [political satire](http://www.theonion.com/article/north-korea-celebrates-as-kim-jong-un-becomes-firs-31085) most of  you won't say a No.[Like this ](http://media.townhall.com/Townhall/Car/b/bg042916dAPR20160429064519.jpg), you won't be laughing again in life. Fortunately, I had a nice night scraping up the Cartoon-scape from India's century old newspaper [The Hindu](http://www.thehindu.com/) once which renowned cartoonists like [R. K. Laxman](https://en.wikipedia.org/wiki/R._K._Laxman), [K. Shankar Pillai](https://en.wikipedia.org/wiki/K._Shankar_Pillai) were ruling the pen.

#What?
Scrapping up all visible cartoon-scape images in (.jpg format)from the English Hindu Website and stores them in a folder with the naming convention of the respective dates.

#Why?
It's a fun to to know about the missed cartoons, a small portable  image column in a corner of the fresh newspaper but will divulge the nation's hot topic or a minimal blow in the asses of something/someone caused the unconvincing situation on the last daylight. Persuading with the the knowledge you are gaining is a ecstasy and a chance to test your skills.

One of my [Drona](https://en.wikipedia.org/wiki/Drona), mentioned about the book [in his blog here](http://www.kirang.in/2015/12/29/books-i-read-in-2015/) made me addicted back to Cartoon/comic crazy again.

<center> 
#How? 
</center>

Below is the gist containing the code. It's Python, so nothing more to explain of the plain-sight Pizza.

{% gist 5d4cc11ce8b6a198cb81aec8de0676ef %}

 


----------


    #!/usr/bin/env python
    # -*- coding: utf-8 -*-
    
    import mechanize
    import re
    from bs4 import BeautifulSoup
    
    
    br = mechanize.Browser()
    
    #   setup the browser for action
    br.set_all_readonly(False)
    br.set_handle_robots(False)
    br.set_handle_refresh(False)
    br.addheaders =  [('User-agent', 'Firefox')]
    
    #   capture the base page
    url = 'http://www.thehindu.com/opinion/cartoon/'
    response = br.open(url)
    html =  response.read()
    
    dl_urls = dict()
    
    soup = BeautifulSoup(html)
    temp = []
    #   get the PTO pages
    for link in br.links(url_regex = 'http://www.thehindu.com/opinion/cartoon/+[?](.*)'):
        temp.append(str(link).split("'")[3])
    
    #   workaround the each image section
    for page_url in list(set(temp)):
        response = br.open(page_url)
        html =  response.read()
        soup = BeautifulSoup(html)
        for i in soup.find_all('div',{'class' : 'section-teaser'}):
            url,date  = re.sub('d.jpg', 'f.jpg', i.a.img['src']), ((i.h2.text).split('-')[-1]).strip()
            print url,date
            dl_urls[date] = re.sub('d.jpg', 'f.jpg', url)        
            image_response = br.open_novisit(url)
            with open(date + '.jpg', 'wb') as f:
                f.write(image_response.read())

#Reference:

 1. Interestingly, when searching google for any projects/codes done before on scraping The Hindu came across [This one.](http://www.thehindu.com/thehindu/2003/05/26/stories/2003052600100200.htm) . 
 2. [@2020saurav's](https://github.com/2020saurav/random-scripts/blob/master/the-hindu-scrap.py) random script repo has one script but outdated.

