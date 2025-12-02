> # Naive Bayes and Probability Concepts
---
## 1. Events

**Definition:**  
An **event** is something that may happen or not happen in a random experiment.

- **Example:** Tossing a coin → getting "Heads" is an event.
- Multiple events: "Getting an even number" when rolling a die.

**Types of events:**

- **Independent events:** The occurrence of one does **not affect** the other.  
  - Example: Tossing two coins.  
  - Mathematically:  
    \[
    P(A \cap B) = P(A) \cdot P(B)
    \]

- **Dependent events:** The occurrence of one **affects** the probability of the other.  
  - Example: Drawing 2 cards from a deck **without replacement**.

- **Mutually exclusive events:** Cannot happen together.  
  - Example: Rolling a 3 and a 5 at the same time with one die.  
   \[
    P(A \cap B) = 0
    \]

## 2. Probability of an Event

**Definition:**  
Probability measures the **likelihood** of an event happening.  

\[
P(A) = \frac{\text{Number of favorable outcomes}}{\text{Total number of outcomes}}
\]

- Example: Tossing a die, probability of rolling 4:  
\[
P(4) = \frac{1}{6}
\]

## 3. Conditional Probability

**Definition:**  
The probability of an event \(A\) **given** that another event \(B\) has occurred.  

\[
P(A|B) = \frac{P(A \cap B)}{P(B)}
\]

- **Example:**  
  - Deck of 52 cards. Event \(A\) = draw an Ace, \(B\) = draw a Spade.  
  - There is 1 Ace of Spades and 13 Spades total.  
\[
P(A|B) = \frac{1}{13}
\]

- **Intuition:** "If I know B happened, how likely is A now?"

## 4. Bayes’ Theorem

Bayes’ theorem **reverses conditional probabilities**.  

\[
P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}
\]

- \(P(A)\) = prior probability of A  
- \(P(B|A)\) = likelihood of B given A  
- \(P(B)\) = probability of B  
- \(P(A|B)\) = posterior probability (updated probability after seeing B)

**Example:**  
- Disease test:  
  - 1% of people have a disease (\(P(D) = 0.01\))  
  - Test is 99% accurate: \(P(\text{Positive}|D) = 0.99\), \(P(\text{Positive}|\neg D) = 0.01\)  
- Probability that someone **has the disease given a positive test**?  

\[
P(D|\text{Positive}) = \frac{0.99 \cdot 0.01}{0.99\cdot0.01 + 0.01 \cdot 0.99} = 0.5
\]

## 5. Naive Bayes Classifier

Naive Bayes is a **probabilistic classifier** based on **Bayes’ theorem** and the **assumption of feature independence**.

**Problem:** Given features \(X = (x_1, x_2, ..., x_n)\), classify into class \(C\).  

\[
P(C|X) = \frac{P(X|C) \cdot P(C)}{P(X)}
\]

- **Naive assumption:** Features \(x_1, x_2, ..., x_n\) are **conditionally independent** given the class.  
\[
P(X|C) = P(x_1|C) \cdot P(x_2|C) \cdot ... \cdot P(x_n|C)
\]

- So:
\[
P(C|X) \propto P(C) \cdot \prod_{i=1}^{n} P(x_i|C)
\]

- **Classify by:**  
\[
\hat{y} = \arg\max_{C} P(C) \cdot \prod_{i=1}^{n} P(x_i|C)
\]

## 6. Types of Naive Bayes

1. **Gaussian Naive Bayes:**  
   - For **continuous features** assuming normal distribution.  
   - \[
     P(x_i|C) = \frac{1}{\sqrt{2\pi\sigma_C^2}} e^{-\frac{(x_i - \mu_C)^2}{2\sigma_C^2}}
     \]

2. **Multinomial Naive Bayes:**  
   - For **count data** (e.g., word counts in text classification).  
   - \[
     P(x_i|C) = \frac{\text{count of word } i \text{ in class C}}{\text{total words in class C}}
     \]

3. **Bernoulli Naive Bayes:**  
   - For **binary features** (presence/absence).  
   - \[
     P(x_i|C) = P(\text{word i present}|C)
     \]

4. **Complement Naive Bayes:**  
   - Improves Multinomial NB for **imbalanced datasets** by using stats from **other classes**.
