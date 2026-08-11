---
locale: en
translation_status: translated
translation_id: "posts/Codex Windows 版上線，但問題不只是工具"
title: Codex for Windows Launched, but the Problem Isn't Just the Tool
slug: codex-windows-beyond-tools
published_at: '2026-03-17'
tags:
- Writings - 創作
- Software - 軟體
- Research - 研究
description: OpenAI has released Codex for Windows, but for AI tools to truly land in the hands of ordinary people, structural issues like authorization mechanisms, system environment differences, and privacy trust might deserve more attention than the tools themselves.
authors:
- Gbanyan
feature_image: ../assets/codex-windows-beyond-tools.jpg
---

OpenAI (the parent company of ChatGPT) has just released the Codex desktop application for Windows, which can be found in the Microsoft Store.

Based on the equalization of knowledge, everyone can consider giving it a try. But what I want to share might be more of some observations and sharing regarding structural issues. Can it be considered popular science? Some of it might also be a layman's little murmur.

## From Q&A to Taking Action: The Next Step for AI Assistants

For models like GPT, Gemini, and Claude, the direction they need to take to evolve from information-answering aids into something more useful and helpful to everyone is to actually get things done for you.

However, digital systems might be much closer to the messy complexity of real life than people imagine.

## The Metaphor of a New Employee

For example, suppose a new employee wants to start working at a shop you own. How do you assess their capabilities?

Looking at a resume is a common practice, as is a probationary period, but these are built on the cognition that, given basic human operational capabilities, even if there are things they cannot do in the shop, it won't cause a disaster. For instance, if they don't know how to operate the coffee machine, they will ask proactively or check the manual. If they need to find a specific item and aren't familiar with the shop layout, they might search one by one, and if they really can't find it, they will politely ask the boss when they are not busy.

This threshold of cognition and caution rises with the professional degree of the industry and the economic or time costs involved. To put it plainly, the higher the risk of something going wrong, the less you trust a new employee, especially when you don't fully understand their capabilities yet.

## The Dilemma of Authorization: Decision Fatigue vs. Risk

To human cognition, digital systems, at least in my personal feeling, are only flatter, more ephemeral, and less concrete than the physical space of a company. Therefore, for this cognitive threshold, some people will be more cautious and fearful, while others won't care as much.

Frontline AI companies, in order to lower this cognitive threshold and the risk of accidents, have constantly been thinking about authorization, sandboxes, and defense mechanisms. But these mechanisms in digital systems will definitely not be human enough; after all, defining which actions require authorization and which do not is also a very complex issue in the real world.

Imagine if that newly hired employee wanted to pick up a manual on the desk or grab a jar of salt from the condiment area to add some, and they had to get your confirmation for every single step—accumulated over time, this would absolutely lead to decision fatigue. You would feel this employee is too tedious, timid, and afraid of taking responsibility.

Therefore, many people choose to bypass the authorization mechanism entirely, fully delegating all operational rights to these Agents released by the companies. By doing so, the efficiency and output of some people soar to incredible heights; but for others, accidents happen—files are completely deleted, sensitive information left completely exposed, and so on.

This further involves some architectures, habits, and even values of digital system structures.

## Differences in Environments: A Tidy Shop vs. a Department Store's Appliance Section

Let's swap roles today; let's try being this new employee.

Right now, you are standing in a shop where cabinets and equipment are neatly arranged, so strict that every device, like the coffee machine, refrigerator, and oven, has an operating manual and a safety rulebook hanging on it. Don't you feel a bit more confident to explore and complete tasks on your own? Because you have a clear understanding of what will happen at each step, or what prompts will appear for erroneous steps.

Then let's make the environment more complex... imagine the appliance section of a department store. You walk in and see the designs of many different new appliances. Even though they look shiny and appealing (I must admit there was a time I loved browsing and playing around with them...), the problem arises: can you guarantee that you know how to operate every device at first glance? For some buttons, when you press them, there is a sense of fear and uncertainty.

In modern visual-interface system environments, it is more like the latter scenario. Each service, manufacturer, and interface design on Windows has its own habits, considerations, and design reasons. But the problem is, through just the initial visual interaction, even the smartest people might need to reason and deduce a bit, let alone ordinary users?

By the same token, for these model assistants, this is not the most efficient mode of functional cognitive exchange.

## The Inherent Advantages of Unix-like Systems

Unix-like systems (macOS, Linux...) and pure text Command Line Interfaces (CLI), surprisingly, have an inherent advantage in this regard. They are more like the aforementioned shop where everything is neatly organized.

This relates to the fact that many Unix-like tools and commands have actually been developed over decades (probably more than twenty years?). Well-designed CLI text tools, just like clearly documented manuals and procedural rules, show what each parameter means, and if a step is done wrong, there will be as clear an error message as possible.

The Windows system itself has a lot of baggage in its GUI, while its text command system has undergone generational changes, with the completeness and operability of the previous generation not matching that of Unix-like systems.

There is a very clear trend with tools released by OpenAI and Claude: they are often released first on macOS, or even operate best solely on macOS. Besides macOS natively embedding these complete Unix tools, macOS actually has comprehensive AppleScript that allows the manipulation of GUI interfaces via text commands. That means ordinary operations in Reminders and Calendar can actually be added, deleted, or modified via text commands.

Returning to the cognition of the employee, this means that in this environment, they have a very clear understanding of what will happen at each step, or what items can be manipulated. But in Windows and other environments, they face something akin to a blob of chaos. Many things have to be explored on their own, and even after taking action, what happens is very opaque (software on Windows is developed independently by various companies, and many processes are essentially black boxes, meaning information is not disclosed). The cost of cognitive reasoning is extremely high, and many employees might just give up halfway through exploration.

## Solutions from AI Companies

Back to these AI companies themselves, their perspective is hoping more people can use the tools they release as employees. But how can these problems be solved? It's impossible to tell everyone to just use macOS, right? (Though a recent wave really did drive up Mac mini sales...)

To lower the authorization friction mentioned earlier and address this problem, I currently see a few directions for solutions:

### 1. Building Isolated Environments

Whether it is advanced users doing it themselves or these AI companies providing it. Taking ChatGPT's desktop application as an example, you can notice that its Agent mode establishes an isolated environment and then executes programmatic commands, so whatever happens inside won't affect the outside. At the same time, many tools inherently have a sandbox mode. Additionally, some advanced users, when utilizing tools provided by these AI companies, will build their own isolated environments, such as restricting read/write directories or setting up virtual machines.

### 2. Brute-Forcing via Visual Recognition and Reasoning

That is, directly taking screenshots or acquiring the positions of operational elements on a web interface to perform actions. In fact, if you are not worried about privacy data issues at all, they have actually realized handing over full control of the phone to cloud AI in China. It can help you send messages, automatically search for information on the internet, and automatically filter necessary information on social media, all fully automated.

But then this leads to another extremely complex issue: where is the boundary of data authorization interaction and privacy?

## The Problem of Identity Verification and Trust

Let's change roles again. If today you are an ordinary citizen going into a government agency to handle administrative affairs, how does the government agency verify that you are indeed the citizen in question? The common verification procedure involves ID documents and photo recognition.

But in digital systems, how can this procedure be implemented? It's impossible to just recite your Gmail password and gain direct passage, right? Would you feel safe if every tool could operate your email? Not to mention that passwords and ID numbers leaking on the internet is already a common occurrence.

Therefore, the authorization and authentication of different data access alone is a huge obstacle for these AI tool assistants.

Or stack the roles: if today an employee of your company goes to the Ministry of Economic Affairs to apply for a business alteration, how do they verify that this employee truly represents you?

Let's be a bit conspiratorial: it's not impossible for outsiders to hijack this employee, make them steal your company's certification documents, and forge your signature. So what about current Agent proxy tools? In the digital system, they don't even have emotions, expressions, or other distress signals for you to judge authenticity.

This is also why, in a situation where AI tools are expected to be smarter, information security policies are also taken more seriously and sensitively.

macOS has an inherent advantage in security: every type of operational permission, just like you going to a government department to apply for reading or writing certain personal data, has a complete process and restriction. Windows actually has this too, and it can be adjusted to be very strict, but by default, it is not as strict and organized as macOS. Thus, this is also a factor in why these AI tools are more suitable for operating on the macOS system.

## Why AI Tools Have Not Truly Landed in the Hands of Ordinary People

This article has unknowingly become very long; let's wrap it up.

If you sincerely want to make good use of this AI employee, synthesizing the above factors, we find there are many friction factors. This is also why some people are already flying high with it, but it hasn't yet smoothly landed in the hands of ordinary people.

### 1. Lack of Direct Cognition of What AI Tools Can Do

With newly hired human employees, no matter what, there is a basic reality framework; you can anticipate what they will and will not do. However, for AI tools, most people's cognition remains at Q&A and information gathering. When it involves data alteration and modification, they cannot confidently hand it directly to them.

Additionally, AI tools do not have a tacit understanding of interacting with you like real people do. Part of this tacit understanding is that they will proactively and gradually adjust until you can directly assess the boundaries of their capabilities. AI tools will only wait for you to issue commands and prompt you on what else can be done.

At this point, engineers with programming and system operation knowledge are the best demographic to exert this capability, because the things engineers know that programs and text commands can achieve are the partial upper limit of AI tools. Meanwhile, the more powerful the model, the better it is at self-orchestrating the planning sequence and execution steps of these programs, which means it can better translate your ambiguous commands into concrete procedural steps.

### 2. Lack of Background Knowledge on How to Correctly Lower Friction

To bypass restrictions and correctly unleash AI tools, one must establish complete data boundaries or prepare relevant protection and backup measures. However, these abilities are primarily embodied by engineers familiar with digital systems.

You want ordinary people to prepare sandboxes and isolated environments? You want them to understand regular backups? You throw a bunch of jargon like git, docker, VM, WSL... I see most people getting dizzy right away. Even the author hesitated here, wondering if writing about Unix earlier was already too much.

Furthermore, the friction of digital authorization itself is an obstacle. Under increasingly strict information security precautions, if I want to allow AI tools to operate my digital assets scattered across different cloud services, such as Gmail, Google Calendar, or other services, just exploring whether the access interface has a complete authentication mechanism is a cost in time and energy, much like those appliances lined up in a department store.

### 3. Insufficient Control over Personal Privacy Data, or Trust Issues with AI Service Providers

Basically, when you start using AI tools to process these documents, you have to accept that the information contained within will absolutely be uploaded to cloud servers and might be processed and utilized by the companies. For instance, my ID photos or my bank account plain text, as long as I tell it to organize them, will definitely be uploaded.

When you have even the slightest bit of unease, yet cannot anonymize (de-identify) your own data, you won't be willing to use AI tools. This is also why there is a faction hoping to develop local AI.

## Returning to Codex for Windows

Returning to the beginning of the article, although the Windows version of the Codex tool has been released, and I encourage everyone to explore it, rival Claude probably already has similar tools.

At the same time, my tone isn't very enthusiastic. Why?

Because of the problems discussed above, and the inherent aptitude of Windows. I even saw that this Codex desktop tool runs via the WSL tool, which means setting up an isolated Linux virtual machine within Windows. But based on my understanding of Windows running into problems every other day (the author hasn't used Windows for serious business in a long time; the last time was using a Citizen Digital Certificate), I feel its usage rate will definitely not reach the levels on macOS (don't come to me if things go wrong, just passing the buck X).

So this piece is probably more like a layman's popular science murmur article.
