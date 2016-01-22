---
title: How to add facebook like button to Jekyll blog.
desc: Adding facebook button on a Jekyll blog site is different compared to HTML sites. This is because Jekyll blogs have an advantage of including html files which are inside _includes folder. We are taking advantage of this option! 
keywords: facebook like button github pages, like button to jekyll blog
author: sharathdt
pulish: false
---

<img alt="" title="" itemprop="thumbnailUrl" src="/images/adding-facebook-like-button-to-jekyll.jpg">

Understanding Jekyll is really important to manipulate the options available to handle different things. One of those is templates. Usually all Jekyll themes will have a **header** and a **footer** inside ```_includes``` folder.

Most of the layouts make use of these templates. If you observe **default** layout inside  ```_layouts``` folder, you'll see that  at some point they have included header and footer with the following code.

<pre>
{% raw %}
{% include header.html %}
{% endraw %}

{% raw %}
{% include footer.html %}
{% endraw %}
</pre>

So they include header and footer respectively. This kind of templating can be done with any html inside ```_includes``` folder. 

A basic Jekyll site structure looks like this. 


{% highlight html %}

.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
├── .jekyll-metadata
└── index.html

{% endhighlight %}

*A master configuration file ```_config.yml``` and an ```index.html``` in the root.

*Folders such as ```_includes```, ```_layouts``` ```_posts```, ```_sass``` etc.,

I will be explaining the functions of these files and folders in a different post. For now I will be concentrating on ```_includes```.

Just like including header or footer with just a line of code, we can add html files inside ```_includes``` to spit it out wherever we want it.

For facebook like button, you should have a facebook page for your website or business. If you do not have one then [create one here](https://www.facebook.com/pages/create/){:rel='nofollow'}{:target="_blank"}.

Once you are done creating a page go here and get the code.