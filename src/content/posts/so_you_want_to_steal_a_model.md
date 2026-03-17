---
title: "So you want to steal a model?"
published: 2026-02-27
draft: false
description: 'A breakdown of how much it costs and how difficult the most recent distillation attack against Anthropic was.'
tags: ['Anthropic', 'Claude', 'hacking']
---

## So you want to steal a model?

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

Using these numbers, we get a total cost of the attack to be: $3,200,000.  $3.2 million dollars is not a lot of money for a company or nation state to spend on stealing a model that could potentially be worth billions of dollars.  This is especially true when you consider that the cost of training a model like Claude from scratch would be in the hundreds of millions of dollars, if not more.  

In a weird way, this is actually a problem for Anthropic and other cloud based model vendors.  Even if they double the price of their API, the cost of performing the attack would still be so cheap that it would still be worth it for a company or nation state to steal the model.  In a weird way, the attacker is actually the best customer they will every have because there is no price they won't pay for API access.  This means they can't use the classic Steam approch of making it easier to buy the game than to steal it, because there is no price they can set that would discourage stealing the model and not also cause them to lose customers.  

##### Indidual Breakdown

Antrhopic breaks down the total attack and lists several companies by name, so I thought it would be interesting to break down the cost of the attack for each company using the same formula as above.  This is not an exact science, as we don't know individual token usage or how many tokens were input vs output, but it should give us a good estimate of the cost of the attack for each company.  Here is the breakdown:

| Company Name | Number of Interactions | Estimated Cost of Attack |
|--------------|------------------------|-------------------------|
| DeepSeek    | 150,000              | $30,000                |
| Moonshot AI   | 3,400,000              | $680,000                |
| MiniMax | 13,000,000 | $2,600,000                |

### Conclusion

The cost of performing a distillation attack against a model like Claude is shockingly low, especially when you consider the potential value of the model.  This raises some serious questions about the current state of the LLM industry, and how we value these companies.  If the models these companies have are not unique and can be easily replicated, then we need to rethink how we regulate them, and how we value them as companies.  Model vendors need to start thinking about how they can detect and prevent these types of attacks, which will require more heavily analysis and monitoring of their API usage, response patterns, and user behavior.  This is not an easy problem to solve, but it is one that needs to be addressed if these companies want to continue to be successful in the long term.  

