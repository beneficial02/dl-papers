# Paper

- A Persona-Based Neural Conversation Model (2016)

# Note

- Made seq2seq model that encodes individual characteristics like background information and speaking style.
- For Speaker Model (models respondent alone), encode speaker information each time step so it helps personalized response.
- The model can infer individual information from other persona nearby
- Speaker-Addressee model predicts speaker _A_'s response to a message from speaker _B_.
- So same speaker may respond differently according to the opposite.
- For Speaker Model, the data is collected from Twitter FireHose for 6 months period, only from users had 60~300 3-turn conversations. So the authors colleted 24,725,711 3-turn conversational sequences from 74,003 users. Another 12000 3-turn conversations from Twitter FireHose is used as dev, validation, test sets.
- 4-layer LSTM models(seq2seq) with 1,000 hidden cells for each layer, batch size 128, learning-rate 1.0, params initialized by uniform distribution [-0.1, 0.1], gradient clipping with threshold 5, vocabulary size limitation was 50,000, dropout rate 0.2.
- ran 14 epochs with a Tesla K40 for a month.
- [Sordoni et al. (2015)](https://arxiv.org/abs/1506.06714) dataset was used as baseline.
- For Speaker-Addressess Model, TV show (_Friends_, _Big Bang Theory_) scripts from IMSDb are used. The corpus was 69,565 turns for 13 characters. dev and testings sets are each about 2,000 turns.
- As the data set is small, used pre-trained model which is trained with OpenSubtitles dataset. Trained 10 interations, same protocols with Speaker Model.
- Word embeddings in both models are initialized by using params learned from OpenSubtitles dataset.
- User embeddings are randomly initialized with [-0.1, 0.1]
- And then ran additional 5 epochs until perplexity on the development set stabilized.
- Suggested models showed better performances in perplexity, BLEU score, MMI, MLE, and human evaluation.
- The model seems catched relationships between some characteristics(country and city), but it also generated inconsistent response. It might be a trade-off between general conversation and persona-specific conversation.

# Thoughts

- Big data acted like data augmentation for each individual. How can I use this technic?
- This paper's idea could be used like this - as the relationship between bot and user changes, speaking style could be changed.
