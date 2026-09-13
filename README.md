# 303

# MoodPulse by 303

Team: Lee Shei Hui, New Zhi Xuan, Valerie Chia Xin Hui 

Problem Statement: Stress & Workload Manager

Video Presentation: [Unlisted Youtube Link] 

Presentation Slides:  https://canva.link/ttubz4chef0js6n

# 1. Project Overview

Our group chose Stress and Workload Manager as our topic. We understand that university students have multiple priorities to take care of, that includes academics, physical and mental health, as well as their social life! That’s a lot to handle at one go, and may lead to severe consequences, such as burnout, if not handled well. But overcoming burnout isn’t just about resting more, it’s about visualising tasks, deadlines, and tracking your health status. We may see similar apps that are already on the market, such as YPT. While it allows users to track their time usage and to do lists, there aren’t any features to remind the user of when their workload may be too heavy. Users can continue adding to-do’s and lose track of their stress level and mental status. In the long term, the user may put themselves in a constant tense state.


Our solution: Our app provides direct access to time management, task management, health tracking and live chatbot all in one! It allows the user to plan their week, manage assignments and projects, as well as track how recent events have been affecting their mood and health status. If the system detects that the user may be overloaded with work or detects that the user’s health status is exceeding normal range, it sends encouragement messages, reminds the user to rest, or take out unnecessary tasks. 


# 2. Ideation & Process

2.1 Ideas We Considered
   
Table of every distinct idea generated, with why each was kept or dropped, order it so that chosen ideas are listed first
| Idea | Why it was dropped/kept |
|------|-----|
| To do list (chosen) | It was related to our theme to help manage workload | 
| Health status (chosen) | One of the main feature of our app to monitor stress levels | 
| Mood diary (Chosen) | Allow users to record their day |
| Timetable (chosen) | Helps user to keep track of their schedule to avoid cram sessions and prevent burnout |
| Live chatbox | Acts as a companion to the user so they won't feel lonely, users can also interact and talk to their companion via this chatbox |
| Study timer | Didn't relate to our app's theme of stress and workload management |
| Daily check-in messages | Users might find it bothersome to spend 5-10 minutes doing this check in |
| Music library/background music | Other apps such as Spotify and Apple Music is already available to use, some users might prefer those apps too |

2.2 Ideation Boards
You can embed the images directly (recommended) or have links to your ideation board. Don’t feel forced to add as many diagrams as you can for “more marks”. The reviewers want to know how your team put your minds together to create your solution. It can be messy, with a lot of small dropped ideas. Add 1–2 lines under each explaining what it shows.

IMPORTANT: You can express this in any way you like, including but not limited to:
Mindmaps
Problem trees
Flowcharts
User flows
Crazy eights
Affinity diagrams
SCAMPER grids
Fishbone diagrams
5 Whys chains
Any other scribbles :)
You can embed images in markdown like so:
![Mindmap](mindmap.png)

2.3 Mentor Consultation
| Date | Mentor | Feedback Received | What was changed |
|------|-----|
| 3rd September | Zack Khong | Advised us to focus more on the health status feature of our app | Updated our health status function and focused on that more |


Even if you disagreed with a piece of feedback, you can say so and explain why. You will not be penalised for doing something against a mentor’s advice, it will still count as engaging with it.

# 3. Design & Prototype
UI Prototype: [ Public Link ]
Check that it opens in an incognito window. This can be a link to Figma, Canva, Netlify, Vercel or any other board where you showcase your UI. It can be clickable with hyperlinks or simply ordered screenshots.
We recommend you embed or link 4–8 key screens as images, with a caption on each explaining the interaction

# 4. What Makes It Different

While our app provides typical features of a stress and workload manager, there are a few distinctions from them:

- Our app provides encouragement to the user if the system detects they have been feeling down for quite some time. 
- It also reminds the user to rest or take out unnecessary tasks if the system detects high level workload or unusual data from the health status report.
- The user can connect the app to their smartwatch to track their heart rate, steps, blood pressure etc.


Overall, our objective is to visualize tasks, and time management, while also reminding them when they might be overloaded, providing them with a clear vision of potential risks that may cause burnout and give a suitable recommendation. 


# 5. Technical Architecture & Feasibility

1. Tech stack
   --------------

Since our team has only beginner-level Python and HTML experience, we picked the simplest option that still lets us demo the core loop, rather than the most "correct" production.

Frontend

- HTML, CSS, and vanilla JavaScript.

- Why: it's the one web technology all three of us already have some exposure to, so we spend our limited time building screens instead of learning a framework.

- Constraint: no framework means more manual work for things like page navigation and reusable components. We'll keep the number of screens small (see Build Plan) to keep this manageable.


Backend

- Python with Flask.

- Why: Flask is a very small, beginner-friendly framework. Since Python is the language we're most comfortable with, this lets us reuse what we already know instead of learning a second backend language.

- Constraint: Flask's built-in server isn't meant for real production traffic, but that's fine — we only need it to run reliably for a demo, not at scale.

Database

- Firebase Firestore (free tier).

- Why: no server setup required, has a simple Python SDK, and the free tier is enough for hackathon-scale data

- Constraint: Firestore's free tier has daily read/write limits, and its query rules take some learning. As a fallback, we can swap this for a local SQLite file or even a plain JSON file if Firebase setup eats into build time — the app's logic doesn't depend on which storage we use.

APIs / services

- Chatbot: rather than building real NLP, we'll use a hosted LLM API (e.g. OpenAI's API, which offers free trial credit) for the live chat feature.

- Constraint: this needs an API key, which must never be exposed in frontend code — it has to be called from our Flask backend, not directly from the browser. If API cost/setup time becomes a blocker, our fallback is a small set of scripted/rule-based responses (e.g. keyword-triggered replies) that still demo the "talk to your avatar" concept without a live model.

Health tracking (sleep, steps, Apple Watch sync): true HealthKit/Apple Watch integration requires a paid Apple Developer account and native iOS development, which is out of scope for our skill level and timeframe.

- Our plan: simulate this with manual input fields (the user types their sleep hours, step count, etc.) for the prototype, and list real wearable integration as future work.

Hosting

- Frontend: GitHub Pages (free, static hosting, simple to deploy from a repo).


- Backend: Render or PythonAnywhere free tier (both support Flask apps with minimal configuration).

- Constraint: free-tier backends can be slow to "wake up" after inactivity (cold starts). We'll account for this in our demo by keeping the app open/warm before presenting.


3. Build plan & scope
   -------------------
Given three beginner developers and a short build window, we're deliberately narrowing scope to a working core loop rather than all five features from our pitch deck. This is what we plan to actually build:

1. Must-build (core demo):

- To-do list with manual task entry, categories, and a done/undo toggle
- Daily mood/stress check-in (simple 1–5 scale, stored per day)
- A basic "capacity" dashboard that combines task load + mood entries into one summary number/view

2. Build if time allows:

- Timetable view (static week grid, manually entered classes/events)
- Rule-based recovery nudge (e.g. "if 3+ high-stress days logged this week, show a rest reminder")
- Chatbot screen, using scripted responses first, upgraded to a live API call if time and budget allow

3. Explicitly out of scope for this prototype (documented as future work):

- Real Apple Watch / HealthKit integration
- Live AI chatbot with full conversational memory
- Avatar/companion customization and unlockables
- Push notifications / native mobile app
