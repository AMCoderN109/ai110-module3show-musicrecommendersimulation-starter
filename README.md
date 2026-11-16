# 🎵 Music Recommender Simulation

## Project Summary

In this project you will build and explain a small music recommender system.

Your goal is to:

- Represent songs and a user "taste profile" as data
- Design a scoring rule that turns that data into recommendations
- Evaluate what your system gets right and wrong
- Reflect on how this mirrors real world AI recommenders

Replace this paragraph with your own summary of what your version does.

---

## How The System Works

Explain your design in plain language.

Some prompts to answer:

- What features does each `Song` use in your system
  - For example: genre, mood, energy, tempo
- What information does your `UserProfile` store
- How does your `Recommender` compute a score for each song
- How do you choose which songs to recommend

Our design would be a little less complicated compared to how real-world recommendations work. Our music recommender will focus mainly on songs that match the user's favorite mood and energy level. It will also focus on the genre and acoustic levels of the music, but those are the main focus. As for how the scoring process works, when a song's mood or even genre matches the user's preferences, we give points to it. Also, when a song's energy is close to the user's chosen energy level, it will provide a higher score. So, with this scoring process, our system sorts the songs, gathers the ones with the highest scores, and recommends them to users. 

You can include a simple diagram or bullet list if helpful.

=============================================================================
                          RECOMMENDER DATA FLOW MAP
=============================================================================

  [ INPUT ] --------> [ PROCESS (THE LOOP) ] --------> [ OUTPUT ]
  • User Profile        For every track in CSV:         • Sort by Total Score
  • songs.csv           1. Check Genre  (+4.0)          • Slice Top K Songs
                        2. Check Mood   (+2.0)          • Display Recommendations
                        3. Calc Energy  (0.0 - 1.5)
                        4. Check Acousticness (+1.75)
                        5. Sum Points
=============================================================================

### Potential Biases

- Genre has the most points, so exact genre matches may dominate the results.
- Different genre labels may cause similar songs to be treated as unrelated.
- Common genres may be recommended more often than less-represented genres.
- A narrow user profile may limit variety in the recommendations.
- The small dataset may not represent all types of music.


---

## Getting Started

### Setup

1. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # Mac or Linux
   .venv\Scripts\activate         # Windows

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Run the app:

```bash
python -m src.main
```

### Running Tests

Run the starter tests with:

```bash
pytest
```

You can add more tests in `tests/test_recommender.py`.

---

## Sample Recommendation Output

Paste a sample of your recommender's output here as a text block so a reader can see what it produces:

```
# e.g.:
# User profile: genre=indie, mood=chill, energy=low
# Recommendations:
#   1. ...
#   2. ...
#   3. ...
```

**Screenshot or video** *(optional)*: <!-- Insert a screenshot or demo video link here -->

---

## Experiments You Tried

Use this section to document the experiments you ran. For example:

- What happened when you changed the weight on genre from 2.0 to 0.5
- What happened when you added tempo or valence to the score
- How did your system behave for different types of users

---

## Limitations and Risks

Summarize some limitations of your recommender.

Examples:

- It only works on a tiny catalog
- It does not understand lyrics or language
- It might over favor one genre or mood

You will go deeper on this in your model card.

---

## Reflection

Read and complete `model_card.md`:

[**Model Card**](model_card.md)

Write 1 to 2 paragraphs here about what you learned:

- about how recommenders turn data into predictions
- about where bias or unfairness could show up in systems like this



