# Day2_SixPatterns.md

## Student Question

**"Explain SQL vs NoSQL databases for a placement interview."**

---

# Pattern 1 — PERSONA

### Prompt Used

> You are a senior database faculty mentor at an engineering college in Andhra Pradesh. You have trained over 300 B.Tech CSE students for placement interviews in Wipro, TCS, and Accenture. A final-year student preparing for technical interviews asks about SQL vs NoSQL databases. Explain it like a 1-on-1 placement mentoring session using practical examples from apps students already know.

### Best Output

Think of **SQL** as a neatly organized college attendance register — fixed rows and columns, structured, and consistent. Databases like MySQL and PostgreSQL follow this model.

**NoSQL** is more flexible, like WhatsApp chats or Instagram posts where data structure keeps changing. MongoDB stores data without requiring strict tables.

In placements, remember this line: **SQL = structured + relationships, NoSQL = flexible + scalability**.

### Self-Score (1–5)

**5/5**

### Peer-Score (Out of 10)

| Criterion    | Score |
| ------------ | ----- |
| Clarity      | 2     |
| Context      | 2     |
| Specificity  | 2     |
| Format       | 1     |
| Verification | 1     |

**Total: 7/10**

---

# Pattern 2 — FEW-SHOT

### Prompt Used

> Here are example explanations from a placement coach:
>
> Q: What is an API?
> A: API is like a waiter in a restaurant. You order food, the waiter takes your request to the kitchen and brings back the result.
>
> Q: What is cloud computing?
> A: Using servers over the internet instead of your own computer. Like storing photos in Google Drive instead of your laptop.
>
> Q: What is SQL vs NoSQL?
> A:

### Best Output

SQL databases store data in structured tables with fixed columns — like an Excel sheet. NoSQL databases are flexible and can handle changing formats, like social media posts with different content types.

Example: **Banking systems prefer SQL** because relationships and consistency matter. **Netflix or Instagram may use NoSQL** for huge, changing data.

### Self-Score (1–5)

**4/5**

### Peer-Score (Out of 10)

| Criterion    | Score |
| ------------ | ----- |
| Clarity      | 2     |
| Context      | 1     |
| Specificity  | 2     |
| Format       | 2     |
| Verification | 1     |

**Total: 7/10**

---

# Pattern 3 — CHAIN-OF-THOUGHT

### Prompt Used

> Explain SQL vs NoSQL to a placement interview candidate. Think step by step before answering.
>
> Step 1: Define SQL and NoSQL in one sentence.
> Step 2: Give one real-world example for each.
> Step 3: Explain when to choose one over the other.
> Step 4: Summarise in 3 interview-ready sentences.

### Best Output

### Step 1: Definition

SQL databases use structured tables and predefined schemas, while NoSQL databases handle flexible or unstructured data.

### Step 2: Examples

A **bank management system** commonly uses SQL because transactions require accuracy.

An **e-commerce recommendation system** may use NoSQL because product and customer data change frequently.

### Step 3: When to Choose

Choose SQL when consistency and relationships matter. Choose NoSQL when scalability and flexibility matter.

### Step 4: Summary

SQL databases are structured and ideal for relational data. NoSQL databases are flexible and better for massive, rapidly changing data. In interviews, explain the **use case difference** rather than saying one is better.

### Self-Score (1–5)

**5/5**

### Peer-Score (Out of 10)

| Criterion    | Score |
| ------------ | ----- |
| Clarity      | 2     |
| Context      | 1     |
| Specificity  | 2     |
| Format       | 2     |
| Verification | 1     |

**Total: 8/10**

---

# Pattern 4 — STRUCTURED OUTPUT

### Prompt Used

> Explain SQL vs NoSQL for a placement interview. Return ONLY valid JSON with this exact shape — no markdown fences, no commentary:
>
> {
> "definition": "one-sentence definition",
> "real_world_analogy": "simple analogy",
> "comparison_example": "practical example",
> "common_mistake": "what students misunderstand",
> "interview_followup": "question interviewer may ask"
> }

### Best Output

```json id="yyhq4r"
{
  "definition": "SQL databases use structured relational tables while NoSQL databases support flexible data models.",
  "real_world_analogy": "SQL is like an attendance register with fixed columns, while NoSQL is like social media content that changes format.",
  "comparison_example": "Banking systems commonly use SQL; recommendation systems and social media platforms often use NoSQL.",
  "common_mistake": "Students incorrectly assume NoSQL is always better than SQL.",
  "interview_followup": "When would you choose MongoDB instead of MySQL?"
}
```

### Self-Score (1–5)

**5/5**

### Peer-Score (Out of 10)

| Criterion    | Score |
| ------------ | ----- |
| Clarity      | 2     |
| Context      | 1     |
| Specificity  | 2     |
| Format       | 2     |
| Verification | 1     |

**Total: 8/10**

---

# Pattern 5 — SYSTEM PROMPT

### System Prompt Used

> You are a placement trainer for B.Tech CSE students preparing for service-based company interviews in India. Explain technical concepts in under 80 words using relatable examples and interview-focused language.

### User Prompt

> Explain SQL vs NoSQL.

### Best Output

SQL databases store data in fixed tables and are great for structured applications like banking systems. NoSQL databases are flexible and useful for apps with changing data like Instagram feeds. In placements, remember: **SQL for relationships and consistency, NoSQL for scalability and flexibility**.

### Self-Score (1–5)

**4/5**

### Peer-Score (Out of 10)

| Criterion    | Score |
| ------------ | ----- |
| Clarity      | 2     |
| Context      | 2     |
| Specificity  | 2     |
| Format       | 1     |
| Verification | 0     |

**Total: 7/10**

---

# Pattern 6 — PROMPT CHAINING

## Conversation 1 (Extract)

### Prompt Used

> List the 5 most important sub-concepts a B.Tech student must understand about SQL vs NoSQL databases. Just the list, no explanation.

### Output

1. What SQL databases are
2. What NoSQL databases are
3. Key differences between SQL and NoSQL
4. Real-world applications of each
5. Interview questions commonly asked

---

## Conversation 2 (Expand)

### Prompt Used

> For each of these 5 sub-concepts of SQL vs NoSQL, write a 1-paragraph explanation tailored to a final-year B.Tech CSE student preparing for placements.

### Output Summary

Five detailed placement-oriented explanations with practical industry examples.

---

## Conversation 3 (Polish)

### Prompt Used

> Synthesise these 5 paragraphs into ONE concise 80-word placement-prep explanation of SQL vs NoSQL. Preserve all 5 sub-concepts. Conversational tone. End with one practice question.

### Final Output

SQL databases use structured tables and are best for applications requiring relationships and consistency, like banking systems. NoSQL databases are flexible and better for rapidly changing, large-scale data such as social media platforms. Learn their differences, real-world uses, and when to choose each because placement interviewers frequently ask scenario-based questions.

**Practice Question:** Why might Netflix prefer NoSQL in some systems?

### Self-Score (1–5)

**5/5**

### Peer-Score (Out of 10)

| Criterion    | Score |
| ------------ | ----- |
| Clarity      | 2     |
| Context      | 2     |
| Specificity  | 2     |
| Format       | 2     |
| Verification | 1     |

**Total: 9/10**

---

# Reflection

For placement-prep students, I would use **Persona** and **Prompt Chaining** most often. Persona helps tailor explanations to student level and interview context, making technical topics easier to understand. Prompt Chaining is useful for complex concepts because breaking them into smaller steps gives clearer and more complete answers than one long prompt.
