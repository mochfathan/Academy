---
title: "raw"
description: No liquid will be parsed in within these tags.
sub_category: Other
---
##### Input

{% assign l_bracket = "{" %}
{% assign r_bracket = "}" %}
{% raw %}
~~~liquid{% raw %}
  {{ page.title }}{% endraw %}
{{ l_bracket}}% endraw %{{ r_bracket }}
~~~

##### Output
{% raw %}
~~~html
{{ page.title }}
~~~
{% endraw %}
