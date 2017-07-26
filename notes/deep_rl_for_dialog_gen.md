# Paper

- Deep Reinforcement Learning for Dialogue Generation (2016)

# Note

- Integrated deep reinforcement learning to make chatbot take account of long-term reward in the conversation.
- Seq2seq model was used as backbone of the model. The author simulated conversation between two agents and made them learn how to maximize expected reward.
- Each dialogue turn was handled as actions taken according to a policy.
- Policy gradient method was more suitable than Q-learning for the scenario.
- The previous two dialogue turns were used as state.
- The policy took the form of an LSTM encoder-decoder.
- The reward was composed of ease of answering, information flow, and semantic coherence.  
  - Ease of answering: The negative log likelihood of responding to the utterance with a dull response like "I have no idea", "I don't know what you're talking about".
  - Information flow: The author wanted each turn to have new information. So the negative log of the cosine similarity between the previous turn and new turn.
  - Semantic coherence: To make sure that the generated reply is grammatical and coherent, mutual information between the previous turn and new turn.
  - Final reward is calculated by weighted sum of the 3 rewards (0.25, 0.25, 0.5)
- For training, predicting a target sequence using supervised seq2seq model was used first. OpenSubtitles dataset and seq2seq2 model with attention was used.
- The authors initialized policy model with pre-trained seq2seq model. But pre-trained seq2seq model generates dull response often, mutual information score from pre-trained model's previous turn and new turn (candidates) is used as a reward and back-propagated to generated sequences with higher rewards.
- Curriculum learning strategy was employed as beginning simulation by 2 turns of dialogue to 5 turns at most. 5 candidate responses are generated at each step of the simulation.
- 0.8 million sequences from OpenSubtitles dataset which have low likelihood of generating the response "I don't know what you are talking about" were extracted for the evaluation.
- As the suggested model pursue the long-term success, the author thought BLEU score and perplexity are not suitable for the evaluation. Following metrics are used.
  - Length of the dialogue: The author judged a conversation ends when a agent generate dull reponses (rule base), or two consecutive utterances from same agent are highly overlapping (whether share same words more than 80%).
  - Diversity: The number of distinct unigrams and bigrams in generated responses.
  - Human evaluation
    1) Generated outputs of two models were presented to 3 judges and asked to decide which is better.
    2) The judges asked to decide which is easier to respond to.
    3) 200 simulated 5-turn conversations were presented to the judges, and asked to decide which has higher quality.
- RL based agent generated more interactive responses.
- **RL based agent had a tendency to end a sentence with another question and hand the conversation over to the user.**
- The dialog somtimes entered a cycle with 2 or greater length.
- The model sometimes gave a less relevant topic during the conversation.
- The metrics used for the reward is heuristic.
- the model couldn't consider longer turns in the simulation as the number of cases grow exponentially.

# Thoughts
- Great paper. It has many points which could be implemented for the chatbot systems.
- Though the metrics in reward and evaluation is heuristic, it seems good. It could be a light for the next step.
- Is there no conflict between information flow and semantic coherence in the reward?
- What is the criteria for deciding the quality of conversation in Human Evaluation step?
