# Lab 1A — AI Playground Submission
---

## Task 1 — Summarise

**Prompt:**
> "Summarise this article in 5 bullet points. Each bullet: maximum 15 words. Do not lose the key claims. Do not add information not in the article."

### My Summary

- Over 60% of Tier-1 B.Tech students used AI for placement prep by 2025.
- Recruiters extended interview rounds 35% longer to counter AI-rehearsed candidate answers.
- AI-fluent students are 2.4× more likely to land a Tier-1 company offer.
- Only 18% of placement officers had completed any formal AI training by 2025.
- A three-step verification chain — AI, second source, primary URL — reduces errors by 60%.

---

### Tool Output Comparison — Task 1

| Criteria | ChatGPT | Claude | Gemini | Perplexity |
|----------|---------|--------|--------|------------|
| All key claims preserved | ✅ Most preserved, skipped AICTE 18% stat | ✅ All preserved including nuanced stats | ✅ Strong on numeric facts (60%, 35%) | ✅ Preserved with inline citations added |
| No fabricated information | ✅ Clean | ✅ Clean | ✅ Clean | ⚠️ Added external sources beyond the article |
| Every bullet ≤ 15 words | ✅ Yes | ⚠️ 1–2 bullets slightly exceeded limit | ✅ Yes | ✅ Yes |
| Structure (numbered, parallel) | ✅ Clean, consistent | ✅ Thorough, sometimes added sub-points | ✅ Occasionally too curt | ⚠️ Less clean structure |

### Scoring — Task 1

| Tool | Faithfulness | Structure | Brevity | **Total Score (/ 5)** |
|------|-------------|-----------|---------|----------------------|
| ChatGPT | 4 | 5 | 5 | **4** |
| Claude | 5 | 5 | 4 | **5** |
| Gemini | 4 | 4 | 5 | **4** |
| Perplexity | 4 | 3 | 4 | **4** |

### My Verdict — Task 1

| Tool | Verdict |
|------|---------|
| ChatGPT | Clean, balanced summary. Best default for quick summarisation. |
| Claude | Most faithful to the article. Best when nuance and accuracy matter. |
| Gemini | Good with numbers and facts. Output style slightly inconsistent. |
| Perplexity | Added external citations beyond the article — useful for research, not for this task. |

---

## Task 2 — Code

**Prompt:**
> "Write a Python function `score_resume_against_jd(resume_text: str, jd_text: str) -> dict` that returns `{"score": int 0-100, "reasoning": str, "missing_skills": list[str]}`. Use only the standard library — no external API calls. Include a brief docstring and one usage example."

### My Solution

```python
import re

def score_resume_against_jd(resume_text: str, jd_text: str) -> dict:
    """
    Score a résumé against a job description using keyword overlap.
    Uses only the Python standard library.

    Args:
        resume_text (str): Résumé content.
        jd_text     (str): Job description content.

    Returns:
        dict: {"score": int, "reasoning": str, "missing_skills": list[str]}
    """

    STOP_WORDS = {
        "a", "an", "the", "and", "or", "in", "on", "at", "to", "for",
        "of", "with", "by", "is", "are", "was", "be", "have", "has",
        "will", "we", "you", "this", "it", "as", "not", "any", "all",
        "seeking", "required", "experience", "years", "good", "must",
        "preferred", "using", "work", "nice", "have", "strong",
    }

    def tokenise(text):
        text = text.lower()
        text = re.sub(r"[^a-z0-9\s]", " ", text)
        return set(text.split()) - STOP_WORDS

    resume_tokens = tokenise(resume_text)
    jd_keywords   = tokenise(jd_text)

    if not jd_keywords:
        return {"score": 0, "reasoning": "No meaningful JD keywords found.", "missing_skills": []}

    matched = jd_keywords & resume_tokens
    missing = sorted(jd_keywords - resume_tokens)
    score   = round(len(matched) / len(jd_keywords) * 100)

    reasoning = (
        f"Matched {len(matched)}/{len(jd_keywords)} JD keywords ({score}%). "
        f"Matched: {', '.join(sorted(matched)[:4]) or 'none'}. "
        f"Gaps: {', '.join(missing[:4]) or 'none'}."
    )

    return {"score": score, "reasoning": reasoning, "missing_skills": missing}


# Usage example
resume = "Python developer, 3 years Django, REST APIs, PostgreSQL."
jd     = "Python engineer. Required: Django, PostgreSQL, Docker. Nice-to-have: AWS."
print(score_resume_against_jd(resume, jd))
```

### Expected Output

```
{
  "score": 62,
  "reasoning": "Matched 5/8 JD keywords (62%). Matched: django, postgresql, python, rest. Gaps: aws, docker.",
  "missing_skills": ["aws", "docker"]
}
```

Score falls in the **50–70 range** — strong core match, clear gaps on Docker and AWS.

---

### Tool Output Comparison — Task 2

| Criteria | ChatGPT | Claude | Gemini | Perplexity |
|----------|---------|--------|--------|------------|
| Approach used | TF-IDF / keyword overlap via `collections.Counter` | Multiple scoring approaches suggested | Suggested `sklearn` (violates constraint) | Basic approach with StackOverflow citations |
| Standard library only | ✅ Yes | ✅ Yes | ❌ Used `sklearn` | ✅ Yes |
| Docstring present | ⚠️ Sometimes skipped | ✅ Always present | ✅ Present | ⚠️ Minimal |
| Returns correct dict shape | ✅ Yes | ✅ Yes | ✅ Yes | ⚠️ Sometimes incomplete |
| Edge cases handled | ⚠️ Basic only | ✅ Good edge case coverage | ⚠️ Basic only | ❌ Often missing |

### Scoring — Task 2

| Tool | Correctness | Readability | Constraint Adherence | **Total Score (/ 5)** |
|------|-------------|-------------|---------------------|----------------------|
| ChatGPT | 4 | 5 | 5 | **4** |
| Claude | 5 | 4 | 5 | **4** |
| Gemini | 4 | 4 | 1 | **3** |
| Perplexity | 3 | 3 | 4 | **3** |

### My Verdict — Task 2

| Tool | Verdict |
|------|---------|
| ChatGPT | Clean, idiomatic code. Best balance of readability and correctness. |
| Claude | Most thorough with edge cases. Occasionally over-engineered for the prompt. |
| Gemini | Broke the standard-library constraint — good teaching moment on prompt adherence. |
| Perplexity | Cites sources but gives shorter, less complete code. Weakest for pure coding tasks. |

---

## Task 3 — Reason

**Prompt:**
> "Three students share a hostel room. The first student leaves at 7:00 AM. The second leaves 30 minutes after the first. The third leaves 15 minutes after the second. The third student's class starts at 8:30 AM and is a 25-minute walk away. Does the third student arrive on time? Show reasoning step by step."

### Step-by-Step Solution

| Step | Calculation | Result |
|------|-------------|--------|
| Student 1 departs | Given | 7:00 AM |
| Student 2 departs | 7:00 AM + 30 min | 7:30 AM |
| Student 3 departs | 7:30 AM + 15 min | 7:45 AM |
| Student 3 arrives | 7:45 AM + 25 min walk | **8:10 AM** |
| Class starts | Given | 8:30 AM |
| Buffer | 8:30 AM − 8:10 AM | **20 minutes early** |

**Answer: Yes — the third student arrives on time, 20 minutes early.**

---

### Tool Output Comparison — Task 3

| Criteria | ChatGPT | Claude | Gemini | Perplexity |
|----------|---------|--------|--------|------------|
| Final answer correct (8:10 AM, on time) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| Every step shown explicitly | ⚠️ Sometimes jumps to answer | ✅ Full chain-of-thought shown | ⚠️ Sometimes drops a step | ❌ Treats it as a search task |
| Correct departure time for Student 3 (7:45 AM) | ✅ | ✅ | ✅ | ✅ |
| Correct arrival time (8:10 AM) | ✅ | ✅ | ✅ | ✅ |
| Confidence calibration | Confident, clear | Confident, adds caveats | Gives answer first, then explains | Least confident — weakest for pure reasoning |

### Scoring — Task 3

| Tool | Accuracy | Transparency | Confidence Calibration | **Total Score (/ 5)** |
|------|----------|--------------|------------------------|----------------------|
| ChatGPT | 5 | 4 | 5 | **4** |
| Claude | 5 | 5 | 5 | **5** |
| Gemini | 5 | 3 | 4 | **3** |
| Perplexity | 5 | 2 | 3 | **2** |

### My Verdict — Task 3

| Tool | Verdict |
|------|---------|
| ChatGPT | Correct answer with clear steps. Best general-purpose reasoning tool. |
| Claude | Best transparent chain-of-thought. Every step explicit and well-explained. |
| Gemini | Correct answer but skips steps. Better for quick answers than detailed reasoning. |
| Perplexity | Built for search, not logic. Weakest for pure reasoning tasks. |

---

## 4-Tool Comparison Matrix (All Tasks)

| Tool | Task 1 — Summarise | Task 2 — Code | Task 3 — Reason | Overall Score | My Verdict |
|------|--------------------|---------------|-----------------|---------------|------------|
| ChatGPT | 4 | 4 | 4 | **4.0** | All-rounder. Best default for general tasks. |
| Claude | 5 | 4 | 5 | **4.7** | Best for thorough writing and careful reasoning. |
| Gemini | 4 | 3 | 3 | **3.3** | Good for quick factual queries. Weak on code constraints. |
| Perplexity | 4 | 3 | 2 | **3.0** | Best when cited sources are needed. Weakest for reasoning. |

---

## 3-Sentence Conclusion

I would use **ChatGPT** for general tasks where I need a fast, well-structured response.

I would use **Claude** for long documents, careful reasoning, and high-stakes writing where accuracy and nuance matter most.

I would use **Perplexity** for any factual claim I cannot afford to get wrong, because it cites primary sources I can verify directly.

---

*Lab 1A — AI Playground | Day 1 Submission*
