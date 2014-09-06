---
layout: post
title:  "Format.js and format.json are not the same..."
categories: code
---

Today's random bit of knowledge that came about from work:

In a Rails controller,
{% highlight ruby %}
respond_to |format| do
  format.js { render json: ... }
end
{% endhighlight %}
is quite obviously not the same as
{% highlight ruby %}
respond_to |format| do
  format.json { render json: ... }
end
{% endhighlight %}

and not paying attention to which one I'm using is probably going to cause problems, even if it doesn't happen server side.

It's worth knowing that js and json (in the examples above) refer to different MIME types.  That's all well and good, but all I really care about is that format.js sends back plain text (which causes a parsererror if you try to treat like straight up JSON) while format.json will actually send back data that's encoded as json.  All of which makes perfect sense, if only I read what I code...

###Resources

[Link to edge guides for working with javascript and rails][rails_guide]


[rails_guide]:    http://edgeguides.rubyonrails.org/working_with_javascript_in_rails.html