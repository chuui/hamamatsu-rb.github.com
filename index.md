---
layout: default
title: Hamamatsu.rb
---

Hamamatsu.rbは、静岡県浜松市周辺のRuby技術者やRubyに関心がある人が集まって、Rubyに関する何か(兼飲み会)をする予定の地域コミュニティです。

# ATND
<ul class="posts atnd-dest" ></ul>
<script id="atnd-template" type="text/x-jquery-tmpl">
    <li><span>${started_at}</span> &raquo; <a href="${event_url}">${title}</a></li>
</script>
<script type="text/javascript">
    function handleAtnd(results) {
        $("#atnd-template").tmpl(results.events).appendTo(".atnd-dest");
    }
</script>


# お知らせ
<ul class="posts">
{% for post in site.posts limit:5 %}
<li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>

# メーリングリスト

[Hamamatsu.rbのGoogleグループ](https://groups.google.com/group/hamamatsu-rb?hl=ja) へ参加してください。

<h1 style="margin-top: 2em">
Twitter
<a href="http://twitter.com/#!/hamamatsurb"><img src="http://a2.twimg.com/sticky/default_profile_images/default_profile_5_normal.png" width="24" height="24" style="vertical-align: middle; margin: 0 3px"></a>&nbsp;
<a href="http://twitter.com/#!/hamamatsurb" style="font: 0.8em normal; color: gray">@hamamatsurb</a>&nbsp;
<a href="http://twitter.com/#!/search/%23hamamatsurb" style="font: 0.8em normal; color: gray">#hamamatsurb</a>
<a href="http://twitter.com/?status=@hamamatsurb%20subscribe" style="font: 0.8em normal; color: gray">Twitterグループに参加</a>
</h1>
<div id="members"></div>

# Facebook
<iframe src="http://www.facebook.com/plugins/likebox.php?href=https%3A%2F%2Fwww.facebook.com%2Fpages%2FHamamatsurb%2F196508373706679&amp;width=585&amp;colorscheme=light&amp;show_faces=true&amp;stream=false&amp;header=false&amp;height=182" scrolling="no" frameborder="0" style="border:none; overflow:hidden; width:585px; height:182px;" allowTransparency="true"></iframe>

<script type="text/javascript" src="http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.8.3.min.js"></script>
<script type="text/javascript" src="http://ajax.microsoft.com/ajax/jquery.templates/beta1/jquery.tmpl.min.js"></script>

<script>
jQuery(function(){
  $.ajax({
    url: 'http://api.twitter.com/1/hamamatsurb/hamamatsu-rb/members.json',
    dataType: 'jsonp',
    success: function(data, dataType) {
      $.each(data.users, function(i, user) {
	var name = user.screen_name;
	var href = 'http://twitter.com/' + user.screen_name;
	var src = user.profile_image_url;
	var link = $('<a href="' + href + '" title="' + name + '"><img src="' + src + '" width="48" height="48" /></a>');
        $("#members").append(link);
      });
    },
    error: function(XMLHttpRequest, status, errorThrown) {
      console.log(status);
      $("#members").html("Oops, Something Is Wrong...");
    }
  });
});
</script>

<script type="text/javascript" src="http://api.atnd.org/events/?keyword=hamamatsu.rb&count=5&format=jsonp&callback=handleAtnd"></script>
