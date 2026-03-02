---
layout: post
title: youtube-dl
subtitle: A CLI tool to download videos and subtitles from the web
categories: [Linux]
tags: [CLI, ascii, subtitle, youtube-dl]
lang: en
---
[youtube-dl](https://ytdl-org.github.io/youtube-dl/index.html) is a command-line program to download videos and subtitles from youtube. It works not only on youtube.com, but on many more sites. [Supported sites](https://ytdl-org.github.io/youtube-dl/supportedsites.html)
To download the most recent version [visit project](https://github.com/ytdl-org/youtube-dl) page and follow the install instructions.
<div class="alert alert-dark" role="alert">Caveat: see a recent issue/bug raised on <a href="https://www.reddit.com/r/youtubedl/comments/cjilhz/fyi_since_googleyoutube_just_broke_youtubedl/">r/youtubedl!</a></div>

# Example 1 - download English subtitles only
I borrowed from this [discussion](https://superuser.com/questions/927523/how-to-download-only-subtitles-of-videos-using-youtube-dl).

When you need to download only subtitles in a given or all languages you have the following options according to the [documentations](https://github.com/ytdl-org/youtube-dl/blob/master/README.md#options) (`man youtube-dl` or `youtube-dl -h` depending on install method).
[![screenshot]({{ site.baseurl }}/assets/img/20-02-04/yt-man.jpg)]({{ site.baseurl }}/assets/img/20-02-04/yt-man.jpg)

The following command will download subtitles this [video](https://youtu.be/gDqAnOyAgt4) (America's Great Divide: Steve Bannon, 2nd Interview)
Note: You can check the available languages and formats with `youtube-dl --list-subs YOUR_URI`. `--sub-lang en` specifies **English** langugage, and `skip-download` is the **only** part, that is an opt for subtitles only. In this way video content will not be downloaded.

```sh
youtube-dl --write-sub --sub-lang en --skip-download https://youtu.be/gDqAnOyAgt4
```

The result will be a WebVTT (with .vtt extension) text file, that can be process or use for one's purpose.


	WEBVTT
	Kind: captions
	Language: en

	00:00:00.000 --> 00:00:03.580
	 So we’re in the summer of 2017.

	00:00:03.580 --> 00:00:06.416
	The president is waffling on DACA [Deferred Action for Childhood Arrivals].

	00:00:06.416 --> 00:00:08.048
	You recognize that.

# Example 2 [Get only part of a video - TBC](#)

[How to download portion of video with youtube-dl command?](https://unix.stackexchange.com/questions/230481/how-to-download-portion-of-video-with-youtube-dl-command)

	youtube-dl -g "https://www.youtube.com/watch?v=V_f2QkBdbRI"

	-g, --get-url Simulate, quiet but print URL
&
cut out 10 seconds from the start at (15.00 second)

	ffmpeg -ss 00:00:15.00 -i "OUTPUT-OF-FIRST URL" -t 00:00:10.00 -c copy out.mp4

superuser- [Cutting Video](https://blog.superuser.com/2012/02/24/ffmpeg-the-ultimate-video-and-audio-manipulation-tool/) guide says:

"The time values can either be seconds or in the form of HH:MM:SS.ms. So, you could also cut one minute, ten seconds and 500 milliseconds:"

	ffmpeg -ss 00:01:30 -i input.mov -c:v copy -c:a copy -t 00:01:30.500 output.mov

## Posts in "Linux" category:

{% for post in site.categories.Linux %}
  <ul>
        {% if post.lang == 'en' %}
          <li>
            <a href='{{ post.url | absolute_url }}'>{{ post.title }}</a>
          </li>
        {% endif %}
  </ul>
{% endfor %}
