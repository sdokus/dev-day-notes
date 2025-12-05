# Tech Talks: How to Develop LLMs and RAG

## What is LLM and RAG?
LLM = "large language model"
RAG = Retrieval-Augmented Generation

## What makes up an LLM?
They are trained on general text (i.e. fed a bunch of text and books and publically available things on the internet)
Since it's a snapshot of the internet essentially, there is a knowledge cutoff from when the snapshot was taken

## What goes into an LLM call?
User Prompt = the current "chat" being sent from the user
System Prompt = the rules that have been given to the system to remember for every response

## RAG = "open book test"
OpenAI released ["Cookbooks" ](https://cookbook.openai.com/examples/fine-tuned_qa/ft_retrieval_augmented_generation_qdrant)
"Add a few shot" = give some examples to train the AI

## The answers are wrong, what should I tune?
https://arize.com/llm-evaluation/ and there was a chart in the slide deck too
You can use other LLMs to evaluate your LLM
