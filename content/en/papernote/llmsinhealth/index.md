---
title: "Opportunities and Challenges for LLMs in Biomedicine and Health"
date: 2025-08-27
draft: false
tags: ["computer_science", "llms", "biomedical", "health"]
categories: ["AI in Healthcare"]
summary: "Notes on the paper 'Opportunities and challenges for ChatGPT and large language models in biomedicine and health'"
---

## Abstract
Examine the application of LLMs in biomedicine and health like information retrieval, question answering, medical text summarization.  
Find a significant advance in text generation.  
But LLMs haven't evoluted in the field of biomedical → more risk (uncorrected info, privacy and legal, ...).  
Give an overview for researcher.  

- This is an overall paper → not deep into the field.

---

## Notes

### Overview
- There is a few biomed specific have been developed with biomed data
- Recent models can do vary task but need a lot of data for fine-tuning the model
  - More complexity to model development and deployment
- Large decoder-only LMs can perform unseen task after less-shot prompting (p.2)
- LLMs can generate unhealthy contents due the noise of the input data (p.3) → important to make LLMs generate helpful content
  - There is a design that make LLMs generate non toxic content along with human feedback (p.4) → Alignment tuning
- Fine tuning will become inefficient and costly when the size of the model increase 
  - Prompt engineer can take advantage of the learning ability of LLMs
  - Can tuning the model with nature language to return expected output + improve the performance (p.5) → Check fig1
- There is a branch called biomedical NLP
  - Model tuning by using style of US Medical Licensing Exam → evaluate the performance (idk) → approach level of human expert in 6 months → through different strategies
    - Pre training from scratch (he) → create a special LM for biomed with initialized parameter from biomed data base
    - Pre train from checkpoints → check again
    - Fine tuning with specific data → used frequently to adapt with smaller LMs for specific task
    - Fine tuning with another strategies like instruction tuning or RLHF fine-tuning
    - and a lot more
- Model can have some benefit if it trained by biomed data but it will be costly → LMs will be larger nowadays
  - Applying the technique can reduce the cost
  - Applied in combination

---

### Application of LLMs in Biomed and Health

#### Information retrieval
- Cannot use LLMs as search engine at the time of the paper because it makes up wrong information
- LLMs is good at summarizing information, search engine like Google use AI to summarize the search result but not guarantee error free
- Can use LLMs to make better queries → better search result

#### Question Answering
- Definition: answer automatically given questions
- Used to assist decision making
- Use retrieval augmentation to reduce hallucination, still need a system for evaluation
  - More than 1 way to reduce hallucination

#### Text summarization
- Important application of NLP
- Significant application: 
  - Radiology report summarization
  - Clinical note summarization

#### Information extraction
- Extract specific information from unstructured text into a structured format with 2 most common studies
  - Named entity recognition: recognizing biological and clinical entities
  - Relation extraction: extract relation between entities between text

#### Medical education
- Good area to develop
- Already applied in Khan Academy, not related to health care though
- Still need to develop

#### Other applications
- Coreference resolution: finding all mentions that refer to the same entities in a text
- Text classification

---

### Limitation and risk
- **Hallucination**
  - Produce fake contents
- **Fairness and bias**
  - LMs learn from historical data → can lead to bias
  - Proof that ChatGPT has social bias in answers → not health related
- **Privacy**
  - Might leak personal information → what can it do with biomed data
- **Legal and ethical**
  - (hihi)
- **Open source and close source LLMs**
  - Open source:
    - Pros: easy to adapt into specific tasks
    - Cons: depend on community support
  - Closed source:
    - Pros: more dedicated support
    - Cons: hard to customize

---

### Discussion and conclusion
- Some branch of biomed LLMs already develop
- LLMs achieved new state of performance art such as QA
- Promising

---

## Comments
- Prompt is a real job
- A lot of LLMs was made for Biomed tasks
- QA tasks is like another way to retrieve information → text summary of LLMs do a very good job
- OMG hallucination huhuhuhu
- Good idea retrieval augmentation: use the advance of LLMs

---

## Question
- What kind of data use to train the LLMs model?

---

## New Terms
- Encoder
- Decoder
- Zero-shot prompting
- Alignment tuning
- Instruction fine-tuning
- Hallucination
- Retrieval augmentation

---

## Figures and Tables

{{< figure src="/images/llm_fig1.png" title="Figure 1" >}}

{{< figure src="/images/llm_fig2.png" title="Figure 2: X = Name of LLMs, Y = Accuracy of the return information" >}}

**Table 2**
- Compare the models in each task (test database)
  - Learning: the way people tuning the model → give instruction for the model
  - The rest is the test database
- Numbers: The accuracy of informations
