# 2011-06-15 Improving website performance

tags: apache, ASP.NET, google page speed, MIX11, mod_pagespeed, page speed, performance, website performance, yslow

I was watching a [very interesting video from MIX11](https://channel9.msdn.com/Events/MIX/MIX11/FRM04) which deals with optimizing website performance using ASP.NET. A lot of the tips are general to web development, and not just ASP.NET, so I think it's worth watching for anyone. If you don't feel like watching it, then at least just check out the below:
- [Yahoo's YSlow](https://developer.yahoo.com/yslow/) Plugin
- [Google's Page Speed](https://code.google.com/speed/page-speed/) Plugin
- [Best Practices for Speeding Up Your Web Site](https://developer.yahoo.com/performance/rules.html), from Yahoo
- [Page Speed Family](https://code.google.com/speed/page-speed/docs/overview.html), from Google (look for the 'Page Speed rules' menu)

At the time that I was looking into these plugins, Page Speed wasn't available for Firefox 4 (I believe it is now?) so I didn't try it out, but they basically both grade your website and give you tips on how to improve it - for example, if you don't have compression turned on, if you don't minify your JavaScript, or if your number of requests is high. Along with what is wrong and short tips on how to improve, you also get links to articles on the web explaining the concept. Take YSlow for example: if you haven't setup ETags you can click the 'Read More' link, which takes you to Yahoo's ["Best Practices for Speeding Up Your Web Site"](https://developer.yahoo.com/performance/rules.html) page, to the ["Configure ETags"](https://developer.yahoo.com/performance/rules.html#etags) section.

So try them today, and don't worry about getting 100%, but try get to at least 90% - even small things like ensuring GZIP compression is turned on will make a noticeable difference.

There is also a <b>mod_pagespeed</b> Apache module from Google Page Speed which can do automatic optimizations, I haven't tried that, nor would I really be confident in trying it just because I'm a control freak, but it is from Google so it probably just works. If anyone has used it successfully, please let me know.
