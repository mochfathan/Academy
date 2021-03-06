---
date: 2017-02-06
title: Introduction to includes
video_id: GXtx42MOiww
description: Jekyll includes let you include page fragments on your site
tags:
  - jekyll-includes
resources:
  - name: "Include documentation"
    link: https://jekyllrb.com/docs/frontmatter/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/includes
type: Video
set: basics
set_order: 10
icon: include
---
## Introduction

On this example `index.html` there's a subscribe to our newsletter section.

![Newsletter section](/images/tutorials/includes/newsletter-section.png){: .screenshot}

We also want this newsletter section on `blog.html`. One way of doing this would be to copy the newsletter section HTML and paste it into `blog.html`. This works but we've duplicated source code on the website. If we ever wanted to change content inside the newsletter section, then we'd have to make the change in multiple places. A better solution is to use Jekyll includes.

## Implementation

To use an include we'll create a new folder called `_includes`. Inside this we'll create a new file called `newsletter.html`. Now we'll copy the source code for the newsletter section across to `newsletter.html`:

{% raw %}
~~~html
<div class="newsletter spacing">
  <form action="">
    <h3>Subscribe to our mailing list!</h3>
    <label for="email">Email</label>
    <input type="email" name="email" id="email">

    <input type="submit" value="Subscribe">
  </form>
</div>
~~~
{% endraw %}

In `index.html` we can replace the newsletter section with the include:

{% raw %}
~~~html
...
{% include newsletter.html %}
...
~~~
{% endraw %}

We can also use this newsletter include on `blog.html`. If we change `newsletter.html` it's reflected on both pages.

## Passing parameters to an include

In more complicated situations you can pass parameters to an include. In this example we're going to add YouTube videos to the site which we always want presented in a consistent way. We need them to be centered and a particular size.

Let's create a new include, `_includes/youtube.html`. In this file we'll create the structure for displaying a YouTube video and have a placeholder for the YouTube video id. We can access parameters passed to an include using `include.variable_name`.

{% raw %}
~~~html
<div class="spacing youtube">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/{{ include.youtube_id }}" frameborder="0" allowfullscreen></iframe>
</div>
~~~
{% endraw %}

We can use this include throughout our site and pass in the video id we want to display:

{% raw %}
~~~html
{% include youtube.html youtube_id="YIiHiMXOeYU" %}
~~~
{% endraw %}
