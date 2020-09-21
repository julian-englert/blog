+++
author = "Julian Englert"
title = "How to Use Daily Notes in Obsidian"
date = "2020-09-21"
description = "Process information, plan & execute tasks during the day, and keep track of content and recommendations"
tags = [
    "guide",
    "Obsidian"
    "note taking"
    "productivity",
]
+++


[Obsidian](https://obsidian.md) is a powerful knowledge management tool that allows you to take notes in a networked fashion. 

The ability to form `[[connections]]` between them mimics the way ideas are captured in your brain, with the distinction that Obsidian never forgets: Built on top of a local folder of Markdown files, it is the perfect tool to construct a "second brain".

In this series I'll show some of the workflows I've found out to be working very well using Obsidian.

Here: **Daily notes with capture note**

<!--more-->


## Purpose
- process incoming information (thoughts, ideas, recommendations)
- write down tasks for the day and hold yourself accountable to them
- keep track of content you consume and serve as springboard for notes taken on podcasts, articles, etc

## Header

On the top of my daily notes you can see a section with links to yesterday's and tomorrow's note. This allows me to quickly navigate between daily notes to revisit them or to move tasks from one day to the next.

![](/obsidian_daily_notes/header_template.png)

It also has a link to my **capture note** which I use to note down incoming information that I don't have the time to properly process in that moment. 

This could be thoughts I have but that are not fleshed out enough to constitute an actual task; little reminders that I revisit later; or recommendations / prompts from other people.  

![](/obsidian_daily_notes/capture_desktop.png)

Using one of the various Markdown editors for iOS, I can edit all my notes on mobile too[^icloud]. 

In practice though, I mostly only use my capture note to write down things on the go and process it later on desktop. 

![](/obsidian_daily_notes/capture_mobile.png)

The Markdown for this header template can just be copied from one daily note to another and adjusted for each day or you can use a script to paste it with a shortcut of your choice (here with [Autohokey](https://autohotkey.com/)[^autohotkey])

```md
<< Yesterday `[[link to yesterday's daily note]]` | `[[link to tomorrows's daily note]]` Tomorrow >>


`[[link to capture note]]`

---

your notes

```

## Daily reading notes

In this section, I create notes for the articles I read during the day. 

Each note has some basic metadata with author information, date of publishing and reading, link and tags, to be able to organize my collection of notes via tags and MOCs (*maps of concepts*).

![](/obsidian_daily_notes/daily_reading_notes.png)

## Daily To Dos

Below, I write down my tasks for the day and keep track of things I'm doing (writing emails, planning things, writing or documenting code, talking to people etc.). 

Markdown allows you to create checkbox lists with nested items so finished tasks can simply be crossed out.

For meetings, I create a note with discussion topics or minutes directly from the daily note.
![](/obsidian_daily_notes/daily_to_dos.png)

Unfinished tasks I copypaste to tomorrow's daily note. There, after doing my daily planning and prioritization on the next day I either pick them up or discard them.  

![](/obsidian_daily_notes/next_day.png)

[^icloud]: this requires using iCloud as directory for the Obsidian Vault 

[^autohotkey]:
	```ahk
	; Syntax
	; ^ = CTRL
	; ! = ALT
	; + = SHIFT
	; # = WIN
	; :: = run when pressed keys together

	^+d::
		yesterday := a_now
		yesterday += -1, days

		tomorrow := a_now
		tomorrow += 1, days

		FormatTime, tomorrow, %tomorrow%, yyyy-MM-dd
		FormatTime, yesterday, %yesterday%, yyyy-MM-dd

		SendInput, << Yesterday **[[Daily notes/%yesterday% | %yesterday%]]**{space}|{space}**[[Daily notes/%tomorrow% | %tomorrow%]]** Tomorrow >> 
		Send, {Enter}
		Send, {Enter}
		SendInput, **[[000 Inbox]]**
		Send, {Enter}
		Send, {Enter}---
		Send, {Enter}
	Return

	```

