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

Where this transitions from a technique to an attack in Antrhopic's case is that both they, OpenAI, Google, and XAI, all keep their models private.  When you buy access to their models, their API, and most of their revenue stream is designed around keeping said model private and unable to be easily duplicated or recreated.  By asking a wide varity of questions that stimulate a wide variety of responses, you can train a smaller model on the outputs of the larger model, and eventually have a model that performs just as well as the larger model, without needing direct access to the larger model.  This is why Anthropic is calling it an attack, because it is a direct attack on their business model, and the way they make money.  If you can steal their model, then you don't need to pay them for access to it anymore.

Distillation attacks do raise a weird truth about the current state of the LLM industry: so much of the value of these companies is in the data they have access to, and the models they have trained on that data.  If you can easily recreate the model, is there really any justification for the high evaulations many of these companies have?  All of our current policies and regulations are based on the idea that the models these companies have are unique and can't be easily replicated.  If that is not the case, then we need to rethink how we value these companies, and how we regulate them.  

### The Cost of Distillation

While Anthropic doesn't go into the cost of performing the attack, we can make some educated guesses based on the information they do provide.  While they don't list the exact interactions, they do provide how many interactions they flagged as being part of the attack, and how many interactions they had in total.  Based on this, we can estimate the cost of performing the attack, and how much it would cost to steal a model like Claude.  

#### Cost Formula

Anthropic's API is priced based on the number of tokens you use.  So to try and estimate the cost, we need to figure out how many tokens were used in the attack.  However, Anthropic only provides the number of interactions, not the number of tokens.  To get around this, we have to estimate the number of tokens per interaction.  A quick google search shows the average number of tokens per conversation can vary widely, with 4,000 to 8,000 tokens being a common range.  Given that Anthropic lists over 24,000 accounts possibly being involved, we can assume the attackers were trying to make all the interactions look like normal conversations.  To make the math easier, we'll assume every interaction uses the high range of the estimate, 8,000 tokens.  This is probaly an overestimate, but it should give us a good upper bound on the cost of performing the attack.  With that in mind, we can use the following formula to estimate the cost of performing the attack:

```
Cost = (Number of Interactions) * (Tokens per Interaction) * (Cost per Token)
```

Where:

- Cost per Token: We'll use Anthropic's most expensive model, Opus 4.6, which has a cost of $25 per million tokens, or $0.000025 per token.
- Tokens per Interaction: As mentioned above, we'll use 8,000 tokens per interaction.
- Number of Interactions: Anthropic lists 16 million interactions in total that were flagged as part of the attack.

Using these numbers, we get a total cost of the attack to be: $3,200,000.  