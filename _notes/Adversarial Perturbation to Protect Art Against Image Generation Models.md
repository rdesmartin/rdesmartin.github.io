---
tags:
  - logic
  - proof-checking
season: winter
---
Recent advances in image generation models (IGM) like Midjourney, Stable Diffusion or Dall-e pose an ethical and copyright problem, as they are trained on art found online without the artists consent, and make it possible to mimic the artists's style. Artists have already [sued creators of image generation models](https://www.polygon.com/23558946/ai-art-lawsuit-stability-stable-diffusion-deviantart-midjourney).

One possible solution to this problem is to use [adversarial perturbations](https://arxiv.org/abs/1412.6572): it is known that small perturbation in the input can fool even very accurate neural networks. In the case of image input, like it is the case for IGM, these perturbations can be imperceptible to the human eye.
The idea is then let an artist A compute perturbations that will make popular AI models misclassify their art as belonging to a different style B, and apply these perturbations to their art pieces before posting them online. This way, A's art will be scraped and used to train IGMs, but when the IGM will be prompted to mimic style A, it will instead mimic style B.

This approach was published by [Glaze](https://arxiv.org/pdf/2302.04222.pdf), a project from a University of Chicago team.