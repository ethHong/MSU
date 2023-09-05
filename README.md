# MSU
MSU (Mathematical Solution Understanding) of LLM Evaluation
---
## Introduction
* This repository contains code to evaluate MSU score (Mathematical Solution Understanding) of LLM models.
* Dataset: https://github.com/hendrycks/math (Hendrycks et al, 2021)

## How to use
* Please set up requirements using: **pipenv install**
* This project utilize [OpenAI APIs](https://openai.com/blog/openai-api). Please create **api_key.txt** file and put your own API key.
* Run codes in **MSU_scoring.py** to go through mathe solution creation, and evaluation of each models. You can change **gpt**, and **extract_notion** function defined in p**rompting.py**, if you are trying to evaluate other LLM models of your own. 

## Formulation of MSU

1. **Problem and Solution Definitions from dataset:** Begin with a problem set defined as:
   
   $$X = (x_1, x_2, \ldots, x_n)$$
   For each problem, corresponding human-generated solutions are represented as:
   $$S_h = (s_{h_1}, s_{h_2}, \ldots, s_{h_n})$$

2.  **Solution generation using LLMs:** Produce LLM generated solution \(S_l\) for each problem. This set is derived through prompt engineering, utilizing various LLMs:
   $$S_l = LLM(prompt_{solving}, X) = (s_{l_1}, s_{l_2}, \ldots, s_{l_n})$$

3. **Keyword extraction from solutions:** From solutions in \(S_l\) and \(S_h\), extract keywords and vectorize them.
   $$K_{h}= LLM(promt_{extraction}, S_h)$$
   $$K_{l}= LLM(promt_{extraction}, S_l)$$

4. **Compute the embedding distance:** Evaluate \(K_h\) and \(K_l\) by computing the cosine similarity, which is the MSU score:
   $$\text{MSU}(X, S_h, LLM)  = \frac{{K_h \cdot K_l}}{{\|K_h\|_2 \cdot \|K_l\|_2}}$$

---
## Citation

> Hendrycks, Dan et al. (2021). Measuring Mathematical Problem Solving With the MATH Dataset. *NeurIPS*.
