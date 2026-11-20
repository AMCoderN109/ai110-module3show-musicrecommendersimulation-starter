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

Top recommendations:

1. Sunrise City
   Score: 7.47
   Reasons:
   - genre match (+4.0)
   - mood match (+2.0)
   - energy similarity (+1.47)

2. Gym Hero
   Score: 5.30
   Reasons:
   - genre match (+4.0)
   - energy similarity (+1.30)

3. Rooftop Lights
   Score: 3.44
   Reasons:
   - mood match (+2.0)
   - energy similarity (+1.44)

4. Training Season
   Score: 1.48
   Reasons:
   - energy similarity (+1.48)

5. Despacito
   Score: 1.48
   Reasons:
   - energy similarity (+1.48)

### Adversarial Profile Results

The following output comes from running each profile against `recommend_songs` with `k=5`.

#### Conflicting Preferences

```text
Profile: {'genre': 'pop', 'mood': 'sad', 'energy': 0.9}
1. Gym Hero - 5.46 (genre match (+4.0); energy similarity (+1.46))
2. Sunrise City - 5.38 (genre match (+4.0); energy similarity (+1.38))
3. Storm Runner - 1.48 (energy similarity (+1.48))
4. How You Like That - 1.48 (energy similarity (+1.48))
5. Golden - 1.47 (energy similarity (+1.47))
```

#### Low-Energy Intense

```text
Profile: {'genre': 'rock', 'mood': 'intense', 'energy': 0.1}
1. Storm Runner - 6.29 (genre match (+4.0); mood match (+2.0); energy similarity (+0.28))
2. Gym Hero - 2.25 (mood match (+2.0); energy similarity (+0.25))
3. Spacewalk Thoughts - 1.23 (energy similarity (+1.23))
4. Library Rain - 1.12 (energy similarity (+1.12))
5. Coffee Shop Stories - 1.09 (energy similarity (+1.09))
```

#### High-Energy Chill

```text
Profile: {'genre': 'lofi', 'mood': 'chill', 'energy': 1.0}
1. Midnight Coding - 6.63 (genre match (+4.0); mood match (+2.0); energy similarity (+0.63))
2. Library Rain - 6.53 (genre match (+4.0); mood match (+2.0); energy similarity (+0.52))
3. Focus Flow - 4.60 (genre match (+4.0); energy similarity (+0.60))
4. Spacewalk Thoughts - 2.42 (mood match (+2.0); energy similarity (+0.42))
5. Gym Hero - 1.40 (energy similarity (+1.40))
```

#### Unknown Genre

```text
Profile: {'genre': 'classical', 'mood': 'happy', 'energy': 0.5}
1. Rooftop Lights - 3.11 (mood match (+2.0); energy similarity (+1.11))
2. Sunrise City - 3.02 (mood match (+2.0); energy similarity (+1.02))
3. Midnight Coding - 1.38 (energy similarity (+1.38))
4. Focus Flow - 1.35 (energy similarity (+1.35))
5. Calm Down - 1.32 (energy similarity (+1.32))
```

#### Unknown Mood

```text
Profile: {'genre': 'pop', 'mood': 'melancholic', 'energy': 0.8}
1. Sunrise City - 5.47 (genre match (+4.0); energy similarity (+1.47))
2. Gym Hero - 5.30 (genre match (+4.0); energy similarity (+1.30))
3. Training Season - 1.48 (energy similarity (+1.48))
4. Despacito - 1.48 (energy similarity (+1.48))
5. Espresso - 1.47 (energy similarity (+1.47))
```

#### Neutral Profile

```text
Profile: {'genre': '', 'mood': '', 'energy': 0.5}
1. Midnight Coding - 1.38 (energy similarity (+1.38))
2. Focus Flow - 1.35 (energy similarity (+1.35))
3. Calm Down - 1.32 (energy similarity (+1.32))
4. Coffee Shop Stories - 1.30 (energy similarity (+1.30))
5. The Door - 1.29 (energy similarity (+1.29))
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



