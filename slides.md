# Exotic Runtimes

subtitle
:   Ruby and Wasm on Kubernetes and GitOps Delivery Pipelines

author
:   Kingdon Barrett

institution
:   Weaveworks

theme
:   rabbit-theme-wwinternalstyle

date
:   2023-05-10

allotted-time
:   40m

start-time
:   2023-05-10T11:10:00-07:00

end-time
:   2023-05-10T11:50:00-07:00

# Full Session Today

ICYMI:

* Yesterday, this was a lightning talk
* Will repeat most of that info today
* (Won't assume you've seen it)
* Check out GitOpsCon when those sessions get posted to YouTube!

# Intro

* Hi
  I'm Kingdon Barrett
* Find me on YouTube or Mastodon
* [youtube.com/@yebyen][]
* [hachyderm.io/@yebyen][]

[youtube.com/@yebyen]: https://youtube.com/@yebyen
[hachyderm.io/@yebyen]: https://hachyderm.io/@yebyen

# Job

* Weaveworks: Developer Experience
* OSS Engineer @ WW since 2021
* Second S is for ~~Smooth Operator~~
  (no, it's Open Source **Support**!)
* Work on Flux (Slack/ web/ community maintainer, former Flux v1 maintainer)

# Flux

* Flux Bug Scrub - weekly
  [fluxcd.io/#calendar][]
* What: OS _Support_ Engineer
* (I try to use our OSS deeply)
* Lean into fully OSS solutions

[fluxcd.io/#calendar]: https://fluxcd.io/#calendar

# Flux Talks

![](images/fluxqr.jpeg "bit.ly/gitopscon2023"){:width='250' height='250'}

# Intro (me)

* On YouTube - I'm new here
* Let's Study: Arabic
* Cloud Jockey: `%radio` DJ
* Live Coding: Ruby + Kubernetes
* (Please mash like & subscribe button)

# Wasm and Ruby

* *What are we here for today*
* What is "untrusted code"
* Why do we want to run it
* Healthy skepticism about
  (yes, even our own) code

# Ruby

* Can Wasm? run it
* Yes
* Why would we do that?
  * This is a serious question
  * Do you know why Wasm? (What is Wasm?)

# Why Wasm

* Secure Foundation
* "Bytecode Alliance"
* Portable artifacts
  * with a degree of language independence

# Why Wasm

* Frankly I cannot sell Wasm
  * No commission either
* If you take it with you, I get nothing
  * I think it will be useful
  * Let's find out together

# Why Kubernetes

* For Flux and GitOps
* If you chose Kubernetes,
  you already know why you did (!)
* Declarative, versioned, immutable artifacts describe a desired state
* Self-healing infrastructure

# Compiled Languages

* Rust
* Go
* JavaScript, TypeScript
* C#
* ... (value for you all as well)

# History as a Rubyist

* I used Ruby since 2002(?)
  * Thanks Eivind - Enlightenment, E16, E17, `#gah` on ~~EFnet~~, ~~Freenode~~, IRC (I'm old now)
  * First "permanent job"
    at Metrix Matrix in Rochester, NY
  * Second "permanent job"
    at University of Notre Dame OIT, South Bend

# Why Ruby?

* I know it better than other languages
* Comfort and familiarity
  * Top Notch Debugging ++
  * Bundler, Fibers, Ruby 3.0
* MVP: for faster time to market

# Ruby Solutions

* To run a website
* To connect a database
  * scrape content from internet
  * To build an IRC bot
  * No compiler, duck typing, object orientation, imperative, monkey patching, ease of use

# More Ideas: Ruby Solutions

* To build a K8s Operator, of course
  because why not!

# Web Assembly in Ruby

* Ruby: interpreted language
* gem: wasmer-ruby
* gem: wasmtime-rb
* Run Wasms in Ruby
* What is a Web Assembly?

# Runtime Format

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
* Stdio, filesystem, (restricted) HTTP/S
* There is no network
* How do you run a server?
  * WAGI (like CGI!) offload responsibility of conn

# Omitted Features

* Has no string type, tough limitations
* Numbers and well-defined data structures only(ish) - hard for Ruby
* Allocate memory, make ptr
* Pass ptr to str+length/size

# Ruby and pointers

* I don't want to do pointer math at all
* Could not figure out how do:
  * Wasm as library
* I spent some time on this, couldn't make it work in Ruby unfortunately

# Ruby and Wasm lib

* I need string params and return values
* Reverted to WASI for this
* We can parse the output, pass in fs dir
* Now let's try to solve a real problem with some Wasm in Ruby!

# What is Spin?

* My first entrypoint to Wasm
* Great docs about Ruby capabilities, references to relevant projects + docs
* "Serverless" - compose Wasms + run
* Test locally, no Kubernetes needed, no "linking" - works like controller/router

# What is Spin?

* "Serverless" framework
* Test locally
* Run on Fermyon Cloud

# What is Spin?

* "Serverless" framework
* Test locally
* (Run on Hippo Factory)
  * This is OSS Summit!

# What is Spin?

* "Serverless" framework
* Test locally
* (Run on Hippo Factory)
  * You're pulling our leg, right?

# What is Spin?

* Serverless framework
* Test locally
* (Run on Kubernetes!)
  * Did I mention I'm a Flux maintainer

# Why are we here?

* Hope to gain:
  * Testability
  * Reusability
  * Type safety between languages
* Capacity for polyglot teams to work together, benefit from specialization in many languages

# How about we dive in?

* I built some things in Wasm
  * Break misconceptions
  * Follow good examples
* How are we going to use it?
* Let's solve a real problem now

# Problem to explore

* GitHub Packages problem - DX needs to know how many downloads over time
* fluxcd/flagger/
  * [pkgs/container/flagger][]
  * GitHub does not expose this value on any API afaict, so we scrape some HTML and parse it!

[pkgs/container/flagger]: https://github.com/fluxcd/flagger/pkgs/container/flagger

# I built some things

* EKS cluster: Find on GitHub
  [kingdonb/eks-cluster][]
  * with Flux bootstrap (eksctl+flux 2.0.0-rc.2)

# I built some things

* Blog service: GitHub
  [kingdonb/taking-bartholo][]
* GitOps via Helm Controller
* Helm + Helmet library chart
  * At this point I understood pain of running Wasm+Kubernetes (not pain from Ruby... yet)

# I built some things

* I began to understand some things
  * Fermyon isn't using K8s or Helm
  * This would be v. hard without Flux (used Flux OCI to ship content separately from runtime, a novel application of Flux's OCI Artifacts!)

# I built more things

* Kubernetes operator: GitHub
  [kingdonb/stats-tracker-ghcr][]
  * Fetch from URL (in Ruby)
  * Write to file, pass in fs context
  * Parse HTML (in rust)
  * Return number as string (WASI!)

# Finally

* Kubernetes operator: GitHub
  [kingdonb/stats-tracker-ghcr][]
  * Parse number (back in Ruby)
  * Store the number we parsed out of scraped content in CRD status
  * (Come back and retrieve it later)

# Based on

* Kubernetes operator: (GitLab)
  [tobiaskuntzsch/kubernetes-operator][]
  * Wonderful example to build with Ruby
  * Register CRD, Register `upsert`
  * Reg. `delete` - manages Finalizers

# Based on (dependency)

* Kubeclient gem: GitHub
  [ManageIQ/kubeclient][]
  * Also easy to use
  * Server-side apply only (!)
  * (about SSA, Flux uses this too)
    * can account for admission controllers, wait for ready, ... lots of benefits here!

# This is the end

* of the Lightning talk - but today!
* We can dive into topics further
  * (before we do - I've more talks tomorrow)
    * Dev-Driven Automated Deployments Like a Cloud Native Pro (Thu 11:00am)
      * Juozas Gaigalas, Weaveworks (I'll be standing in)
    * Go/TypeScript: OpenGovCon (Thu 4:05pm)
      * with co-presenter Will C, Defense Unicorns

# ~~Operator isn't finished~~

* OK, still not finished, but it works now!
* Did it live on YouTube ([.com/@yebyen](https://youtube.com/live/hSZtVahbP-Q))
* 3 hours ago - JIT presenting FTW!
* I am very tired, I hope it doesn't show

# How is the code?

* Wrote the operator from e2e in 3h
* Code is there, a few things not working yet
* Only missing a bit... we'll tour the code!
* First Rust app - be gentle (it was fun!)

# Rust App

* Let's start with the Rust app, then work our way out
* We'll come back to see Taking Bartholomew for a Spin
* How is this deployed using FluxCD?

# Thank You

* Visit us for the rest of the week:
  [bit.ly/gitopscon2023](https://bit.ly/gitopscon2023)
* Find these slides:
  [kingdonb/cdcongitopscon2023-slides][]
  on GitHub

# Thank You

![](images/slidesqr.png "github.com/kingdonb/cdcongitopscon2023-slides"){:width='190' height='190'}

[kingdonb/eks-cluster]: https://github.com/kingdonb/eks-cluster
[kingdonb/taking-bartholo]: https://github.com/kingdonb/eks-cluster
[kingdonb/stats-tracker-ghcr]: https://github.com/kingdonb/eks-cluster
[tobiaskuntzsch/kubernetes-operator]: https://gitlab.com/tobiaskuntzsch/kubernetes-operator
[ManageIQ/kubeclient]: https://github.com/ManageIQ/kubeclient
[kingdonb/cdcongitopscon2023-slides]: https://github.com/kingdonb/cdcongitopscon2023-slides
