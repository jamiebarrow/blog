# 2024-07-27 Blazor

Blazor was introduced back in 2018.
I am surprised that it has already been out for 6 years, since I have only recently begun a work project that makes use of it.

It is a technology that was made possible by Steve Sanderson, making use of WebSockets and WebAssembly to load and run a .NET runtime in the browser. State can be kept server side, and any updates needed to the DOM can be made asynchronously, sending only the parts needed to be updated through the WebSocket channel.

The browser platform has some limitations obviously such as security, access to the operating system and file system and so on, so there may be libraries that are not fully compatible with Blazor.

However, anything you could do previously with JavaScript in the browser can now be done with .NET code, enabling .NET developers to create web applications using components written with Razor templates and backing C# code. These Blazor components can then bridge a gap where .NET developers wished to create rich web applications, client side single page applications, or even still the traditional server side rendered websites, all with a single mental model of Blazor. It is then only a matter of choosing which hosting model is best suited to your application and/or webpages. A mixture is even possible, with some pages that don't need interactivity being rendered statically server side, and for the pages that do need interactivity they can be loaded using WebAssembly or even use an automatic mode where it is initially rendered server side and later made interactive once the .NET code begins to execute.


