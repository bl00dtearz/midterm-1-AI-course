# Midterm 1: answers

GitHub username: bl00dtearz
Session code: maple-66
Fingerprint: ed61aa15

## AI-use declaration

I used Claude (Anthropic) during this exam to explain the task and the formulas in simple words. I did not use any other AI tool.

## AI-use declaration

(About half a page: which assistants or tools you used and for what. If you used none, say so.)

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

| candidate | annual cost |
|---|---|
| A, k=3 | |
| A, k=5 | |
| B, k=3 | |
| B, k=5 | |

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
