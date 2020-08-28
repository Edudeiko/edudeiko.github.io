---
layout: post
title: Building API
subtitle: Create easy to use Spotify API 
image: img/Spotify.jpg
gh-repo: Edudeiko/dj_helper_search_api
gh-badge: [star, fork, follow]
comments: true
---

While I was working for one of the projects, I couldn’t find desired Spotify API calls. At that time I needed the following: 1) Search function which will deliver **Artist Name**, **song name**, **song ID**, **external URL** is handy to listen for a whole song, **explicit** has two values True or False, **preview** gives you 30 seconds to listen a song and a cover **image** for the specific song.

### Register Spotify for Developers account
Before getting into the code you need to register an account at [Spotify for Developer](https://developer.spotify.com) and create an app in order to get **Client ID** and **Client Secret** keys. In edit settings add **Redirect URIs**. I added http://127.0.0.1:5000/callback/ and https://sp-search.herokuapp.com/callback/. You need to change it to your own localhost and to the host you will deploy your APIs to.


Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.
