---
title: How (NOT) to build with AI
url: /its-a-whole-new-world
category: Development
tags:
  - AI
  - Career
  - Engineering
date: 2026-05-17
---
So, I missed my weekly update.  I know, I know. I’m already hearing the collective sigh of my zero subscribers, but I broke my one rule: [*ship something, anything, every week*](/blog/learning-publicly/).

It happened because I fell for the classic blunder. No, not a land war in Asia. I said the cursed words: <span style ="color: #b392f0">"I can do this in a weekend"</span>

It was supposed to be simple. A CLI, some SQLite, and a dash of LLM magic. I’d have it done by Sunday brunch. By Tuesday, I’d be the main character of a viral Twitter thread. I was going to turn my digital graveyard of bookmarks into Doompile, the ultimate AI study planner, with a super learning loop of  
	`ingest->extract->organise->plan->track->build` 
that would propel me to the peaks of productivity.

Instead, after two weeks of fucking around, I have a repo that is 80% boilerplate and a scope currently orbiting Saturn.

But I learned (tbh, re-learnt) a lot about how to build with AI and crucially how **NOT** to build with AI.  So, in the long tradition espoused by all my idols, I'm shipping a blog post instead.

## Embrace the Fog (But Don't Inhale)

> "You now have soma. We call it Claude Code... a warm, pleasant fog where every problem dissolves. Stuck on a bug? Soma. Need to scaffold a new service? Soma. A gramme is always better than a damn." - A Brave New World, if Gary Marcus wrote it....probably

Jokes aside, the paradigm has shifted, <span style ="color: #b392f0">**it really is a new world**</span>. Doesn't matter how many 9s of reliability GitHub loses or how many times us-east-1 faces a vibe-coded outage, this is the new baseline. We have to adapt, so we might as well learn some new rules. 
### 1. A single thread is a bottleneck

You aren't using this tech if you're working sequentially. You have to get comfortable keeping multiple running threads in your head. Frontend, backend, infrastructure, you should be spinning them up simultaneously and switching between them often. It feels really unintuitive when you start but eventually you just have to get adjusted to ADD (ADHD Driven Development).
### 2. It's all just vibes, man

If you're multi-threading at that speed, you can't track every detail. This is especially terrifying for veterans who have spent years building muscle memory around good coding practices. <span style ="color: #b392f0">You have to unlearn the instinct to own every single line of code. It doesn't scale anymore</span>. You have to make peace with the unknown, embrace the foggy nature of coding from here onwards (but not completely, as we'll see in a minute)

## Meet the new boss, same as the old boss 

Yeah so, despite what I was literally just saying about it being a whole new world, turns out, the more things change the more they stay the same and in fact, <span style ="color: #b392f0">much of traditional boomer engineering wisdom is more relevant than ever now</span>

1. **Define your minimum viable intent**

	![Apple Pie](/assets/images/apple_pie.jpg)
   AI is the ultimate yes-man. Give it a vague prompt, and it will bloat your scope until you're trying to build the universe from scratch.
   In my study planner experiment, I asked my agent to parse some bookmarks. Instead, it went rogue and built a data ingestion pipeline with OCR, entity disambiguation, and a custom graph search on top of SQLite. I had no idea if it actually worked, and when it inevitably broke, I couldn't fix it.

   <span style ="color: #b392f0">If you don't enforce a ruthlessly tight scope, the AI will build you a cathedral when you just needed a shed</span>.
   (Side note my personal conspiracy theory is the labs are deliberately training the models to always generate more tokens so they can bill you more, I'm onto you Dario ಠ_ಠ)

2. **Architecture is the Only Thing You Actually Own**

   This is the flip side of vibe-coding. Because you're delegating the micro-implementation to the clankers, the macro-design is all yours. You must have total clarity from 10,000 feet up. Remember, if the AI is the Co-Pilot, **you are the pilot** and you need to have

   - **Strict boundaries**: Clean API surfaces, abstracted business logic layers, strictly defined data ownership, all validated by the developer.
   - **Structured telemetry**: Logs, logs, and more logs. Structured and queryable, you need to be able to audit exactly what your agents are doing when they decide to rewrite your auth logic at 2 AM.
   - **Data-centric design**: Your data model is the core. If you get it wrong, the rest of the application will spend its entire life apologizing for it.
   - **Resilient by default**: Do not try to build a perfect system. You will fail and so will your app. Build one that expects failure, handles them gracefully and heals itself.

3. **Diffusion Models > Auto-regressive Models**

   Diffusion models work by iteratively denoising a machine, over and over, gradually bringing it closer and closer to the desired result. Autoregressive models by contrast, generate the entire output, from left to right, in a single pass. Which, oddly enough, reminds me of a common term people have recently started using, "one-shotting".

   We love the magic trick of the "one-shot", giving the AI a massive spec and watching it spit out an entire app left-to-right. It feels amazing, it's like a drug, in fact, it IS a drug. And just like a drug, you come down from the high three hours later (allegedly 🌚 )

   Then you're staring at an impenetrable wall of regex that supposedly parses HTML, and you want to cry. When the inevitable hallucination happens deeply nested in that one-shot code, you won't know where it broke or why.

   Resist the instinct to one-shot things, you are just reinventing waterfall from first principles. Act like a diffusion model, not an auto-regressive one. <span style ="color: #b392f0">Build, validate, refactor, iterate.</span> Denoise the code step-by-step.

	![Cato](/assets/images/cato.jpeg)

4. **An exploding ship, is technically the fastest ...**

   One of Meta's core values used to be "Move Fast, Break Things". At some point we decided to drop the "Break Things", just "Move Fast", it was cleaner. But it seems like it's making a bit of comeback in recent days .....
	   
	![Move_fast](/assets/images/gotta_go_fast.jpg)

   The thing is, this hyper fixation on speed we've had as an industry, had an implicit requirement alongside speed all these years. **Feedback!**
   
   Speed paired with accurate, rich feedback signals is how SpaceX catches descending rockets with giant metal chopsticks. Speed with inaccurate feedback (or worse, no feedback at all!) is the Mariner 1 launch in 1962. A single missing over bar in a guidance equation caused the rocket to misinterpret its velocity and fishtail so violently it had to be blown up 293 seconds after liftoff.
   
   <span style ="color: #b392f0">Speed is a liability if your feedback loop is slower than your execution</span>. You shouldn't fly faster than your "guidance system" (validating the functionality and performance) can course-correct. This is especially true with AI since all models seem to have a repeated tendency to get tunnel visioned and never course correcting (He's just like me fr fr). So, have a tight, accurate feedback loop in all your development workflows

5. **Tests, types and tabs**

   The AI doesn't have a soul, so it will be yours being judged for the 3,000-line utils.ts slop. Just because you can't check every single line of code doesn't mean there's no option but to let it rot.

   Use strict types to enforce safety boundaries between agent tasks. Run your linters. Have comprehensive unit tests, even if the AI writes them, you need to know exactly what functionality they're testing.

   Cleanliness is next to godliness, so keep your damn codebase clean.

## Tactical hygiene for the new age

You can't just raw-dog a frontier model and expect production-ready code. Here's some practical advice I've learnt at work as well as in my own personal tinkering

1. **Beware of context poisoning.**
	Keep track of exactly what's in your agent's session. Unwanted ideas sneak in and derail the whole train. Especially when brainstorming, stay neutral. Don't lead the witness, let the model form an opinion first, then argue with it. 
2. **Checkpointing is crucial.**
	You need a record of what changed, why it changed, and what's left to do, etc. Keep this in a format both you and the clanker can read, markdown files in source control work just fine. 
3. **Stop paying Opus to write tests.**
	Frontier models like Claude Opus or GPT-5.5 are brilliant for complex reasoning. They are also incredibly expensive. Use models slightly behind the frontier (like Kimi or Deepseek) for defined coding tasks. Use free, fast models like Minimax M2.5 for writing docs or unit tests. Match the model to the target.
4. **Learn the new primitives.**
	The IDE is changing. You need to understand the new building blocks. This is your new debugger. Learn how to set them up
	- AI web search tools
	- Retrieval pipelines
	- Context and memory management
	- Skills, MCPs and tool-calling
	- Change viewers, lightweight editors, Git hacks to enable multi agent coding, etc.
5. **Pick a stack and move.**
	Tool fatigue used to be for JavaScript frameworks and now it's models, agents, and prompts. Stop agonizing over the "perfect stack." Pick one and start shipping. Note the friction points, and only then look for a tool to fix them. 
	My current terminal-obsessed setup:
	- OpenCode: For switching models and agentic flows + exa web search integration.
	- OpenSpec: For tracking progress and checkpointing. 
	- OpenClaw style memory: One active memory file + daily archives.
	- Hunk: For viewing changes in the terminal.
	- Minimal nvim: Just syntax highlighting and fuzzy search.

## What's next?
I'm moving into two iterations of manual learning. I'm going to pick a topic, build a plan, and log the progress right here. 
There are two goals. 
- First, validate the core loop for my study planner to ensure it's actually ergonomic for self-guided learning
- Second, extract the high-friction, repetitive parts and automate them with a proper agentic flow. 
We’ve spent enough time talking about the tools. It’s time to see if the loop actually works.
