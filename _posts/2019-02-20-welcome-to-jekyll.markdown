---
layout: post
title:  "Welcome to Jekyll!"
categories: Jekyll markdown github
---

You'll find this post in your `_posts` directory - edit this post and re-build (or run with the `-w` switch) to see your changes!
To add new posts, simply add a file in the `_posts` directory that follows the convention: YYYY-MM-DD-name-of-post.ext.

**Jekyll**  also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')

#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

and you can also use markdown code highlighter:

```python
def print_hi(name):
	print "Hello, world!"
print_hi('Jerry')
```

one more highlighter example:

{% highlight java %}
package com.walleops.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.servlet.ModelAndView;

/*
 * author: Aaron Yao
 */
@Controller
public class WalleopsHelloworld {

	@RequestMapping("/welcome")
	public ModelAndView helloworld() {
		String message = "<br><div style='text-align:center;'>"
				+ "<h3> Hello guy, this page comes from branch_for_test_merge.</h3>"
				+ "This message is coming from CrunchifyHelloWorld.java </div><br><br>";
		return new ModelAndView("welcome", "message", message);
	}
}
{% endhighlight %}

Your Jekyll blog source code and posts can be managed on github free, and github pages provides free host, so after composed blog, you can commit you post on github, and it will be built and published automatically. Check out [Github pages][gh-pages] for more information.

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll's GitHub repo][jekyll-gh].

[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
[gh-pages]: http://pages.github.io
