# Quotes Generation — QGT-2

 Creating captivating quotes from a single word input using the power of AI and Mathematics

### Noteworthy Quotes

```py
"The meaning of life may only be to cope with the lies spread by nerves, but cats seem to have it figured out"
"Innocence and guilt breathe life into our choices, carefully projecting the will to move forward. In the end, even John may be abandoned"
"Guilt without glory isn't great, but my only purpose now is to do anything I can to make up for it"
"Cats may be buried, but they are not gone forever. They are somehow still alive and ignited within us, even if we cannot see them"
```

### Motivation

From a deep-rooted passion for philosophy and some blank walls in my room, I set out to use AI to generate the quote for some artwork, and I couldn't find anything I liked online. Also with the hype surrounding natural language processing I wanted to see what I could build on my home computer, as compared to spending millions of dollars on the cloud.

### Objective

Leverage AI to generate some profound and weird quotes, and see where it takes us.


### Dataset

The dataset I found was on Kaggle. It has nearly 500k quotes which was perfect for what I was looking for. [Here is the dataset](https://www.kaggle.com/datasets/manann/quotes-500k)

# Process

### First Steps

Immediately I wanted to try to generate the characters individually and see where that could take me, keeping the vocab size low and focusing primarily on the training. I started with tensorflow and built out a simple one step model. I experimented with various model architectures, starting with a basic Recurrent Neural Network (RNN) to understand the fundamental aspects of sequence generation. The idea was to generate characters one by one, gradually building up the quote.

For the initial step, I preprocessed the dataset by tokenizing the quotes into individual characters. This allowed me to create a simplified vocabulary, which helped in managing the complexity of the model. I implemented the RNN using TensorFlow's API and trained it on the dataset. The results were intriguing but not yet up to the level I was aiming for.

```py
"Bliss is a myth, more like more trees with eternal blood, though not all awake in pain"
```

### Iterative Refinement

Recognizing the limitations of the basic RNN, I decided to explore more advanced architectures like Long Short-Term Memory (LSTM) and Gated Recurrent Units (GRU). These architectures proved to be more effective in capturing long-range dependencies within the quotes, leading to the generation of more coherent and contextually relevant text.

However, a challenge emerged with generating quotes that made sense both grammatically and semantically. To address this, I introduced attention mechanisms to give the model the ability to focus on different parts of the quote as it generated each character. This resulted in quotes that had a smoother flow and a better sense of structure. Even still, I thought I could do better.

```py
"Chess is a game of grace, and life is a game of chess; it is never too late to have grace, now or never"
```


### A Switch in Strategy

I reached out to a friend of mine much more experienced than me in machine learning to ask for advice on the model. He reccomended switching from generating characters to words. This reduction in complexity was aiming to make it easier for the model to construct complex sentences. However, where the drop in the complexity for words, the vocab size became much, much larger. In fact I has to run some filtering to only use the most common words in the dataset. This loss of some quotes was a constraint I had to deal with in the training time.

I adopted a Word-level LSTM model for this new approach. This allowed the model to grasp the relationships between words and produce quotes that were more structurally accurate. The model now considered the context of the previous words while generating the next one, resulting in quotes that flowed more naturally.

### Fine-Tuning and Hyperparameter Optimization

With the word-level generation strategy in place, I focused on fine-tuning the model's hyperparameters. This involved experimenting with various settings such as the number of LSTM layers, hidden units, dropout rates, and learning rates. The objective was to strike a balance between generating diverse and creative quotes while maintaining coherence and relevance.

Through an iterative process of training, evaluating, and adjusting parameters, I was able to achieve a more consistent and satisfactory generation of quotes. The final model produced quotes that exhibited a remarkable blend of philosophical depth and a bit of crazy too.

# Conclusion

This project was quite an interesting one. I switched my strageties quite a few times and had to do a lot of experimenting with what worked. There was a lot to take away from this and I learned a lot. I hope you enjoyed reading this as much as I enjoyed writing it.

### Citation

if you find this code useful, please site the following:

```py
@misc{Schaefer2022,
  author = {Schaefer, Nik},
  title = {quotes-generation},
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/NikSchaefer/quotes-generation}},
}
```

### License

[MIT](https://choosealicense.com/licenses/mit/)
