---
layout: mypost
title: Contact
---
<script type="module" src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.esm.js"></script>
<script nomodule src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.js"></script>

## Name: Congbo Song / 宋从波, Pronouns: he/him
<img align="left" src="{{site.baseurl}}/static/img/bio.jpg" width="100" height="100">
<br clear="left"/>

## Address
Room 2.03, Simon building, University of Manchester, Oxford Road, Manchester M13 9PL, United Kingdom

## Email
<congbo.song@manchester.ac.uk>  

## Website
[Google Scholar](https://scholar.google.com/citations?user=JcL-uzcAAAAJ&hl=en){:target="_blank"};   [ResearchGate](https://www.researchgate.net/profile/Congbo-Song){:target="_blank"};  [ORCID](https://orcid.org/0000-0001-7948-4834){:target="_blank"};  [ResearcherID](https://publons.com/researcher/3024756/congbo-song/){:target="_blank"}; [Scopus ID](https://www.scopus.com/authid/detail.uri?authorId=57192012559){:target="_blank"};<br />
University profile page:[https://research.manchester.ac.uk/en/persons/congbo-song](https://research.manchester.ac.uk/en/persons/congbo-song){:target="_blank"}

## Link info
```
* Title: {{ site.description }}
* Website：{{ site.domainUrl }}{{ site.baseurl }}
* Logo：{{ site.domainUrl }}{{ site.baseurl }}/static/img/logo.jpg
```

<!--
<ul>
  {%- for link in site.links %}
  <li>
    <p><a href="{{ link.url }}" title="{{ link.desc }}" target="_blank" >{{ link.title }}</a></p>
  </li>
  {%- endfor %}
</ul>
-->
## Useful links
<div style="display:flex;flex-direction:  column">
  {%- for link in site.links %}
    <div style="display:flex;width:100%;">
      <div style="display:flex;width:100%;margin-bottom:16px;">
        <div style="text-decoration: none;">
          <a href="{{link.url}}" style="display: block;border-bottom:none;">
          <img style="border:0px solid #f00;width:50px;height:50px;border-radius: 50%;" src="{{ link.header }}">
          </a>
        </div>
        <div style="margin-left:12px;margin-top:0px;display:flex;flex-direction:column">
          <p style="border:0px solid #000;height:28px;">
            <a href="{{ link.url }}" title="{{ link.desc }}" target="_blank" >{{ link.title }}</a>
          </p>
          <div style="border:0px solid #000;font-size:12px;height:14px;">{{link.desc}}</div>
          <!-- <div style="border:0px solid #000;font-size:12px;height:24px;">{{link.tag}}</div> -->
        </div>
      </div>
    </div>
  {%- endfor %}
</div>


{% include comment.html %}

<!---
<script type="text/javascript" src="//rf.revolvermaps.com/0/0/6.js?i=5b08vik95x4&amp;m=7&amp;c=e63100&amp;cr1=ffffff&amp;f=arial&amp;l=0&amp;bv=90&amp;lx=-420&amp;ly=420&amp;hi=20&amp;he=7&amp;hc=a8ddff&amp;rs=80" async="async"></script>
-->

<script type='text/javascript' id='clustrmaps' src='//cdn.clustrmaps.com/map_v2.js?cl=3e4ab5&w=200&t=tt&d=TIXUK3EDg_Mgmr7ZUFD2xYtYEow2BWLshP0Jvh-MYdg&co=feffff&cmo=75ff53&cmn=ff5353&ct=000000'></script>
