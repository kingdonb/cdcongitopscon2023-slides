# wasm

subtitle
:   Exotic Runtime Targets for GitOps Delivery Pipelines (wasm, ruby, k8s, gitops)

author
:   Kingdon Barrett

institution
:   Weaveworks

theme
:   rabbit-theme-wwinternalstyle

date
:   2023-05-09

allotted-time
:   15m

start-time
:   2023-05-09T15:05:00-07:00

end-time
:   2023-05-09T15:20:00-07:00

# Lightning Talk


Gotta go pretty fast

* Try not to talk so fast
* Don't want to lose you
* Many twists and turns
* Rabbit-shocker timer to help keep honest!

# Intro

* Hi
  I'm Kingdon Barrett
* Find me on YouTube or Mastodon
* youtube.com/@yebyen
* hachyderm.io/@yebyen

# Job

* Weaveworks: Dev Experience
* OSS Engineer since 2021
* Second S is for ~~Smooth Operator~~ (no, it's Support!)
* I work on Flux (Maintainer)

# Flux

* Flux Bug Scrub - weekly [fluxcd.io/#calendar][]
* ?: OS _Support_ Engineer
* (I use our OSS deeply)
* Lean into OSS solutions

[fluxcd.io/#calendar]: https://fluxcd.io/#calendar

# Flux Talks

![](images/fluxqr.jpeg "bit.ly/gitopscon2023"){:width='350' height='350'}

# Intro (me)

* On YouTube - I'm new here
* Let's Study: Arabic
* Cloud Jockey: %radio ⚡️🌩️🌀
* Live Coding: Ruby + Kubernetes
* Plz mash like & subscribe

# Wasm and Ruby

* *What is this for*
* What is "untrusted code"
* Why do we want to run it
* Healthy skepticism about (even our own) code

# Ruby

* Can Wasm? run it
* Yes
* Why would we do that?
  * This is a serious question
  * Do you know why Wasm?

# Why Wasm

* Secure Foundation
* "Bytecode Alliance"
* Portable artifacts
  * with language independence

# Why Wasm

* Frankly I cannot sell Wasm
* No commission either
* If you take it, I get nothing
* I think it will be useful
* Let's find out together

# Why Kubernetes

* For Flux and GitOps
* If you chose Kubernetes, you already know why you did (!)
* Declarative, versioned, immutable artifacts
* Self-healing infrastructure

# Compiled Languages

* Rust
* Go
* JavaScript, TypeScript
* C#
* ... (value for you all as well)

# Why Ruby

* I used Ruby since 2002(?)
* Comfort and familiarity
* Top Notch Debugging ++
* Bundler, Fibers, Ruby 3.0
* for faster time to market

# Ruby Solutions

* To run a website
* To connect a database
* scrape content from internet
* To build an IRC bot
* No compiler needed, duck typing, object orientation

# Web Assembly in Ruby

* Ruby is interpreted language
* gem: wasmer-ruby
* gem: wasmtime-rb
* Run Web Assemblies in Ruby
* What is a Web Assembly?

# Bytecode Runtime Format

* Can run Ruby in Wasm?
* Yes, but first...
* Wasm is a binary format
* Wasm also builds libraries
  * Include it in other programs

# Ruby in Ruby?

* Consider not doing this
* No theoretical benefit afaict
* It was the first thing I tried
* I could not make it work
* Let's try the other thing

# Web Assembly

* Call functions from it
* Ship memory around
* Export functions to it
* Use a compiler, or...
* System Interface (WASI)

# Features: Format

* What is a system interface?
* Stdio
* There is no network
* How do you run a server?
  * WAGI (it's like CGI!)

# Omitted Features

* Wasm has no string type
* Numbers and well-defined data structures only(ish)
* Allocate memory, make ptr
* Pass ptr to str+length/size

# Ruby and pointers

* I don't want to do pointer math at all
* Could not figure out how do:
  * Wasm as library
* I spent some time on this, couldn't figure unfortunately

# Ruby and Wasm lib

* I need string return values
* Reverted to WASI
* We can parse the output 👍
* Now let's try to solve a real problem

# What is Spin?

* Fermyon "Serverless" framework
* Test locally
* Run on Fermyon Cloud
* (Run on Hippo Factory)
  * This is OSS Summit!

# What is Spin?

* Fermyon "Serverless" framework
* Test locally
* Run on Fermyon Cloud
* (Run on Hippo Factory)
  * ~~This is OSS Summit!~~

# What is Spin?

* Fermyon "Serverless" framework
* Test locally
* Run on Fermyon Cloud
* (Run on Hippo Factory)
  * This is GitOpsCon!

# Why are we here?

* Hope to gain:
* Testability
* Reusability
* Type safety btw languages
* Capacity for polyglot teams

# How about we dive in?

* I built some things in Wasm
* Break misconceptions
* Follow good examples
* How are we going to use this?
* Let's solve real problem now

# Problem to explore

* GitHub Packages problem - DX Engineer solution
* fluxcd/flagger/
* [pkgs/container/flagger][]
* Need to know how many downloads for each package

[pkgs/container/flagger]: https://github.com/fluxcd/flagger/pkgs/container/flagger

# I built some things

* EKS cluster: Find on GitHub [kingdonb/eks-cluster][]
  * with Flux bootstrap (eksctl+flux 2.0.0-rc.2)

# I built some things

* Blog service: GitHub [kingdonb/taking-bartholo][]
  * GitOps enabled via Helm Controller
  * Helm + Helmet library chart
  * At this point I began to understand
    * Why Fermyon isn't using K8s or Helm?
    * This would be really hard without Flux

# I built more things

* Kubernetes operator: [kingdonb/stats-tracker-ghcr][]
  * Fetch from URL (in ruby)
  * Parse HTML (in rust)
  * Return number as string (WASI!)
  * Parse number (we're back in Ruby)

# Based on

* Kubernetes operator: (GitLab) [tobiaskuntzsch/kubernetes-operator][]
  * Wonderful example for learning about Operators with Ruby
  * Register CRD, Register `upsert`
  * Register `delete` - manages your Finalizers

# Based on (dependency)

* Kubeclient gem: GitHub [ManageIQ/kubeclient][]
  * Also easy to use
  * Server-side apply only (!)

# Out of time

* Lightning talk - Fin
* Dive into these topics in more depth
  * OSS Summit
  * More Ruby: Wednesday
  * Go, TypeScript: Thursday

# Operator isn't finished

* Let's do it live (today)
* On YouTube
* (We'll hear how it went tomorrow)
* It is really 98% finished already :D

# Let's do it live

* I wrote this in an hour live
* Code is there
* Only missing a tiny bit
* My first Rust program!

# Thank You



[kingdonb/eks-cluster]: https://github.com/kingdonb/eks-cluster
[kingdonb/taking-bartholo]: https://github.com/kingdonb/eks-cluster
[kingdonb/stats-tracker-ghcr]: https://github.com/kingdonb/eks-cluster
[tobiaskuntzsch/kubernetes-operator]: https://gitlab.com/tobiaskuntzsch/kubernetes-operator
[ManageIQ/kubeclient]: https://github.com/ManageIQ/kubeclient

# ToDo

  * Inline images
  * Jump to a link
  * Sound
  * Video
  * 3D

# Image

![](images/fluxqr.jpeg "Lavie"){:width='100' height='100'}

# Image: Reflect

![](images/fluxqr.jpeg){:relative_height='80' reflect_ratio='0.5'}

# Image: Background (1)

* Background image
* Centering by default

## Properties

background-image
:   images/fluxqr.jpeg

background-image-relative-width
:   50

{::comment}
background-image-align
:   right

background-image-relative-margin-right
:   3
{:/comment}

# Image: Background (2)

![](images/fluxqr.jpeg){:relative_width="30" align="right" relative_margin_right="-5"}

* Right justified backgorund image
* Specify in slide
  * \{:align="right"\}

# Image size

Relative image sizes

![](images/fluxqr.jpeg){:caption="USAGI" relative_height="50"}

# External image

Download an image from a URL

![](images/fluxqr.jpeg "COZMIX Chu")

: comment
def method_name
  body
end

End of source code.

# Source: Highlighted

The following is source code:

# comment
def method_name
  body
end
{: lang="ruby"}

End of source code.

# Quotation

> You take the ''red pill'', you stay in Wonderland and 
> I show you how deep the ''rabbit-hole'' goes.

# Enumeration

* Level 1-1
  * Level 2-1
* Level 3-1
* Level 3-2
  * Level 2-2
* Level 1-2

# Labeled list

Rabbit
:   USAGI

Tortoise
:   KAME

USAGI
:   Rabbit

# Table

| Heading 1 | Heading 2 |
|---------|--------|
| content 1 | content 2 |
| very long content 3 | veeeery looooooooooooooooooooooong content 4 |

# Op.: Move

Next page
:   Bindings for next page/Left click

n, f, j, l, Spc, Ret, +, ↓, →, ...

Previous page
:   Bindings for prev. page/Center click

p, b, k, h, BS, Del, -, ↑, ←, ...

# Op.: Advanced move

Go to the title page
:   a, 0, <, Home

Go to page n
:   1-9, +Ctrl=+10, +Alt=+20

Go to the last page
:   e, $, >, End

# Op.: On stage (1)

Toggle full screen
:   F5, F10, F11, Gesture↓↑

Toggle index mode
:   i

Go to the page
:   Double click on the desired page

# Op.: On stage (2)

Cache all slides
:   c

Toggle info window
:   I

# Op.: On stage (3)

Magnifier
:   Ctrl + right click

Change scale by wheel

Spotlight
:   Double right clicks

Change radius by wheel

# Op.: On stage (4)

Graffiti
:   Popup menu (right click) →
"Graffiti mode"

Mouse gesture
:   Right button drag

# Op.: On stage (5)

Whiteout
:   W

Blackout
:   B

# Op.: Save

Screenshot
:   Save each page as an image

s

Print
:   Print each page as PS/PDF

Ctrl+p

# Op.: Display

Redraw
:   Ctrl+l

Reload theme
:   t, r

Reset slide adjustment
:   Alt+a

# Op.: Hole

Expand the hole
:   E

Narrow the hole
:   N

# Op.: Search

Search forward
:   C-s, /

Search backward
:   C-r, ?

Quit search
:   C-g

# Op.: Quit

Quit
:   q, Escape

Iconify
:   z

# Conclusion

* A presentation tool
* Multi platform
* Feat./UI: High & Unique
* Emphasize keybord shortcuts
  * UI/text based source
