# Papers
- Learning Phrase Representations using RNN Encoder-Decoder for Statistical Machine Translation (2014)
- Sequence to Sequence Learning with Neural Networks (2014)

# Note
- Both papers show Seq2Seq model is cool.
- LSTM can map an input sentence with variable length into a fixed-legth vector representation.

#### in Sutskever et al.
- Reversing the source sentences made better result, even with long sentences.
- Deep LSTMs significantly outperform shallow LSTMs.
- **They wrote training details thoroughly!**
  - Used deep LSTMs with 4 layers, with 1000 cells at each layer and 1000 dimensional word embeddings.
  - Each additional layer reduced perplexity by nearly 10%
  - Initialized all parameters with the uniform distribution between -0.08 and 0.08
  - SGD with learning rate = 0.7. After 5 epochs, halved learning rate every half epoch. Trained for total 7.5 epochs.  
  - Made a constraint for the gradient to avoid exploding gradients.
  - Made all sentences in a minibatch to have roughly same length to boost speed.
