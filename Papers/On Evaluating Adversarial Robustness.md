# On Evaluating Adversarial Robustness

| Date | Authors | Keywords | Paper Link | GitHub Link | Work Status |
|:----:|:-------:|:--------:|:----------:|:-----------:|:-----------:|
| 20 Feb 2019 | Carlini et al. | Adversarial Evaluation | <https://arxiv.org/abs/1902.06705> | <https://github.com/evaluating-adversarial-robustness/adv-eval-paper> | Incomplete |

### TL;DR

Many of the research on adversarial defense shown to be incorrect or incomplete. This *living* paper offers principles and checklists to guide a rigorous adversarial defense research.

### Highlights

- Principles of Rigorous Evaluations
	- Define a clear threat model (i.e. conditions under which defense is intended work and must be evaluated) such as **$\ell_p$-norm constrained**.
	- Assume attacker is aware of the defense method and deliberately try to break your defense. Utilize adaptive attacks that are tuned to specifics of defense for evaluation. (Quote) **an evaluation against non-adaptive attacks**  (e.g. state-of-the art PGD with default hyperparameters) **is of very limited utility.**
	- Share source code and pretrained models for community to analyze.
