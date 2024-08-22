---
title: "FASST"
excerpt: "Simultaneous speech translation using Llama3 backend <br/><br/><img src='/chinmaydandekar/images/fasst/latency.png' style='width: 75%'>"
collection: portfolio
---

<h2 style="text-align: center; text-style: bold"> FASST: Fast LLM-based Simultaneous Speech Translation </h2>
<p style="text-align: center;">
Siqi Ouyang†, Xi Xu†, Chinmay Dandekar‡, Lei Li†<br/>
†Carnegie Mellon University<br/>
‡University of California, Santa Barbara<br/>
{siqiouya, xixu, leili}@cs.cmu.edu<br/>
cdandekar@ucsb.edu
</p>

---

**Project Overview:**

FASST (Fast LLM-based Simultaneous Speech Translation) is an advanced system designed to address the challenges of real-time, simultaneous speech translation. This system leverages large language models (LLMs) to translate spoken language into text in another language as the speech is being delivered, making it ideal for applications in multilingual conferences, live streaming, and other real-time communication scenarios.

**Background:**

Simultaneous speech translation (SST) requires the translation of ongoing speech into another language without waiting for the entire speech to be completed. 

Here is an example of what simultaneous speech translation looks like:

<img src='/chinmaydandekar/images/fasst/latency.png'>

Note that AlignAtt, LST and FASST are models that simultaneous speech translation models.

The core challenge in SST is balancing translation quality with latency, where latency refers to the delay between the speech being spoken and the translation being generated. Traditional methods often struggle to maintain high translation quality without introducing significant latency, particularly when using LLMs, which are computationally intensive.

FASST addresses these challenges through several innovative techniques displayed here:
<img src='/chinmaydandekar/images/fasst/architecture.png'>

1. **Blockwise-Causal Speech Encoding (BCSE):**
   - This method incrementally encodes new speech input without recomputation, significantly reducing latency. The encoding process is divided into blocks, where each block of speech data is processed causally, meaning that only past and current data influence the encoding, not future data. This ensures that the system can begin translating sooner without waiting for large chunks of speech to be processed.


2. **Consistency Mask and Incremental LLM Decoding:**
   - FASST introduces a consistency mask that allows the LLM to decode the translation incrementally. This method ensures that each segment of translated text remains consistent with the overall context of the speech, even as new segments are being processed. The consistency mask helps in managing the translation of phrases that span multiple segments of speech.


3. **Two-Stage Training Strategy:**
   - FASST employs a two-stage training strategy to optimize the system for simultaneous inference:
     1. **Stage 1:** Aligns speech encoder outputs with LLM embeddings using word-aligned contrastive loss, ensuring that the model can accurately associate spoken words with their corresponding translations.
     2. **Stage 2:** Fine-tunes the system for simultaneous translation using a wait-k-stride-n policy, which determines how much of the speech is processed before starting the translation and how many words are generated before more speech is processed.



**Performance Evaluation:**

FASST was evaluated on the MuST-C dataset, which is a widely recognized benchmark for speech translation. The system demonstrated superior performance, achieving a 1.5 BLEU score improvement over previous state-of-the-art models in English-to-Spanish translation, while maintaining comparable latency.

Here are the results for the English to Spanish and English to German direction:
<img src='/chinmaydandekar/images/fasst/results.png'>

LAAL-CA is a metric used to measure the latency of a simultaneous speech translation model. For each line, every data point in the line represents a different _k_ in _wait-k-stride-n_, where k ranges from 1 to 5.  As we can see FASST outperforms all other models at similar latency, and Wait-k-Stride-n LST incurs a much higher latency for translation than FASST does.

---

**Links:**
For more details, read the paper here: [FASST paper](/chinmaydandekar/files/fasst.pdf)
