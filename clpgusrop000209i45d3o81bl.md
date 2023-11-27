---
title: "LLMs : Large Language Models Learnings & Laws"
seoTitle: "LLMs : Large Language Models learnings & Laws"
seoDescription: "Deep dive into the LLMs mechanisms and various learnings which make it, take over a lot of roles and positions in tech domain"
datePublished: Mon Nov 27 2023 11:56:33 GMT+0000 (Coordinated Universal Time)
cuid: clpgusrop000209i45d3o81bl
slug: llms-large-language-models-learnings-laws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700961672762/c243cf92-7663-4c1b-abde-f214832dfa2c.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1700961837696/e31c46e2-a41a-47a9-8e48-abb729f36a9d.jpeg
tags: ai, artificial-intelligence, machine-learning, deep-learning, wemakedevs, chatgpt

---

# Introduction

Artificial Intelligence has been taking huge steps in the development processes not only by helping in developing the codebase but also have coming up with deployments and auto management of the codebase to production. Eatin up a lot of jobs in the tech community, it has come across to perform a lot of actions that weren't easy to find with a single developer let it be related to Machine Learning, Data Structure, Web Development, DevOps, Cloud, SRE and a lot more roles, which started from the training model for text manipulation and generation which enables models to understand form the input and then guess its answer from the training data been fed or being developed after scaling it up, these were the Large Language Models (LLMs). Here in this blog, we will be learning about different models, learnings adopted by these models and their efficiency comparison and Laws that can be further used by us to make our own tools and contribute to this revolution.

# Large Language Models

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701085139523/c5636135-3e3f-45db-9f75-7d9cf0c4410b.jpeg align="center")

Large Language Models (LLMs) are a specific category of neural network models characterized by having an exceptionally high number of parameters, often in the billions. These parameters are essentially the variables within the model that allow it to process and generate text which are trained on vast quantities of textual data, which provides them with a broad understanding of language patterns and structures. The main goal of LLMs is to comprehend and produce text that closely resembles human-written language, enabling them to capture the subtle complexities of both syntax (the arrangement of words in a sentence) and semantics (the meaning conveyed by those words).

These models undergo training with a simple objective: predicting the subsequent word in a sentence. However, they develop a range of **emergent abilities** during this training process.

## Language Modelling

Language modeling helps in explicitly learning the probability distribution of the words in a language. This method predicts the next token based on the previous token in sequence by using various statistical methods or deep learning techniques.

### Tokenization

The first step in this process is tokenization, where the input text is broken down into smaller units called tokens. Tokens can be as small as individual characters or as large as whole words. The choice of token size can significantly affect the model's performance. Some models even use subword tokenization, where words are broken down into smaller units that capture meaningful linguistic information.

For example: we could take the word Large Language Model as the tokens in the training dataset, where we may split up the tokens in the line whenever we find the white spaces as :

```python
["Large", "Language", "Model"]
```

or else, we may also include the white spaces in the training dataset if we wants to include them as:

```python
["Large", " ", "Language", " ", "Model"]
```

### **Model Architecture and Attention**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701084199965/5defecaa-e79c-436b-8b90-fff557e69d4b.jpeg align="center")

The core of a language model is its architecture. Recurrent Neural Networks (RNNs) were traditionally used for this task, as they are capable of processing sequential data by maintaining an internal state that captures the information from previous tokens.

#### **Vanishing Gradient Problem (VGP)**

In [machine learning](https://en.wikipedia.org/wiki/Machine_learning), the **vanishing gradient problem** is encountered when training [artificial neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) with [gradient-based learning methods](https://en.wikipedia.org/wiki/Stochastic_gradient_descent) and backpropagation. In such methods, during each iteration of training each of the neural network weights receives an update proportional to the [partial derivative](https://en.wikipedia.org/wiki/Partial_derivative) of the error function concerning the current weight. The problem is that in some cases, the gradient will be vanishingly small, effectively preventing the weight from changing its value. In the worst case, this may completely stop the neural network from further training.

#### **Transformer Adoption to Overcome VGP:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701085726289/691d773f-a214-4bab-bce7-1b812b7106c2.png align="center")

This Vanishing Gradient Problem leads to addressing the struggle for long sequences. To overcome these limitations, transformer-based models have become the standard for language modeling tasks. These models use a mechanism called **attention**, which allows them to weigh the importance of different tokens when making predictions. This allows them to capture long-range dependencies between tokens and generate high-quality text.

#### **Training**

The model is trained based on a large amount of training dataset and parameters to maximize the probability of the output received, to predict the next token of a sentence correctly.

Typically a model is trained on a very large general dataset of texts from the Internet, such as [The Pile](https://pile.eleuther.ai/) or [CommonCrawl](https://commoncrawl.org/). Sometimes also more specific datasets are used, such as the [StackOverflow Posts](https://huggingface.co/datasets/mikex86/stackoverflow-posts) dataset.

<mark>The model learns to predict the next token in a sequence by adjusting its parameters to maximize the probability of outputting the correct next token from the training data.</mark>

Once the model, is trained it is expected to output the next token in the sequence based on the corpus provided, which is done by feeding the sequence into the model. This outputs a probability distribution over the possible subsequent tokens. based on which the next token is then chosen.

## Fine Tuning

Fine-tuning is the process of taking pre-trained models and further training them on smaller, specific datasets to refine their capabilities and improve performance in a particular task or domain. Fine-tuning is about turning general-purpose models and turning them into specialized models. It bridges the gap between generic pre-trained models and the unique requirements of specific applications, ensuring that the language model aligns closely with human expectations. Think of OpenAI's GPT-3, a state-of-the-art large language model designed for a broad range of natural [](https://www.superannotate.com/blog/what-is-natural-language-processing)language processing (NLP) tasks.

## **Few Short Learning**

Few-shot learning refers to a machine learning paradigm where a model is trained on a small amount of data before making predictions, which can be particularly useful when label

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701084311627/1cb3f70c-e7de-4dfe-8494-2546df4c88de.gif align="center")

ed data is limited. These examples "teach" the model how to reason and act as "filters" to help the model search for relevant patterns in the dataset.

<mark>The advantage of few-shot learning is fascinating as it suggests that the model can be quickly reprogrammed for new tasks.</mark>

The few-shot examples are helping the model search for relevant patterns in the dataset. The dataset, which is effectively compressed into the model's weights, can be searched for patterns that strongly respond to these provided examples. These patterns are then used to generate the model's output. The more examples provided, the more precise the output becomes.

## **Scaling Laws**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701084423321/31dcd6e4-3ada-4be2-a555-6326b2612b8e.png align="center")

Scaling laws refer to the relationship between the model's performance and factors such as the number of parameters, the size of the training dataset, the compute budget, and the network architecture. They were discovered after a lot of experiments and are described in the [Chinchilla paper](https://arxiv.org/abs/2203.15556). These laws provide insights into how to allocate resources when training these models optimally.

The main elements characterizing a language model are:

1. The number of parameters (N) reflects the model's capacity to learn from data. <mark>More parameters allow the model to capture complex patterns in the data.</mark>
    
2. The size of the training dataset (D) is measured in the number of tokens.
    
3. FLOPs (floating point operations per second) measure the compute budget used for training.
    

#   
**Emergent Abilities in LLMs**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701084494512/f80d5576-bec9-4136-8832-96a1095cbe4a.png align="center")

Emergent abilities in LLMs refer to the sudden appearance of new capabilities as the size of the model increases. These abilities, which include performing arithmetic, answering questions, summarizing passages, and more, are not explicitly trained in the model. Instead, they seem to arise spontaneously as the model scales, hence the term "emergent."

***LLMs are probabilistic models that learn patterns in natural language.***

***<mark>When these models are scaled up, they not only improve quantitatively in their ability to learn patterns, but they also exhibit qualitative changes in their behavior.</mark>***

Earlier, the models needed to be architecturally upgraded using various task-specific trainings and learnings, but now only scaling these models can help in developing new functionalities and perform these specific trainign and learnings by itself without getting to invest much time in these tasks, and can just monitor to keep track of the the features and learnings it produced due to scaling in itself.

These LLMs can grow rapidly and unpredictably transition from near-zero to sometimes state-of-the-art performance. This phenomenon suggests that these abilities are emergent properties of the model's scale rather than being explicitly programmed into the model.

**Thus just scaling up these models can lead to the spontaneous development of new capabilities.** Thus these self-learnings can give rise to some unethical or incorrect outputs being reflected by the LLMs when asked for an output, which can result in spreading wrong information, misleading people or might even hurt some people of color or gender, due to some racial comment. These are known as the Hallucinations and Biases in LLMs, which need to be monitored and corrected by the developers after scaling up the LLMs.

# **Hallucinations and Biases in LLMs**

Hallucinations in LLMs refer to instances where the model generates outputs that do not align with real-world facts or context. This can lead to the propagation of misinformation, especially in critical sectors like healthcare and education where the accuracy of information is of utmost importance. Similarly, bias in LLMs can result in outputs that favor certain perspectives over others, potentially leading to the reinforcement of harmful stereotypes and discrimination.

For example, someone asked who get the Nobel Prize for Physics in 2050, and LLM came up with a name for an year that hasn't even announced.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701085081919/679ff604-cdb0-4575-9d10-a69263faff6a.png align="center")

**Bias** in AI and LLMs is another significant issue. It refers to these models' inclination to favor specific outputs or decisions based on their training data. If the training data is predominantly from a specific region, the model might show a bias toward that region's language, culture, or perspectives. If the training data contains inherent biases, such as gender or racial bias, the AI system might produce skewed or discriminatory outputs.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701085069689/e79d26f7-7c6d-477c-8c7b-43dd6f008739.png align="center")

For example, ChatGPT and many other LLMs were being blamed for biasing according to Gender, Color, and other types, like the most common type of Bias being observed by many people was, while they were generating images through the image generation tools like Midjourney and Dall E by Open AI, where whenever users asked to generate an image of a nurse, it came out to be a women but when they were generating for a doctor then it came out to generating a picture of a man, which offended many people.

Mitigating hallucinations and bias in AI systems involves refining model training, using verification techniques, and ensuring the training data is diverse and representative. Finding a balance between maximizing the model's potential and avoiding these issues remains challenging.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701084745131/d602e545-2d76-4ccb-9170-b53d6b7ddc26.jpeg align="center")

These kinds of hallucinations can be useful in creative domains like media and fiction writing and can be helpful for enabling the generation of unique and innovative content

I hope you found some value that got added to you, soon I will be releasing a blog explaining various different kinds of LLM models with their amazing specs and the whole timeline explaining the upgrades that took place in LLMs, the Transformer's working & mechanisms in LLMs & emergent abilities in LLMs & It's going to be LEGEN.....DARY🔥🔥

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701086039628/eb0a1219-087c-4fa3-9d9f-b51ec0881c52.gif align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)