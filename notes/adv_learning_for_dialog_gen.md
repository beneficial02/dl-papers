# Paper

- Adversarial Learning for Neural Dialogue Generation (2017)

# Note

- Implemented adversarial learning to open-domain dialogue generation system with deep reinforcement learning.
- Inspired from Turing Test - A good dialogue model should generate utterances indistinguishable from human dialogue.
- Generative model takes a form similar to seq2seq with policy gradient
- Discriminative model encodes input using hierarchical encoder(LSTM), then feed to 2-class softmax fuction, do binary classification.
- The authors suggests an algorithm _REGS_ which calcuclates reward for every token generation step, as vanilla model can calculate the reward only after the whole generation is finished. To achive this, Monte Carlo search and training a discriminator that is able to assign rewards to partially decoded sequences are proposed.
- In order to teach some standard targets for generator, human-generated resoponses are also fed to generator (teacher-forcing).
- Pre-train generative model, which is seq2seq model with attention, on the OpenSubtitles dataset.
- Pre-train discriminative model with half of negative examples (machine-generated through decoding).
- A few strategies are used to improve response quality.
  - Remove training examples with the length of responses shorter than a threshold (5) - significantly improve.
  - Use weighted learning rate considering the average tf-idf score for tokens within the response - the effect from dull & generic response decrease.
  - Penalize intra-sibling ranking when doing beam search. Penalize word types that already generated - dramatically decrease the repetitive/contradictory response.
- The author also propose adversarial evaluation, which is a seperate procedure from adversarial training, to measure the general quality of responses.
- To use the adversarial evaluator, we have to assume the evaluator is reliable. However, if the discriminator is not good enough, evaluation is meaningless.
- So scenarios to evaluate the evaluator is developed.
- Based on suggested metrics, model with Hierarchical Neural setting is chosen to be used as evaluator.
- Human evaluation is also done, following protocols from the [previous paper](https://arxiv.org/abs/1606.01541).
- Suggested model with _REGS_ outperformed baseline models. In constrast to the [previous paper](https://arxiv.org/abs/1606.01541), single-turn dialogue quality is also improved.
- So, reward adopted in adversarial training is more general than heuristically defined reward.


# Thoughts

- I think I couldn't understand the evaluation part well. But it also seems good paper.
