---
layout: post
title: Tracking Safety - from AVs to the world of LLMs 
date: 2024-03-10 16:40:16
description: Learnings on safety and risk management from ADAS & AV industry, and an analysis of what's happening with LLMs 
tags: AI, Safety, LLMs, Preparedness
categories: AI 
---

## Managing Risk in deep-tech  

With time, we're seeing more and more startups and fast paced teams making their mark in the field of Deeptech- the likes of nuclear fission/fusion, space tech, biotech, autonomous vehicles etc. The horizontal mother to all these, is evolving to be the field of powerful AI models,which could influence the development of any of those other fields. 

Managing risk and ensuring safety is a vital need in this space of powerful technologies, where there is a non-zero probability of threat to human life, if the guardrails are not set properly. 

There are numerous examples in history we could look at , to learn how the risk was contained in those fields -  Airline industry, defence technology etc. but the development track of those were different from the software & AI development practices involved in the modern deep tech efforts. Being agile and build & fail fast is predominant in the culture of many software teams. A clash of this fast paced culture with the inherent safety principles one needs to have, is the challenging task at hand to today's deep-tech companies. 

## Learnings from AV and ADAS projects 

I've been fortunate to have worked on risk management problems of AI systems in the early years of AI being applied to a real world task - driving on public roads. 

For all the teams I have worked with over the years - be it the regulatory body NHTSA, the Safety teams of the German Automotive OEMs or the Risk teams of Insurance companies; even though the business objectives and timelines differed based on their respective roles in the industry, the common goal has been to come up with an efficient statistical and empirical approach to estimate and contain the risk of Autonomous Vehicle Systems. 

Whichever method one choses, what I realized over the years is - measuring risk and creating guidelines for AI and safety-critical systems, is a continuous process that extends even to the culture and development practices of the given organization. 

1. Safety should be inherently built within the design & build culture of every team of the org, not only as an isolated activity 
1. It is challenging to balance the activities of fast build vs cautious safety mindset of an team- this is where the mettle of the org is decided 
1. Ideally you’d want your core tech/product builders to contribute strongly to the safety framework, as they’ll have significant knowledge of the edge cases of what they have built. 
1. Use a sufficiently large scale of data to measure your safety metrics
1. Ensure a way of continously refreshing the datasets with real world deployments 
1. Synthetic/Simulated data guided by system experts is another key complement to real world data 


## Status of Safety Initiatives in the LLM world 

Similar to safety reports released by AV players back in the day, we have preparedness and responsibility reports and frameworks published by the AI orgs. 
- OpenAI Prepareness Framework (Beta) - A 27 page [Report](https://cdn.openai.com/openai-preparedness-framework-beta.pdf)  
  - Simplicity of their scorecard is good - it's easy to track, forecast and control the threats under various categories.But I also believe it will evolve both in the number of categories and the way risk thresholds are decided in each category. E.g. The inclusion of subject matter experts from the domains of CBRN, is going to be vital to improve the current risk assessment process. 

- Anthropic's RSP (Responsible Scaling Policy) - A 22 page [Report](https://www-cdn.anthropic.com/1adf000c8f675958c2ee23805d91aaade1cd4613/responsible-scaling-policy.pdf) 
  - Their AI Safety Levels (ASL) seem similar to the US government’s biosafety level (BSL) standards. They have classified a model’s potential for catastrophic risk into 5 Safety levels, with higher ASL levels requiring increasingly strict demonstrations of safety. 

Tooling Companies like Scale are coming up with safety evaluation benchmarks that could be widely adopted by anyone into the development of powerful AI models. They released a benchmark called [WMDP](https://scale.com/blog/measuring-mitigating-risk-wmdp) this March.


## A few teams to follow for updates on AI Safety 

- OpenAI Preparedness team 
- Anthropic's Safety team
- Scale's SEAL team 
- Center for Governance of AI (Oxford)
- Center for AI Safety (Safe.ai)
- U.S. AI Safety Institute Consortium (AISIC)

It is going to be both exciting and inspiring to see how today's leading AI teams will balance the act of safety and fast paced build, in the coming years.  