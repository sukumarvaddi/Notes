# Getting Started with ASP.Net Core

## Introduction

---

ASP.NET Core is a cross platform web framework to build server rendered dynamic web applications. This framework can also be used to develop RESTful endpoints that can be called by mobile applications as well as SPAs. This endpoints can be called by other backend applications as well. This framework abstracts away client HTTP requests and other networking details. You will eventually write request handlers using the primitives provided by the framework. These handlers call into your domain logic you write in C# language.

The framework provides libraries to make following tasks easy.

- Login facilities for the user
- Generating dynamic webpages
- Logging client requests
- Common structure for building web application.
- Providing Custom configurations through files and reading those files.
- Serving static content (images, CSS, JS etc.)

> History of ASP.NET Core

_ASP.NET Core is released in 2016 and is an evolution of Microsoft's time tested ASP.NET Web framework. ASP.NET Core is completely re written from the scratch to keep up with the latest trends that have been happening in other web frameworks. The first version of ASP.NET was released way back in 2002. ASP.NET web forms allowed developers to create simple web apps fast using a graphical designer and event model. This mimicked the desktop application building trends. But the rapidly changing web eco system allowed building large scale web applications. But ASP.NET web forms could not scale up to build such large scale applications. It lacked the ability to test and has a complex state model. It also has limited control on what sort of HTML is generated._

_ASP.NET MVC was released in 2009 to overcome the inherent problems in ASP.NET. This is based on Model-View-Controller design pattern. This separated UI from domain logic and solved the problems in ASP.Net. This is built on underlying framework provided by System.Web.dll file which is part of .NET framework that came preinstalled with windows. This has an explicit dependency on IIS which is not available on other OS platforms. Finally ASP.NET Core is the result of demand for a cross platform framework. ASP.NET core is open source._

ASP.NET core runs on light weight platform called .NET Core that runs on Windows, Linux and Mac OS. .NET core is rechristened to .net 5 after .NET Core version 3.1. As of this writing the latest version of .NET Core is .Net 6.0

We can build cross platform console applications using .NET Core. ASP.NET Core is an additional layer on .NET core Console applications. With is, by adding and composing libraries we can turn a console application into a web applications.
All you do is run a .NET Core console application and that runs an instance of ASP.NET Core Webserver. A cross platform Webserver called 'Kestrel' is provided by microsoft. The web application logic is run by Kestrel server. Additional libraries are added as required to enable logging and HTML generation.

You will find libraries that are used with ASP.NET Core [here](https://github.com/dotnet/aspnetcore). Core libraries needed for most web applications such as the authentication and logging libraries, libraries for reading configuration information and third party libraries for authentication using facebook or google could be found at the above link.

## How does ASP.NET Core application Work?

---

When a HTTP request is made by client such as browser, the request reaches the ASP.NET core webserver (Kestrel by default).
The server receives the request and passes it to the middle ware. The application which is hosted on this core server process the request and a response is generated. Response is passed through the same middleware stack the request is passed through but in the reverse order. Finally the webserver receives this response and sends that to the client that made the request.

As soon the Kestrel server receives the request, it constructs an internal representation of the data. It is basically an object of type **HttpContext**. This object has all the details to create a response.

_Though we can expose Kestrel server to directly to the internet, it is customary to use reverse proxy. Reverse proxy is a server responsible for receiving the requests and forwarding them to appropriate web servers. This reverse proxy is directly exposed to the internet. The underlying server is only exposed to reverse proxy. This setup enhances security and performance of the web servers. Proxy servers are battle hardened against potential threats on the internet. They perform additional aspects. One of that is restarting the process that was crashed. Kestrel can be free of those additional responsibilities and remain simple._
