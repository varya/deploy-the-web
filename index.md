---

layout: varya

style: |

    #Launch h2 {
        margin:250px 0 0;
        color:#000000;
        text-align:center;
        font-size:100px;
        outline:none;
        text-shadow: 5px 0 15px #FEF1B5;

        }
    #Launch p {
        margin:10px 0 0;
        text-align:center;
        color:#000;
        font-style:italic;
        font-size:20px;
        }
        #Launch p a {
            color:#000;
            }

    #me .note,
    #me code {
        font-size: 75%;
    }

    #debian {
        background-image:url("pictures/package.jpg");
        background-repeat: no-repeat;
        background-position: right bottom;
    }

    #debian ul {
      font-size: 125%;
    }

    .terminal {
        background-color: #333;
        color: #FFF;
    }
    .terminal h2 {
        color: #CCC;
    }
    .terminal code {
        color: #FFF;
    }
    .terminal pre mark.comment {
        color: #FFF8DC;
    }

    #Picture h2 {
        color:#FFF;
        }
    #SeeMore h2 {
        font-size:100px
        }
    #SeeMore img {
        width:0.72em;
        height:0.72em;
        }
---

# Deploy the Web {#Launch}

By [Varya Stepanova](http://varya.me/)

![](pictures/launch.jpg)


## Leuk u te ontmoeten {#me}

    {
      name: "Varya Stepanova",
      from: "Russia",
      before: "<mark class="ya">Я</mark>ндекс, 5 years",
      now: "TMG Online"
    }

{:.note}
Яндекс [Yandex]: search engine in Russia, 2000 devs, 150 f/e.


## Time to deploy

1. Development
2. Testing
    - deploy to a testing server
3. Release
    - deploy to a production cluster

## Inside deployment

{:.big}
1. New files go onto the servers
2. Commands are run
3. Processes restart

## Manual deployment

{:.big}
- <del>Long</del> Looooooong
  - Time is <mark>money</mark>
- People make mistakes
  - No hot-fixes. They <mark>pay</mark> again.

## Automation

{:.big}
- Custom script
- Version control system
- Third-pary service
- Packages

## Debian packages for Web {#debian}

- [bit.ly/debian-basics](http://bit.ly/debian-basics)
- [bit.ly/debian4web-1](http://bit.ly/debian4web-1)
- [bit.ly/debian4web-2](http://bit.ly/debian4web-2)

## Why packages?

{:.compact .big}
- unification
- versions
- postinstall scripts
- easy to uninstall

{:.note .compact}
my-awesome-website_1.0.106<br/>
my-awesome-website_1.0.107

## Packing
{:.terminal .no-numbers}

    > debuild
    > debrelease

    <mark class="comment">my-awesome-wesite_2.10-102_amd64.build</mark>
    <mark class="comment">my-awesome-website_2.10-102_amd64.changes</mark>
    <mark class="comment">my-awesome-website_2.10-102.dsc</mark>
    <mark class="comment">my-awesome-website_2.10-102.dsc.asc</mark>
    <mark class="comment">my-awesome-website_2.10-102.tar.gz</mark>

## Installing
{:.terminal .no-numbers}

    > apt-get update
    > apt-get install my-awesome-website

## Web project contents

- Backend files & Database
- Static files
  - images
  - CSS
  - JavaScript
  - fonts

## Static cluster

When a file is requested the server returns an image, CSS or JavaScript file (as
well as static HTML). This is all what happens. Machines in the static cluster
<mark class="important">think&nbsp;less</mark> and <mark
class="important">serve&nbsp;fast</mark>. And they send headers to <mark
class="important">cache&nbsp;files&nbsp;forever.

## Static files deployment
{:.no-numbers}

    my-awesome-website_1.0.108
    my-awesome-website-static_1.0.108

- [awesome.tmg.nl]()
- [st.awesome.tmg.nl]() or [st.tmg.nl]() or [tmg.st/awesome/]()

## Solving the biggest problem
{:.no-numbers}

<figure markdown="1">

> There are only two hard things in Computer Science: <mark
> class="important">cache&nbsp;invalidation</mark> and
> naming things.

<figcaption>Phil Karlton</figcaption>
</figure>

{:.compact}
    http://tmg.st/awesome/logo.png
    http://tmg.st/awesome/logo1.png
    http://tmg.st/awesome/new/logo.png
    http://tmg.st/awesome/widget.js?dhsyb

## Versioning
{:.no-numbers}

    my-awesome-website-static_1.0.108

    http://tmg.st/awesome/1.0.108/logo.png
    http://tmg.st/awesome/1.0.108/js/widget.js

## Freeze URLs

{:.small}
    http://tmg.st/awesome/_/<mark>6rUIvSy1fLQ0Nn_OdCLP1h6IAcA</mark>.png

File name depends on its content and chages only when the&nbsp;content has been
changed.

## Static files mapping

    .logo {
      background:url("logo.png");
    }

{:.small .no-numbers .compact}
    .logo{background:url("http://tmg.st/awesome/_/6rUIvSy1fLQ0Nn_
    OdCLP1h6IAcA.png")}

A wonderful tool to do this is [Borschik](http://bem.info/tools/borschik/)

## Backend/Client

{:.no-numbers}
    my-awesome-website_1.0.108

{:.small .compact}
    <script src="http://tmg.st/awesome/1.0.108/page.js">
    </script>

{:.reset}
    my-awesome-website-static_1.0.108

{:.small .compact}
    http://tmg.st/awesome/1.0.108/page.js

## Backend/Frontent/Client

3-layer scheme

## Backend/Frontent/Client

{:.no-numbers}
    <backend>
    my-awesome-website-www_1.0.108
    my-awesome-website-static_1.0.108

## Robots to do this all

{:.big}
- Teamcity
- Jenkins

## Questions?
