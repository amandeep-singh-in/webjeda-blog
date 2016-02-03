---
title: Lazy loading CSS
desc: Loading JavaScript at the end is common but for a faster website one should load big CSS files at the end as well. Learn how to defer CSS loading which makes your website superfast. 
keywords: defer css, lazy load css, load css at the end
author: sharathdt
tags: Jekyll SEO
---

<img alt="" title="" itemprop="thumbnailUrl" src="/images/lazy-load-css-for-fast-website.jpg">
<a target="_blank" rel="nofollow" href="http://www.freepik.com/free-vector/cartoon-animals_802878.htm">Designed by Freepik</a>

## Why lazy load css?

Along with loading JavaScript after the document, you should also load big css files at the end. This makes your website superfast. Because the main content loads first. So even on a slow connection, the content will be available for the user.

In this method the content loads without any style and then the stylesheet loads followed by JavaScript. You may have observed this while browsing my website. This is important for a user with a slow connection. Content(visible stuff) should load at the very beginning. Style(css) and scripts(js) can wait.

This ensures that even if the style or script fails to load, user can still read the content (if the content is text). You can also [minify your blog for faster loading](/how-to-compress-html-in-jekyll).

What I did was, I put a script at the end of the html document to insert the css link tag only after loading the document. This was helpful because my ```main.css``` is a huge file and also fontawesome stylesheet that loads from a CDN.

After testing in [PageSpeed](https://developers.google.com/speed/pagespeed/insights/){:rel='nofollow'}{:target="_blank"} I found that my website is faster than ever! Do use this tool to find out what is slowing down your website.


## How to load CSS at the end?

This is possible if I declare my link tag at the end of the document. But it is advised to place link tags in the head section. So I'm using a script to place the link tag( linking css) in the head section.

{% highlight html %}

<script defer>
var cb = function() {
var l = document.createElement('link'); l.rel = 'stylesheet';
var m = document.createElement('link'); m.rel = 'stylesheet';
l.href = '/css/main.css';
m.href = 'https://maxcdn.bootstrapcdn.com/font-awesome/4.5.0/css/font-awesome.min.css';
var h = document.getElementsByTagName('head')[0]; h.parentNode.insertBefore(l, h);
var i = document.getElementsByTagName('head')[0]; i.parentNode.insertBefore(m, i);
};
var raf = requestAnimationFrame || mozRequestAnimationFrame ||
webkitRequestAnimationFrame || msRequestAnimationFrame;
if (raf) raf(cb);
else window.addEventListener('load', cb);
</script>

{% endhighlight %}

The above code loads two CSS files. One is local (main.css) and the other is remote (font-awesome.min.css). You can make use of this code and change it accordingly. Make sure you edit the path properly.


If you observe the script tag carefully, I have added ```defer``` attribute to it. This will load this script at the very end. You can change this to ```async``` if you want it to load along with the content. Test it out and see which one works best for you.

## Problems I faced while lazy loading css

This problem occurred because I have adsense. My adsense code is responsive. It adjusts to the screen-size mentioned in the media query. And the media query is inside ```main.css``` which I have made to load at the very end!

Adsense script loads before ```main.css``` and assumes that the screen is full width whereas my content is not full width. My content only goes in the center leaving some gap on both left and right sides. But adsense has already assumed that it is full screen and adjusts its ad size to full screen and hence the ad flows out of the content.

I struggled hard to tackle this. And after a while I realized that I can define the width of my content with inline-css even before the adsense code loads! Thus avoiding it to overflow.

{% highlight html %}
  <div id="container" style="max-width:730px;padding: 0 1.5rem;margin: 0 auto;">
        <main>
         {% raw %}{{ content }}{% endraw %}
        </main>
{% endhighlight %}

So that solved the problem :)


I hope this article has helped you to speed up your website. Let me know how it went. Leave a comment if you have any suggestion. I would be happy to implement it.


Thanks for reading!