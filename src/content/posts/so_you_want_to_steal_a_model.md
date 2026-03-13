---
title: "So You want to steal a Model?"
published: 2022-02-27
draft: true
description: 'A breakdown of how much it costs and how difficult the most recent distillation attack against Anthropic was.'
tags: ['Anthropic', 'Claude', 'hacking']
---

## So You want to steal a Model?

Early this week, Anthropic released a [report](https://www.anthropic.com/news/detecting-and-preventing-distillation-attacks) about the latest distillation attack they detected against there models.  While they don't explictly go over the cost of performing the attacks, it does bring to light a glaring error with how we currently think of both AI policy in the US, and what it means for LLM vendors as an industry.  

### Model Distillation

Before going further, let's define what we mean by distillation in this space.  Model distillation is the process by which you train a smaller model on the outputs of a larger model.  Do this repeatedly over a long enough time period, and eventually the smaller model will perform roughly as well as the larger model, without increasing in size.  

Where this transitions from a technique to an attack in Antrhopic's case is that both they, OpenAI, Google, and XAI, all keep their models private.  When you buy access to their models, their API, and most of their revenue stream is designed around keeping said model private and unable to be easily duplicated or recreated.  