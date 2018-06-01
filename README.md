# Simulated Dialogue

## Machines Talking To Machines (M2M)

We present datasets of conversations between an agent and a simulated user.
These conversations are collected using our M2M framework that combines dialogue
self-play and crowd sourcing to exhaustively generate dialogues. The dialogue
self-play step generates dialogue outlines consisting of the semantic frames for
each turn of the dialogue. The crowd sourcing step provides natural language
realizations for each dialogue turn. More details are available in [this
paper](https://arxiv.org/abs/1801.04871). Please cite the paper if you use or
discuss these datasets in your work:

```shell
@article{shah2018building,
  title={Building a Conversational Agent Overnight with Dialogue Self-Play},
  author={Shah, Pararth and Hakkani-T{\"u}r, Dilek and T{\"u}r, Gokhan and Rastogi, Abhinav and Bapna, Ankur and Nayak, Neha and Heck, Larry},
  journal={arXiv preprint arXiv:1801.04871},
  year={2018}
}
```

## Datasets

We are releasing two datasets containing dialogues for booking a restaurant
table and buying a movie ticket. The number of dialogues in each dataset are
listed below. The README file within each directory contains further details
about the dataset.

| Dataset            | Slots                                                                          | Train | Dev | Test |
| ------------------ | ------------------------------------------------------------------------------ | ----- | --- | ---- |
| Sim-R (Restaurant) | price\_range, location, restaurant\_name,<br>category, num\_people, date, time | 1116  | 349 | 775  |
| Sim-M (Movie)      | theatre\_name, movie, date, time,<br>num\_people                               | 384   | 120 | 264  |
| Sim-GEN (Movie)    | theatre\_name, movie, date, time,<br>num\_people                               | 100K  | 10K | 10K  |

**The datasets are provided "AS IS" without any warranty, express or implied.
Google disclaims all liability for any damages, direct or indirect, resulting
from the use of these datasets.**

**Please email {abhirast, dilekh}@google.com with questions.**


## Dialogue State Tracking

Our publication *Scalable Multi-Domain Dialogue State Tracking (IEEE ASRU 2017)*
reports joint goal accuracy on Sim-R and Sim-M datasets. The released version of
the datasets includes fixes for some errors in dialogue state and action
annotations. This [updated version](https://arxiv.org/abs/1712.10224) of the
paper reports the results on corrected datasets.


## End-to-End Trainable Task Oriented Dialogue

Our publication [*Dialogue Learning with Human Teaching and Feedback in
End-to-End Trainable Task-Oriented Dialogue
Systems*](https://arxiv.org/pdf/1804.06512.pdf) uses Sim-GEN.
