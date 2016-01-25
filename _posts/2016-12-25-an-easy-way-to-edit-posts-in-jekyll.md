---
title: How to add or edit posts in Jekyll
desc: For beginners an easy online editing is beneficial. Learn how to add posts, edit posts and other Jekyll files online through prose.io in this tutorial. Also find out how to upload images using prose.io!
keywords: edit post in Jekyll, edit page in jekyll, add post in jekyll
author: sharathdt
tags: jekyll
---

<img alt="Creating pages in Jekyll" title="Make a new html page in Jekyll" itemprop="thumbnailUrl" src="/images/how-to-edit-add-posts-in-jekyll.jpg">
<a rel="nofollow" target="_blank" href="http://www.freepik.com/free-vector/office-banners_800177.htm">Design by Freepik</a>

In my initial days of blogging with Jekyll, I used to edit posts directly inside Github repository. All the posts will be iside ```_posts``` folder. Editing was easy since it was markdown. But the real struggle was to inserting images. If the image source is a URL then it was easy but if the image is in my local computer folder then there was no way uploading it. I did not know [how to sync files and folders with Github](http://blog.webjeda.com/how-to-sync-files-folders-with-github){:rel='dofollow'}{:target="_blank"}.

## Unable to upload images to Github!
So I used to upload images to my google drive, then get the URL and put that as a source in the blog. One of those examples here
[Image from google](https://lh3.googleusercontent.com/-j3S-KX7DwQ0/VDi4p2xTzVI/AAAAAAAAAGo/_PP4-udRS4c/s550-no/moto-hint-story-pairit-us.jpg){:rel='nofollow'}{:target="_blank"}.

Since you are making a http request, it would take a longer time to load the page. I was not aware of these things. That was my workaround for not being able to upload files to Github.


## A nice tool to upload images to Github
Eventually I found out a tool called [prose](http://prose.io){:rel='nofollow'}{:target="_blank"}. It was good, the interface, functionality and even the animations!
![Prose.io jekyll editor screenshot](/images/how-to-use-prose-io-with-jekyll.jpg)

I was really impressed with this webapp with a feature to upload images. All you need is to add these lines of code inside ```_config.yml```. This will solve the problem of prose.io not uploading images!

{% highlight yaml %}

prose:
  rooturl: '_posts'
  siteurl: 'http://prose.github.io/starter/'
  relativeLinks: 'http://prose.github.io/starter/links.jsonp'
  media: 'media'
  ignore:
    - index.md
    - _config.yml
    - /_layouts
    - /_includes
  metadata:
    _posts:
      - name: "layout"
        field:
          element: "hidden"
          value: "blog"
      - name: "tags"
        field:
          element: "multiselect"
          label: "Add Tags"
          placeholder: "Choose Tags"
          options:
            - name: "Apples"
              value: "apples"
            - name: "Bananas"
              value: "bananas"
    _posts/static:
      - name: "layout"
        field:
          element: "hidden"
          value: "page"
      - name: "permalink"
        field:
          element: "text"
          label: "Permalink"
          value: ""
{% endhighlight %}

{% include adsense-inside-post.html %}

Image upload window on prose.io

![Upload images to github using prose](/images/upload-image-to-github-using-prose.jpg)

Let's say you have a non-jekyll website hosted on Github Pages. Prose.io can be used to edit that as well! But you have to create a ```_prose.yml``` file in the root of your repo and copy paste the same code!

I was happy that I found an option to completely edit my Jekyll posts online. 

Now in the above snippet, you can change the ```rooturl:``` to any folder you want. I have chosen ```_posts``` because that is the folder I often navigate to edit or add new posts.

## Why prose.io?
Once you figure out how to sync files with Github from your local folders then you will realize that ```prose.io``` is not even required and you may think that you have been following the hard way all this time. But syncing files to Github can be hard for many beginners. Unless you have a little understanding about how ```git``` works, you cannot successfully sync files or at least cannot troubleshoot a simple issue.

This is the reason why I recommend prose.io for beginners. It is simple, easy and GUI!

In situations where you are using a chromebook, there isn't any convinient way to sync Github files locally. May be in the future Github will release apps for **Chrome Os** and **Android** but for now there is no option. 

And also while travelling you may just have a smartphone or a tablet with you. In such case you will appreciate prose.io!

I'm searching for a reliable Android app that can edit Jekyll posts. Let me know if you find one.

Thanks for reading!