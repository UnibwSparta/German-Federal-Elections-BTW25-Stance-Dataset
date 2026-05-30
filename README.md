# #btw25: Fine-Grained Multi-Target Stance Detection Toward German Political Actors

This repository contains the **#btw25** dataset, a resource for fine-grained, multi-target stance detection in German political discourse on X (formerly Twitter), collected during the **2025 German federal election campaign** (Bundestagswahl 2025).

## Overview

#btw25 provides stance annotations toward the major German political parties and their leading candidates, supporting target-specific labeling for posts that mention multiple political actors simultaneously. Unlike most existing stance detection datasets, which rely on coarse three-way labels (*against*, *neither*, *in favor*), #btw25 adopts a **five-class annotation scheme** that captures both the direction and intensity of expressed stances:

| Label | Description |
|---|---|
| 1 – strongly against | Explicit rejection, hostility, or strong disagreement |
| 2 – slightly against | Mild criticism or negative orientation |
| 3 – neither | No clear stance, ambiguous, or reporting only |
| 4 – slightly in favor | Mild support or positive orientation |
| 5 – strongly in favor | Explicit endorsement, mobilization, or self-identification |

## Targets

The dataset covers 7 parties and 8 leading candidates:

- **SPD** — Olaf Scholz
- **CDU/CSU** — Friedrich Merz
- **Bündnis 90/Die Grünen** — Robert Habeck
- **FDP** — Christian Lindner
- **AfD** — Alice Weidel
- **Die Linke** — Heidi Reichinnek, Jan van Aken
- **BSW** — Sahra Wagenknecht

## Dataset Structure

The dataset is split chronologically to support realistic evaluation settings in which models are trained on earlier campaign data and applied to later periods. It comprises the following subsets:

**Training subsets** (initiation phase, Oct 2024 – Jan 2025):
- `t_init` — prediction-balanced, initial sample
- `t_amb` — prediction-balanced, ambiguous
- `t_pop` — popular posts

**Evaluation subsets** (weekly intervals, Jan – Feb 2025):
- `b1_amb--b4_amb` — prediction-balanced, ambiguous
- `b5_fair` — prediction-balanced, fair
- `b6_namb` — prediction-balanced, non-ambiguous
- `p1_pop--p6_pop` — popular posts (most-shared)

## Data Format

Each subset is provided as a JSON file. Each entry contains the following fields:

```json
{
  "tweet_id": "string",
  "labels": {"EntityName": 1},
  "spans": [
    {
      "type": "hashtag | user_mention | plain",
      "text": "string",
      "start": 0,
      "end": 10,
      "affiliations": [
        {
          "name": "string",
          "affiliation_type": "party | person",
          "association": "string | null"
        }
      ]
    }
  ],
  "text": "string (available upon request)"
}
```

> **Note:** Post text is not included in the open-access release due to platform terms of service and data protection requirements. It is available upon request strictly for research purposes only.

## Citation

TODO

## License

TODO
