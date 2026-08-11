---
locale: en
translation_status: translated
translation_id: "posts/AI 味從哪來？LLM 為何逃不出資料的影子"
title: Where Does the AI Flavor Come From? Why LLMs Cannot Escape the Shadow of Data
slug: ai-taste-llm-data-shadow
published_at: '2026-03-18'
tags:
- Writings
- Research
description: Why do LLM outputs always have an "AI taste"? From input method predictions to recommendation algorithms, and now Large Language Models, they are fundamentally probabilistic association prediction computations. When models can only seek the most probable patterns from existing data, are novel things that have never appeared doomed to be ignored? I call this the "Curse of Correlation."
authors:
- Gbanyan
feature_image: ../assets/ai-taste-llm-data-shadow.jpg
---

Striking while the iron is hot, here is another long post discussing the capability limits of LLMs (actually, I'm just annoyed that a paper idea I had was done by someone else X).

Some have said that current LLMs feel like the shadow of humanity, while others say that LLM outputs seem to carry an "AI taste" unless specially tuned. Furthermore, exploring new research topics also seems to have some limitations?

## Starting from the Context of Early Digital Tools

Let's start from some contexts of earlier digital tools. In fact, many convenient applications that appear intelligent must begin with probability, statistics, correlation, and prediction. For example, input methods and candidate words are essentially predicting the next word the user will type.

Additionally, Spotify playlists, recommended video channels on YouTube, and social media posts collect numerous quantified features, feed them into models for probabilistic predictions of associations, and continuously reinforce training through the user's own feedback, thus increasingly converging on the user's preferences.

But this context introduces some potential problems. Have you ever thought about why echo chambers emerge so easily? Because this pattern of predicting associations tends to reinforce the more superficial, visible patterns. The less probable and numerically unlikely ones will be pushed further away by this system. Projecting this onto reality a bit more, it makes it harder to come into contact with groups that have different traits and surface preferences than you do—unless you explore more proactively.

## The Essence of LLMs: Predicting the Next Data Fragment

My abilities are relatively weak, so I cannot fully explain the principles from the underlying attention mechanism of LLMs, but the mechanism of LLMs can essentially be thought of as: training a model from all recorded data since human civilization began to predict the most likely next data fragment.

As for the strength of its predictive capabilities, how it aligns with human preferences, how to effectively utilize hardware resources, how to control the input data length during prediction so that it degrades as little as possible, and how the importance fluctuates—these depend on the tuning capabilities of different models. It even includes dividing the data processing pipeline into multiple steps, rather than having a single model output it all at once. Quantitative changes bring about qualitative changes, which is why current LLMs can provide answers so close to humans.

## The Curse of Correlation

But here is the problem: does the underlying complex probabilistic association prediction computation, while infinitely aligning with human outputs, also bring a certain degree of limitation? Are human creative associations and thoughts more discontinuous and less traceable than superficial probabilistic association computations? If LLMs just help us filter and find information based on the most probable and strongly correlated patterns in the data, is it easy to overlook novel things that have never been explored, rarely appear in human data, or have never appeared at all?

I call this phenomenon the "Curse of Correlation."

When New Phonetic (Bopomofo) or other predictive input methods emerged, the language used by humans actually underwent a filtering process, becoming more aligned with input method predictions for efficiency, with fewer complex textual variants, rare vocabulary, or newly coined words intended for creative atmospheres.

So, without carefully designed Prompts and prompt words integrating human thoughts, are LLM creations and outputs somewhat more prone to having an "AI taste," following the same logic as the common vocabulary and texts of input methods? Because, essentially, they are both just predicting the single most probable scenario given the current context across all existing data.

## The Shadow of Humanity

I believe this is also why LLMs are said to be like the shadow of humanity. Because any pattern or process that is too fixed and observable in the data might be sealed into the models in the future as computing resources increase and models develop. Conversely, you could also say, are most human groups actually just very predictable? (Gets hit)

However, what about things not in the data? In human history, many discoveries were strokes of genius or even happy accidents, but humans have the ability to cleverly achieve sudden enlightenment, connecting seemingly unrelated contexts to create new discoveries. Under the current architecture of strong correlational computation, do LLMs have the ability to replicate this?

## An Unfinished Paper Idea

Therefore, my original paper idea was: if I deliberately picked named entities and vocabulary that were very far apart and forced the LLM to output a connection or a reasonable explanation between them, how would the LLM actually react when there is almost no description in existing data?

Because as long as humans reach a certain level of intelligence, they can make up a reasonable story. But for LLMs, from low-end to high-end, you would see outputs in this scenario ranging from gibberish to severely hallucinatory connections, perfectly verifying the gap between LLMs and human capabilities. It's just that being conceptually far apart and almost unrelated is hard to define in computer text data—vectors? Unsearchable by search engines? So this experiment wasn't developed further, and then someone else did it.

## Where LLMs Are Strong and Weak

The article has gotten a bit long, so let's get back to the point. I do not believe that within a correlation-calculating model, you can force it to generate creative, rare topics that break away from existing data. Plainly speaking, what an LLM outputs cannot be random noise; it is data fragments with certain patterns.

So in current scientific research systems, LLMs are strong in that, given existing data and set conditions, they can continuously compute through programmatic loops to filter and screen similar ideas, research topics, and implementation methods. Our own exploration process, on the other hand, involves constantly swapping the named entity keywords in our professional knowledge, asking an LLM Agent to search or deduce the most reasonable path.

But an LLM will not proactively prompt you with novel topics that have weak surface correlations and huge differences in existing data; this is currently something humans must actively think of themselves. This is also why it is said that those who are better at asking questions are better able to use AI tools.

I believe that this fundamentally is the ability to constantly explore seemingly unrelated and unprompted different topics. Furthermore, I believe this step is one of the keys for AI research to conduct high-level decision-making or even Artificial General Intelligence; otherwise, the Curse of Correlation will continue to exist.
