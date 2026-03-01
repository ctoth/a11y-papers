# Abstract

## Original Text (Verbatim)

The accuracy of Automated Speech Recognition (ASR) technology has improved, but it is still imperfect in many settings. Researchers who evaluate ASR performance often focus on improving the Word Error Rate (WER) metric, but WER has been found to have little correlation with human-subject performance on many applications. We propose a new captioning-focused evaluation metric that better predicts the impact of ASR recognition errors on the usability of automatically generated captions for people who are Deaf or Hard of Hearing (DHH). Through a user study with 30 DHH users, we compared our new metric with the traditional WER metric on a caption usability evaluation task. In a side-by-side comparison of pairs of ASR text output (with identical WER), the texts preferred by our new metric were preferred by DHH participants. Further, our metric had significantly higher correlation with DHH participants' subjective scores on the usability of a caption, as compared to the correlation between WER metric and participant subjective scores. This new metric could be used to select ASR systems for captioning applications, and it may be a better metric for ASR researchers to consider when optimizing ASR systems.

---

## Our Interpretation

WER counts errors uniformly, but not all errors damage comprehension equally — errors on unpredictable, semantically important words are far more disruptive to DHH readers than errors on predictable function words. This paper solves the measurement problem: the ACE metric scores each error by how unpredictable the correct word was and how semantically far the error word landed, producing a single quality score that actually matches what DHH users experience. With ACE correlating at ρ=0.743 vs. WER's ρ=0.109 with DHH subjective ratings, this is the paper to cite when justifying why WER is insufficient for DHH captioning research and what to use instead.
