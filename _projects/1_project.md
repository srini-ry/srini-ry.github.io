---
layout: page
title: LLM Resource List
description: Running List of useful resources/links in the current LLM landscape
img: assets/img/13.jpg
importance: 1
category: work
related_publications: false
---
## LLM Resources - Running List 

This is a working shortlist of resources I find useful for projects covering small models, cost and serving details etc. 


### Models for Coding

- [Ollama AI's Codebooga](https://ollama.ai/library/codebooga)
  - A high-performing code instruct model created by merging two existing code models (Phind-CodeLlama-34B, WizardCoder-Python-34B)
- [Starcoder](https://huggingface.co/blog/starcoder)
  - Trained on Github Licensed data, from 80+ programminh languages, commits, issues and Jupyter notebooks 


### Local, small models
 
Relevant links: 
- [Mistral 7b](https://www.xda-developers.com/mixtral-8x7b/)
  - [Getting started blog](https://www.pinecone.io/learn/mixtral-8x7b/)
  - Seems to be the best local and open source LLM model out there, so far. 
  - Useful for creating hybrid setups for AI Agents - where a small, local LLM is used for initial classification or PII removal and GPT4 in the backend for rest of the problem/task 
- Tiny llama 1B
- [Google Gemini Nano - AI Edge SDK](https://ai.google.dev/tutorials/android_aicore?_gl=1*1l85n5p*_up*MQ..&gclid=Cj0KCQiAz8GuBhCxARIsAOpzk8w5fgQzY0Sa74LIEnxN9PioMEULaVZ9MU3A7-Tjal6GFxpz0UyM-j4aAhV6EALw_wcB#benefits-on-device)
- Ollama
- [Nvidia's Local Chatbot](https://blogs.nvidia.com/blog/chat-with-rtx-available-now/)
- [bakllava](https://x.com/Karmedge/status/1727328990090998191?s=20) on local computer in real time to describe images streaming on webcam 


### Serving and Deployment

- [Lambdalabs](https://lambdalabs.com/lambda-stack-deep-learning-software) - Unified docker file and image for all DL softwares - cuda, pytorch etc. 
  - Works for servers, desktops and laptops. 
  - Single line install commands
  - Check for Jetson . 
- [Guidance for Output Generation](https://github.com/guidance-ai/guidance)
- Serving large number of users with small models
  - User posts: 
    - Setup is extremely complex having to deal with builds, CUDA, firmware, Triton and model compatibility issues etc.  
    - TensorRT-LLM has superior performance Example: https://github.com/NVIDIA/TensorRT-LLM/blob/main/docs/source/blogs/Falcon180B-H200.md
     - Combine it with the tensorrt_llm backend in [Triton Inference Server],(https://github.com/triton-inference-server/serve) 
     - Used by most big commercial providers on their backends - like Cloudflare, AWS, Perplexity, Databricks, Phind, etc.
     - 7b on low-end Nvidia TensorRT-capable hardware with this approach can handle "only" a couple of thousand users easily.
  - Source: [Reddit: Serving Small Models](https://www.reddit.com/r/LocalLLaMA/s/TwirASRY7M)
- gpt-auth.com 
 


### Inside the models  
- System instruction behind desktop version of  Chatgpt:  https://x.com/krishnanrohit/status/1755123169353236848?s=20
- https://github.com/karpathy/minbpe - encode token method
- Mental model on current limitations of GPT. [Is it just probability of next token or is it learning the python/the world?](https://www.linkedin.com/posts/drjimfan_i-see-some-vocal-objections-sora-is-not-ugcPost-7164315295774392320-VYoI?utm_source=share&utm_medium=member_android) 
- https://chsasank.com/llm-system-design.html 
- Long Context 
  - How LLMs get lost in the middle (when the context is long). They prefer outer edges - https://arxiv.org/pdf/2307.03172.pdf
  - LLMs with long context [LongLM](https://arxiv.org/abs/2401.01325)


### RAG 
- [Current Status of RAG](https://www.reddit.com/r/LocalLLaMA/comments/19crm8i/comment/kj1yy0y/?share_id=gGNCwzqeX7KJpGMhZo6Zw&utm_content=2&utm_medium=android_app&utm_name=androidcss&utm_source=share&utm_term=1), as of Jan 2024 

### Testing and Benchmarking 
- To test retreival capabilities for long context - https://github.com/gkamradt/LLMTest_NeedleInAHaystack



### Fine-Tuning 

- [Fine-Tuning Whisper for Low-Resource Languages](https://wandb.ai/parambharat/whisper_finetuning/reports/Fine-Tuning-Whisper-for-Low-Resource-Dravidian-Languages--VmlldzozMTYyNTg0) - Great Article on fine tuning process 
- Finetuning methods  
  - LoRA https://github.com/microsoft/LoRA 
    - LoRa is a parameter-efficient fine-tuning style for LLMs and diffusion models. It is ideal to run after an integer 8 quantization. LoRa can be combined with other methods within PEFT, such as prefix tuning.
  - PEFT https://github.com/huggingface/peft  	

 


### Hardware

- Explore [AI-Specific ASIC Options](https://www.reddit.com/r/LocalLLaMA/s/WOu0zCjQ1x)
- Cerebras.ai
- etched.ai
- Specs comparison
  - 4070 GPU = 235 TOPS @200W.
  - Jetson AGX = 275 TOPS @ 15-50W


### Inference Optimization 
- Learn about [Inference Optimization Techniques](https://deci.ai/blog/optimizing-openais-whisper-for-production-with-infery-ffm/)
- [LORA extract](https://www.reddit.com/r/LocalLLaMA/s/uIrk5MYGyJ) from any large model 

### Cost Management in AI Development

Practical tips for managing costs while using Assistant or GPT model APIs (From multiple sources)

- Don't have long chats, to cut down on token usage. Even though it's hosted, it still has to process the entire chat every time, and you pay for all those tokens. Start a chat over at the beginning of each new task.
- If you must have long chats, periodically generate a summary and start the chat over with the summary as the first message followed by the last few messages.
- Use code interpreter instead of knowledge retrieval for structured data, such as a CSV file. Only use knowledge retrieval when dealing with unstructured natural language (i.e. text files, pdfs, etc).
- When using code interpreter, you can sometimes save tokens if you hand write the code it needs. For complicated data, you can have it use sqlite3 as it allows you to write very complex queries with very few tokens.
- Train GPT-3.5 (or GPT-4 Turbo) using GPT-4. Create some examples using GPT-4 and then paste that chat into a GPT-3.5 (or GPT-4 Turbo) chat. Research "shot prompting". When done well, this results in a GPT-3.75
- Experiment with various prompt/chat techniques while actively watching your [usage](https://platform.openai.com/account/usage). (Keep in mind it can be delayed a few minutes.)
- Limit to number of tools(functions) and how to scale https://community.openai.com/t/limit-on-the-number-of-functions-definitions-for-assistant/537992/2

Costs of LLM inferencing
- https://cursor.sh/blog/llama-inference - Llama2 is cheaper for prompt heavy tasks like classification, costlier than 3.5 for competition tokens.
- https://tokentally.streamlit.app/
- https://blog.eleuther.ai/transformer-math/ 
- Batch 1 mode - llama inference makes sense - can do on smaller edge units also https://finbarr.ca/how-is-llama-cpp-possible/
- https://twitter.com/karpathy/status/1691571869051445433?t=3bp70Zz0DaBVO64KKlnyaw&s=19
- https://github.com/chsasank/device-benchmarks/blob/main/llama_bench.sh - bench's


### Use cases for both smaller and general LLMs

- Interactiveness in every face of product - generate sample followup questions against a certain component of your UI - be it a kpi metric, data dashboard, blog etc. base it on the user cache for more personalization.. . Perplexity, LinkedIn is already dng it. You can imagine this in every product UI where personalizatiok drives more interaction and there by positive user engagement

### Agent building 
- Openai assistant : Best so far 
- Langchain agent - ReAct, Mrkl etc. frameworks. Observed mediocre performance 
- AutoGPT 
- AgentGPT 
- Geminipro + vertexai - tool calling is still upcoming https://cloud.google.com/dialogflow/vertex/docs/quick/create-application
- Does Claude have one? 
 
 ### Meeting Tools 
 - https://www.usebubbles.com/ 


### Automotive related LLM applications 
- Cerence - callm. Rag on vehicle specific data, voice also. Sold to NA OEM and EU OEM.
- Baidu Ernie bot
- Inrix compass - on traffic data
- IBM eam

### Blogs 
- https://www.jasonwei.net/thoughts - AI researcher at Openai