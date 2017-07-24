# Paper

- Generating Long and Diverse Responses with Neural Conversation Models (2017)

# Note

- Generated longer response than the standard seq2seq model.
- Putting target-side attention freed up capacity which is required to generate long coherent response, but it was too memory-intensive for large data set.
- So they put _glimpses_ to keep track of what has been outputs so far, and it hadn't any memory issues with very large data sets.
- In order to generate long coherent and diverse response, they injected diversity earlier during the decoding process to make the biggest effect for diversity of generated beams.
- They used Reddit data, 2009 Open Subtitles data, Stack Exchange data, Dialogue-like texts extracted from the web (total 2.3B messages)
- For the evaluation, they used N-choose-K metric as a first diagnostic for faster experimental iteration, like 1 day for a small model with a single GPU to reach 2-choose-1 accuracies 70%-80%.
- Also they used 5-scale human evaluation with 200 context-free open-domain prompts, collected from the sentences that users asked an internal testing bot, The Fisher corpus, Jabberwacky chabot inputs.
- Suggested model generated longer responses, with constant _Acceptable_ or _Excellent_ proportion.
- But when the responses are short, standard beam search generated better resposes.
- So they used both - when the response of suggested model is shorter than 40 characters, they used baseline model.
- Combined model made better result, and human raters alse preferred combined model than baseline model, 103 to 77.
