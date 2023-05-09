# Wasm (Exotic Runtime Target)

subtitle
:   Ruby and Wasm on Kubernetes and GitOps Delivery Pipelines

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
* Don't want to lose everyone
* We're going to talk about Wasm

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

* Flux Bug Scrub - weekly(ish) for over a year
* You need an Open Source Support Engineer
* (Someone that uses your OSS deeply)
* Find Flux at GitOpsCon/OSS Summit

# Flux Talks

![](images/fluxqr.jpeg "QR Code"){:width='100' height='100'}

# Intro (me)

* On YouTube - I'm new here
* Let's Study: Arabic
* Cloud Jockey: %radio ⚡️🌩️🌀🌩️⚡️
* Live Coding: Ruby + Kubernetes

# Wasm and Ruby

* *What is this for*
* What is "untrusted code"
* Why do we want to run it

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

# Compiled Languages

* Rust
* Go
* JavaScript, TypeScript
* C#
* ...

# Web Assembly in Ruby

* Ruby is an interpreted language
* wasmer-ruby
* wasmtime-rb
* Run Web Assemblies in Ruby
* What is a Web Assembly?

# Bytecode Runtime Format

* Can you run Ruby in Web Assembly?
* Yes, but first...
* Web Assembly is a binary
  * You can run it
* Web Assembly is also a library
  * Include it in other programs

# Web Assembly

* Call functions from it
* Ship memory around
* Export functions to it
* Use a compiler
* Or...
* System Interface (WASI)

# Features: Format

* What is a system interface?
* Stdio
* There is no network
* How do you run a server?
  * WAGI (it's like CGI!)

# Omitted Features

* Wasm does not have a string type
* Numbers and well-defined data structures
* You can allocate memory and make a pointer
* Keep the length around

# Ruby and pointers

* I don't want to do pointer math at all
* Could not figure out how to do:
  * Wasm as library
* I spent some time on this
* Reverted to WASI
* We can parse the output 👍

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

# Why are we here?

* Hope to gain:
* Testability
* Reusability
* Type safety between languages

# How about we dive in?

* I built some things in Wasm
* Here's what not to do
* I needed to break misconceptions
* How are we going to use this?

# I built some things

* EKS cluster: [kingdonb/eks-cluster][]
  * with Flux bootstrap (eksctl+flux 2.0.0-rc.2)
* 

[kingdonb/eks-cluster]: https://github.com/kingdonb/eks-cluster

# ToDo

  * Inline images
  * Jump to a link
  * Sound
  * Video
  * 3D

# Image

![](lavie.png "Lavie"){:width='100' height='100'}

# Image: Reflect

![](shocker.jpg){:relative_height='80' reflect_ratio='0.5'}

# Image: Background (1)

* Background image
* Centering by default

## Properties

background-image
:   lavie.png

background-image-relative-width
:   50

{::comment}
background-image-align
:   right

background-image-relative-margin-right
:   3
{:/comment}

# Image: Background (2)

![](lavie.png){:relative_width="30" align="right" relative_margin_right="-5"}

* Right justified backgorund image
* Specify in slide
  * \{:align="right"\}

# Image size

Relative image sizes

![](usagi.png){:caption="USAGI" relative_height="50"}

# External image

Download an image from a URL

![](https://raw.githubusercontent.com/rabbit-shocker/rabbit/master/data/rabbit/image/cozmixng-images/cozmixchu.png "COZMIX Chu")

# Math. expressions

* TeX format
* Backends
  * LaTeX

# LaTeX

$$
$f(x)=\displaystyle\int_{-\infty}^x~e^{-t^2}dt$

\LaTeX
$$

# EPS

Create EPS ahead of time

![](equation.eps){:relative_width="80"}

# SVG

![](spiral.svg){:relative_height="100"}

# Dia

![](rabbit.dia){:relative_width="90"}

# GIMP

![](rabbit.xcf){:relative_height="100"}

# Word Wrapping

looooooooooooooooooooooooooooooooooooooooooooooooooooooooooooong

# Source

The following is source code:

# comment
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
