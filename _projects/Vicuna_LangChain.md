---
layout: page
title: Vicuna LangChain
description: Use the Vicuna and LangChain to build a local GPT
img: assets/img/Vicuna_LangChain/title.jpg
importance: 1
category: fun
---

## Motivation
Sometimes if you want some medical opinions from ChatGPT, it doesn't work at all because it is not allowed to give the user any medical help. But even if it gives users some medical information, users are usually not willing to believe in a generative AI model. After all, users do not know the information source of chatgpt, which may bring some health risks. We want to build a LLM system which can only extract information from given dataset so we will never face some terrible outliers. But because of medical data privacy, we couldn't use the OpenAI's language model or embedding tools. We need to build everything locally.

## Vicuna
We chose **Vicuna** (https://github.com/lm-sys/FastChat) as our local language model. It is an open-source chatbot trained by fine-tuning LLaMA on user-shared conversations collected from ShareGPT. Preliminary evaluation using GPT-4 as a judge shows Vicuna-13B achieves more than 90%* quality of OpenAI ChatGPT and Google Bard while outperforming other models like LLaMA and Stanford Alpaca in more than 90%* of cases.

## LangChain
**LangChain** (https://github.com/hwchase17/langchain) is an open-source package designed for better using the LLMs. 