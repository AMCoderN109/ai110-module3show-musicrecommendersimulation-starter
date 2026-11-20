# 🎧 Model Card: Music Recommender Simulation

## 1. Model Name  

Give your model a short, descriptive name.  
Example: **VibeFinder 1.0**  

Sonic Mix 1.0
---

## 2. Intended Use  

Describe what your recommender is designed to do and who it is for. 

Prompts:  

- What kind of recommendations does it generate  
- What assumptions does it make about the user  
- Is this for real users or classroom exploration  

My recommendar is designed to generate a ranked list of sings that match preferred genre, mood, and energy. The program assumes users express taste through genre, mood, and a range target energy level. The program is also designed for classroom exploration, not real world use at the moment. 

---

## 3. How the Model Works  

Explain your scoring approach in simple language.  

Prompts:  

- What features of each song are used (genre, energy, mood, etc.)  
- What user preferences are considered  
- How does the model turn those into a score  
- What changes did you make from the starter logic  

Avoid code here. Pretend you are explaining the idea to a friend who does not program.

The song features that are used are genre, energy level, and mood. The user preference that are considered are the genre, mood and the energy levels they want to request. How the modle turns the preferences into a score, is by giving points when a song matches the user's prefer genre or mood, then add points based on how close the song's engery is also the user's prefer energy level. The song with the most points will be show at the top of the list. The changes we did make form the starter logis is update genre points from 4 to 2 points, while change energy level points from 1.5 to 3. Leaving mood points the same. 

---

## 4. Data  

Describe the dataset the model uses.  

Prompts:  

- How many songs are in the catalog  
- What genres or moods are represented  
- Did you add or remove data  
- Are there parts of musical taste missing in the dataset  

The recommender uses a dataset of 20 songs. Each song includes a title, artist, genre, mood, energy level, tempo, valence, danceability, and acousticness. The dataset is very small and covers only a limited number of genres and moods, so it may not represent the full variety of music users prefer. For the sensitivity experiment, we changed the scoring weights: genre matching decreased from 4 points to 2 points, while energy similarity increased from a maximum of 1.5 points to a maximum of 3 points. The dataset itself was not changed.

---

## 5. Strengths  

Where does your system seem to work well  

Prompts:  

- User types for which it gives reasonable results  
- Any patterns you think your scoring captures correctly  
- Cases where the recommendations matched your intuition  

The program works well for users who give the program very clear perferences on their genre and mood. The program will correctly favor songs that are closely match the user's target energy level they request. One case that recommendation matech my intuition is the chill lofi profile because it recommended me Midnight Coding and Library Rain, which matches the genre and mood. 

---

## 6. Limitations and Bias 

Where the system struggles or behaves unfairly. 

Prompts:  

- Features it does not consider  
- Genres or moods that are underrepresented  
- Cases where the system overfits to one preference  
- Ways the scoring might unintentionally favor some users  


The program weaknesses is, one it does not represent most of the music genres that exist, such as country and classical, because the 20-song dataset contains only a small selection of genres and moods. So if a user who perfers or asks for an underrepresented genre will receive less to none genre matches. Another weekness is the scoring system also over-prioritized genre before the experiment, although doubling energy and halving genre produced limited visible ranking changes because exact genre and mood matches remained influential. The energy-gap formula may favor users near the middle of the 0–1 energy scale and give no energy points when a song differs by 1.0 or more. 
---

## 7. Evaluation  

How you checked whether the recommender behaved as expected. 

Prompts:  

- Which user profiles you tested  
- What you looked for in the recommendations  
- What surprised you  
- Any simple tests or comparisons you ran  

No need for numeric metrics unless you created some.

I tested a high-energy pop profile and a chill lofi profile. I looked for whether the recommendations matched the requested genre, mood, and energy. The pop profile recommended Gym Hero and Sunrise City, while the lofi profile recommended Midnight Coding and Library Rain. This difference was expected because each profile has a different genre and mood.

One surprise was that Gym Hero kept appearing for profiles that wanted uplifting or happy pop music. Gym Hero matches pop and high energy, but the recommender does not fully understand whether a song is happy or intense. Comparing the two profiles showed that changing the genre and mood changed the recommendations clearly.

---

## 8. Future Work  

Ideas for how you would improve the model next.  

Prompts:  

- Additional features or preferences  
- Better ways to explain recommendations  
- Improving diversity among the top results  
- Handling more complex user tastes  

additonal featues that could be added to the program are tempo, valence, danceability, and acousticness. Another way to improve this program is to add more diversity to the type of genere that were include like jazz, classical, and more. 

---

## 9. Personal Reflection  

A few sentences about your experience.  

Prompts:  

- What you learned about recommender systems  
- Something unexpected or interesting you discovered  
- How this changed the way you think about music recommendation apps  

I learned that recommender systems rank songs using points from features such as genre, mood, and energy. I found it interesting that changing the scoring weights did not create much variety in the recommendations. This project showed me that music recommendation is more complicated than I expected and that features that seem small can affect the results.