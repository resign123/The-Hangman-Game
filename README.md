# The Hangman Game

This project explores advanced decision-making strategies for a Hangman player, focusing on the interplay between entropy-based and frequency-based approaches. The goal is to maximize accuracy and minimize errors by implementing intelligent word filtering and letter selection methods.

## Strategies Implemented

### 1. Entropy-Based Filtering
**Logic:**

- Utilizes entropy as a measure of uncertainty to filter potential word matches from the dictionary.
- When there are too many options left in the dictionary for pattern matching and time is running out, instead of relying on frequency-based guessing, the strategy switches to entropy. It selects the letter that provides the maximum information to help shorten the search space.
- Entropy formula:

  \[
H
(
X
)
:=
−
∑
x
∈
X
p
(
x
)
log
⁡
p
(
x
)
  \]
  
- Each guess aims to maximize information gain by reducing the uncertainty in the remaining words.

**Result:**
- **Accuracy:** 53.2%
- **Observations:** This strategy efficiently reduces the search space but struggles with precision in the initial guesses, which affects overall performance.

### 2. Entropy with ETAOINSHRDLU Guesses
**Logic:**

- Combines entropy-based filtering with the ETAOIN frequency order for initial guesses. ETAOINSHRDLU represents the most common letters in English: E, T, A, O, I, N, S, H, R, D, L, U, etc.
- In the beginning, when there is limited information, the strategy prioritizes frequent letters. If a particular letter appears in most of the matching words without wasting any guess, that letter is selected based on the priority order of the most common letters (ETAOINSHRDLU).
- Initial guesses prioritize frequent letters, and then the strategy transitions to entropy calculations for word filtering.

**Result:**
- **Accuracy:** 54.6%
- **Observations:** This approach improves reliability in early guesses by leveraging the inherent frequency of letters in English, leading to slightly better performance than pure entropy-based filtering.

### 3. Weighted Frequency and Entropy
**Logic:**

- Integrates a weighted combination of frequency and entropy to determine guesses.
- The goal is to eliminate the search space more effectively by using both frequency and entropy. 
- The formula used is:

  \[
  Weighted Entropy=H × 
Total Words/
Freq

  \]
 where 
𝐻
H is the entropy, and 
Freq
Freq is the frequency of the letter in the filtered dictionary.
- Prioritizes letters that are both frequent and provide a significant reduction in uncertainty.

**Result:**
- **Accuracy:** <50%
- **Observations:** Overemphasis on letter frequency diluted the effectiveness of entropy-based filtering, leading to suboptimal guesses and poorer performance.

### 4. Weighted Entropy with ETAOINSHRDLU Guesses
**Logic:**

- Starts with ETAOINSHRDLU guesses for the first few turns to improve early-game reliability.
- Then transitions to weighted entropy calculations, combining frequency and entropy for subsequent turns.

**Result:**
- **Accuracy:** 51.3%
- **Observations:** The combination of frequency-based initial guesses and weighted entropy provided slight improvements over pure weighted entropy but did not outperform pure entropy or entropy + ETAOIN strategies.

## Observations and Conclusion

While entropy-based filtering proved crucial in reducing ambiguity, frequency-driven decisions provided a reliable fallback. Weighted entropy approaches, though theoretically sound and complex, underperformed due to the overemphasis on letter frequency, which diminished information gain.

