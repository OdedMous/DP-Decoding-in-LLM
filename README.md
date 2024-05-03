# DP-Decoding-in-LLM



## Motivation

Large language models are pre-trained on a vast amount of public data collected from the Internet, which very likely contains private or sensitive information. Combined with the fact that large models tend to memorize training data, this scenario poses a potential risk of data leakage.

Differential privacy (DP) is a paradigm that can help in this regard. In the realm of AI models, this method is usually applied during the training phase, but due to the cost of re-training a large model, it is possible to incorporate it at inference time only.

## Method

Recall that during inference time, the LLM generates text token by token. At each step, it selects the next token based on the probability distribution it has created over the vocabulary. This process is known as the "decoding strategy". Various decoding strategies exist, with one basic approach being to simply sample a word according to this distribution. 

The paper **"Differentially Private Decoding in Large Language Models"**, authored by Majmudar, Jimit, et al. (2022), proposes a straightforward perturbation approach to this decoding strategy. 
This method applies linear interpolation between the original distribution q and the uniform
distribution u:

![BreadcrumbsDP-Decoding-in-LLM](https://github.com/OdedMous/DP-Decoding-in-LLM/blob/main/perturbatiation%20method.png)


The parameter lambda controls the trade-off balance between utility (the effectiveness of the generated output) and privacy  (the protection of sensitive information). See an example below:

![BreadcrumbsDP-Decoding-in-LLM](https://github.com/OdedMous/DP-Decoding-in-LLM/blob/main/Utility-privacy%20tradeoff%20example.png)


## My Experiments

**Experiment 1:** Sentence Complement task (using  GPT-2 model)

T is the number of predicted tokens.


![BreadcrumbsDP-Decoding-in-LLM](https://github.com/OdedMous/DP-Decoding-in-LLM/blob/main/Utility-privacy%20tradeoff.png)

**Experiment 2:** Visual QA task (using ViLT model)

![BreadcrumbsDP-Decoding-in-LLM](https://github.com/OdedMous/DP-Decoding-in-LLM/blob/main/word%20probabilities.png)
