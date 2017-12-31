# Are You Talking to Me? Reasoned Visual Dialog Generation through Adversarial Learning

Qi Wu, Peng Wang, Chunhua Shen, Ian Reid, Anton van den Hengel, ArXiv, 2017

## Summary

This paper introduces adversarial training for the task of visual dialog, which is to generate a natural language answer to a question about an image conditioned on and consistent with human dialog history. This is motivated by the goal of developing a visual dialog model capable of generating answers indistinguishable from human answers. Key contributions:

- The answerer is a sequential co-attention based generative model while the adversary or discriminator is a conditional model that tries to discriminate ground-truth human answers from model samples conditioned on the question, image and dialog history features. Since generating an answer involves sequential sampling which is non-differentiable, the answerer is considered to be a stochastic policy as in RL and its gradients estimated via REINFORCE with the output of the discriminator as the reward.

- And since the discriminator only operates on complete sequences, roll-outs are used to estimate intermediate rewards. This works by estimating reward for a token by sampling multiple completions for the same prefix and state and averaging obtained rewards.

- The resulting model + training paradigm is evaluated on the VisDial dataset and achieves state-of-the-art results both for the generative and discriminative settings. Further, fairly exhaustive comparisons with ablations are performed — training with MLE, with/without intermediate rewards, combining with teacher forcing — to tease out individual contributions of factors. Finally, human studies are conducted on 1000 samples where  subjects are asked 1) whether the response was generated by a model or a human, and 2) if model responses are equal or better than human responses, and in both, the proposed model outperforms baselines.

## Notes

The paper is well-motivated, clearly written and the formulation is fairly clear for the most part and the results encouraging. Although much of it seems a direct application of Yu et al., "SeqGAN: Sequence Generative Adversarial Nets with Policy Gradient" to Visual Dialog, this is the first time it's been tried and gotten to work, which is great!