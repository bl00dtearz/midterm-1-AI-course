# Midterm 1: answers

GitHub username: bl00dtearz
Session code: maple-66
Fingerprint: ed61aa15

## AI-use declaration

I used Claude (Anthropic) during this exam to explain the task and the formulas in simple words. I did not use any other AI tool.


## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)


| Config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A (paragraph) | 37/60 = 0.617 | 44/60 = 0.733 | 44/60 = 0.733 | 0.675 |
| B (sentence window) | 31/60 = 0.517 | 43/60 = 0.717 | 48/60 = 0.800 | 0.622 |


### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 | 44 | 0.733 | [0.610, 0.829] |
| A, k=5 | 44 | 0.733 | [0.610, 0.829] |
| B, k=3 | 43 | 0.717 | [0.592, 0.815] |
| B, k=5 | 48 | 0.800 | [0.682, 0.882] |

All four intervals overlap, so the data does not show that any candidate
is better than another. (B, 5) has the highest recall, but its interval
overlaps with all the others, so I cannot claim it is the winner.

### 1c. Annual model cost in USD

Cost of one request in language ℓ = (input tokens × $3 + output tokens × $15) / 1,000,000,
where input tokens = 206 (system) + question_ℓ + k × chunk_ℓ.
Annual cost = Σ (traffic share_ℓ × cost_ℓ) × 13,500 requests/day × 365.

| candidate | annual cost $ | Budget $29,800 |
|---|---|---|
| A, k=3 | 35,400 | over budget |
| A, k=5 | 48,714 | over budget |
| B, k=3 | 20,740 | within budget |
| B, k=5 | 24,281 | within budget |

Both A candidates are too expensive because paragraph chunks are about
4 times longer than sentence-window chunks and Russian and Kazakh chunks
are longer than English ones. Only the two B candidates fit the budget.

### 1d. Decision (at most 150 words)

Chosen candidate:

(Decision, using your intervals and the budget. Give the recall of your choice for EN, RU and KK separately.)

### 1e. Next measurement (at most 60 words)

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H | | | | | | |
| L | | | | | | |

Personal-data pages per year sent abroad under H:

### 2b. Memo (at most 300 words)

## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words):

### Q2

Number:
Why (at most 40 words):

### Q3

Number:
Why (at most 40 words):

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
