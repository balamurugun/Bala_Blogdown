---
title: How to build good API?
author: Balamurugan
date: '2020-09-09'
slug: how-to-build-good-api
categories: []
tags: []
description: Desc
hacker_news_id: ''
lobsters_id: ''
meta_img: /images/image.jpg
---

What is a good API?
Easy for 
  consumers to read
  developers to mainatin
  extending
  
Design:
Ask users what features they like to see and get true use cases
Test it out with examples
Think through proper naming convention and use proper verbs(GET/POST/DELETE)
Always version up APIs especially when backwards compatibility not allowed and it could break consumers pipeline.
Convery Ratelimits in you header
Easy to use, even without documentation
Creation and Deletion of User accounts or data shared between mulitple accounts are strictly no


Implementation
Alaways add the ability to limit and offset
Have ability to Developer testing
Failures houd be handled well with meaniningul errors and status codes
Three or fewer parameter is ideal
Design for eager developer to try out fast and quick
Design for discern developer to try out fast and quick
use snake_case as it 20% easier to read than camelCase

maintenance
Create a metrics to track the common usage and failures

And dont forget to documnet




Stealing the line from Jasmin "Best API is no API that developer doesnt require additional code from Application writer"

References:
The Little Manual of API Design - Jasmin Blanchette
https://github.com/tlhunter/consumer-centric-api-design/blob/master/pdf/Consumer-Centric%20API%20Design%20v0.4.0.pdf
http://fwdinnovations.net/whitepaper/APIDesign.pdf
https://increment.com/apis/api-design-for-eager-discering-developers/
Build APIs You Won’t Hate-Phil Sturgeon
https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api