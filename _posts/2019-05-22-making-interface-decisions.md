---
layout: post
title: "Making Interface Decisions"
alt_title:  "Robotman"
song: "Bannerman by Steve Taylor"
---

After last episode's dilemma, I decided to try and do something on the simple
side. So I started writing a super simple IRC bot. It takes some simple
commands, like ```!bands``` and responds with information about it. Soon after I
started to work on the commands, I started exploring how to test the commands
easily. After a quick stint with irssi again, it occured to me that I could just
as easily connect the bot to STDIN as well. So that's what I did.

I've rewritten the interface to be a single question-response type interface
that has multiple input sources. Right now I have IRC and STDIN as command
sources. I'm going to chase this rabbit hole a little bit and see if I can get
some basic inspection commands done as well as some other simple processes like
generating a new song and creating a link to it. The difficult part of that will
be the fact it'll be generated asynchronously and we'll have to respond much
later without blocking the rest of the process. In theory, that's pretty doable
since I'm using AnyEvent. In practice, when I'm running these long processes to
generate a band or a song, it may end up interfering with sending a message back
to these various frontends. It'll be a fun challenge in any case.
