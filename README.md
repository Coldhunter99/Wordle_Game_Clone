# Wordle_Game_Clone
An implementation of Wordle in Python than can be played via the terminal.

# Wordle Game Rules:
Wordle is such a simple game that there are hardly any rules. But here we go:

1. We have to guess the Wordle in six goes or less
2. Every word we enter must be in the word list. There are more than 10,000 words in this list, but only 2,309 (at the time of writing) are answers to a specific puzzle
3. A correct letter turns green
4. A correct letter in the wrong place turns yellow
5. An incorrect letter turns gray
6. Letters can be used more than once

# Build and Run:
Clone the repository and Run on local terminal.

# Problem/Bug
For example, if the guess is HELLO and the secret is APPLE, then the previous behavior causes the first occurrence of the L to be yellow (because it does appear in the word), but then the second L will be green (because it is in the right position).

On a letter-by-letter basis, this behavior appears fine. But when the entire word is considered, that first L shouldn't appear yellow. Instead, it should appear grey. That's because there is already another L in the guess that 'claims' the occurrence of the L in the secret.

# Solution
Instead of resolving all the letter results in one-pass, we now first initialize it as an array and default all guess letters to grey (not in the word).
We create an list, which is a copy of the secret. Each element corresponds to the letter in the string. For example ["A", "P", "P", "L", "E"].
We then do a first pass through the guess, and identify any letters in the correct position. If we find one, then that letter becomes 'green', and the secret list is updated to void out that letter so it can't be used in a subsequent comparison. So if we guess "HELLO", the remaining secret becomes something like this: ["A", "P", "P", "*", "E"].
We then do another loop this time identify the guessed letters which are in the word (by using a nested loop), but not in position.
