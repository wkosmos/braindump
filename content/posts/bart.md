+++
title = "BART"
author = ["Jethro Kuan"]
draft = false
+++

BART is a denoising auto-encoder for pretraining sequence-to-sequence models. BART is trained by:

1.  corrupting text with an arbitrary noising function
2.  learning a model to reconstruct the original text

It generalizes BERT and GPT. One key advantage of BART is that the noising
function can be arbitrarily selected. For example, they introduce an in-filling
scheme replacing arbitrary lengths of text with a single mask token. This
generalizes the original word masking and next sentence prediction objectives.

BART is trained by corrupting documents and then optimizing a reconstruction
loss - the cross-entropy between the decoder's output and the original document.

BART can then be fine-tuned for downstream applications:

sequence classification
: the same input is fed into the encoder and decoder, and the final decoder token and hidden state is fed into a new multi-class linear classifier.

token classification
: feed the complete document into the encoder and decoder, and use the top hidden state of the decoder as a representation for each word.

sequence generation
: input sequence is given to the encoder, and the decoder
generates auto-regressively.
