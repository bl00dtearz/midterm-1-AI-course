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
| A | 0.617 | 0.733 | 0.733 | 0.675 |
| B | 0.517 | 0.717 | 0.800 | 0.622 |


### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 | 0.733 | 0.610 | 0.829 |
| A, k=5 | 0.733 | 0.610 | 0.829 |
| B, k=3 | 0.717 | 0.592 | 0.815 |
| B, k=5 | 0.800 | 0.682 | 0.882 |

All four intervals overlap, so the data does not show that any candidate
is better than another. (B, 5) has the highest recall, but its interval
overlaps with all the others, so I cannot claim it is the winner.

### 1c. Annual model cost in USD

Cost of one request in language ℓ = (input tokens × $3 + output tokens × $15) / 1,000,000,
where input tokens = 206 (system) + question_ℓ + k × chunk_ℓ.
Annual cost = Σ (traffic share_ℓ × cost_ℓ) × 13,500 requests/day × 365.

| candidate | annual cost $ |
|---|---|
| A, k=3 | 35400 |
| A, k=5 | 48714 |
| B, k=3 | 20740 |
| B, k=5 | 24281 |

Both A candidates are too expensive because paragraph chunks are about
4 times longer than sentence-window chunks and Russian and Kazakh chunks
are longer than English ones. Only the two B candidates fit the budget.

### 1d. Decision (at most 150 words)

Chosen candidate: B, k=3

Both A candidates are over the $29,800 budget ($35,400 and $48,714), so only
B is possible. (B, 3) has recall 0.717 [0.592, 0.815] and (B, 5) has 0.800
[0.682, 0.882]. The intervals overlap, so the data does not show that (B, 5)
is better. I choose the cheaper one: $20,740 per year against $24,281.

Recall of (B, 3) per language (20 questions each):
- EN: 15/20 = 0.75 [0.531, 0.888]
- RU: 19/20 = 0.95 [0.764, 0.991]
- KK: 9/20 = 0.45 [0.258, 0.658]

Kazakh users are served worst: for more than half of their questions the
right chunk is not in the top 3.

### 1e. Next measurement (at most 60 words)

Build a larger Kazakh-only test set (about 200 questions) and measure (B, 3)
and (B, 5) on it. With 20 questions the Kazakh intervals are too wide. If (B, 5)
is clearly better (intervals do not overlap), the extra $3,500 per year is
justified and I would switch.

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H | 0.883 | KK, degraded | 0.767 | 0.591 | 0.882 | 47205 |
| L | 0.800 | RU, degraded | 0.667 | 0.488 | 0.808 | 10800 |

Personal-data pages per year sent abroad under H: 1051200

### 2b. Memo (at most 300 words)

To: Head of Operations. Recommendation: pipeline L.

**Who is served worst.** With H, Kazakh degraded scans: 0.767 (23/30, interval 0.591–0.882). With L, Russian degraded scans: 0.667 (20/30, interval 0.488–0.808). The overall figures (0.883 and 0.800) hide these cells. The intervals overlap and each cell has only 30 invoices, so I am not sure which pipeline is really worse there.

**Personal data.** In 32 % of pages an individual's name and ИИН are printed: 1,051,200 pages a year. ИИН is covered by Kazakhstan's law on personal data (No. 94-V).
- H: the scan goes to a data centre abroad (known). Who stores it and for how long is unknown. A vendor's statement is not a compliance review, so we must find out from the contract and a legal check whether this transfer is allowed.
- L: the scan stays on our server in Kazakhstan (known). We store it and we decide how long (known).

**Safeguards we can verify.**
- Delete scans and extracted data after 30 days; check the deletion log every month.
- The server has no outgoing internet; test it from the server.
- Only two named roles have access; review the access log.
- Pages with low confidence go to a person; count them every month.

**Choice.** I choose L. It costs $10,800 a year against $47,205, and no personal data leaves the country. Residual risk: L is less accurate, and in its worst cell about one invoice in three is wrong. We also become responsible for protecting the stored data. Before launch I would test more Russian degraded scans.

## Part 3: Explain your own numbers

### Q1

Number: 0.90
Why (at most 40 words): Characters grow only 1.13×, but bytes 2.25× (Cyrillic needs 2 bytes) and tokens 2.02×. Tokens grow slightly less than bytes, so the premium comes mostly from the encoding; the tokenizer only partly compensates.

### Q2

Number: 35.1
Why (at most 40 words): An English chunk is 789 e5 tokens, so the last 277 are cut. Russian (384) and Kazakh (228) fit under 512. The cut part is never embedded, so its content cannot be retrieved, and no error is shown.

### Q3

Number: 66.6
Why (at most 40 words): T only rescales scores: the ranking stays Monday, Friday, Sunday, holiday, Easter. All five tokens remain possible; low T just makes the top token much more likely. Removing tokens needs top-p or top-k.

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
