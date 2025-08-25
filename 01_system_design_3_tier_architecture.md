# 3 tier architecture

## ChatGPT:
- What 3-Tier Architecture Is
  - A software architecture pattern that splits an application into three logical layers:
    - Presentation layer (UI) – what the user sees and interacts with (web app, mobile app, etc.).
    - Application / business logic layer – the “brains” that process requests, enforce rules, and make decisions.
    - Data layer – databases or data storage where information is saved and retrieved.
- Why It’s Used
  - Separation of concerns: each layer has a distinct responsibility.
  - Scalability: you can scale layers independently (e.g., add more app servers without touching the database).
  - Maintainability: easier to update or swap out one layer without breaking everything.
  - Security: the database isn’t exposed directly to users.
- Typical Real-World Setup
  - Presentation layer → Browser or mobile app. Could be HTML/CSS/JS or a React frontend.
  - Application layer → A backend service (Node.js, Java Spring, Ruby on Rails, etc.) that processes logic.
  - Data layer → SQL/NoSQL database (PostgreSQL, MongoDB, etc.).
- Example request flow:
  - User clicks "Buy" → Frontend sends request → Backend checks stock, updates DB → Response sent back to frontend → User sees confirmation.
- Likely Topics You’ll Learn Today
  - How data flows between tiers (request/response cycle).
  - Examples of implementation in web systems.
  - Advantages & disadvantages vs. other architectures (e.g., monoliths, 2-tier, microservices).
  - Where it shows up in modern systems (almost everywhere — from small apps to enterprise setups).

## Day 1!

Schedule:

- 3 guest speakers next week. Capstone almuni with years of experience.
- week 3 was DSA, now it's AWS
  - AWS is often used a lot in the capstone project.
  - If you want to take the AWS associate architect exam, you'll be 70% ready. You shouldn't do that instead of the jobhunt, but, it will improve your CV. It's like AI in that respect.
  - Week 4: Max. The main LSbot developer.
  - Week 5 React
    - front end scaling
    - back end scaling
  - Week 6 there is a project -> take-home project
    - weeks 6 - 8 multiple take-home projects.
    - Week 7 + 8:
    - Live interview questons:
      - different/ shorter, like LS216, but not a PEDAC program, but maybe pair programming on a React application live.
  - from week 7 schedule changes. Afternoon sessions also.
    - Wednesday - Thursday: project ideation => exploring differnt possible topics for capstone project
  - week 8: Receive project mentor, until week 16.
  - from week 9 we don't have synchronous sessions.
- Week 13: project implementation is like a full-time job. There are no other demands on your time. 
  - In theory the project should be done at the end of week 15. Tehre is some wiggle room though. Sometimes it bleeds into week 17.
- Thanksgiving break => November
- ... case aftefacts

Q: should we take notes? Not really -> we get cheat sheets.
### Hours
- 6 hours a day is too little, 10 hours a day is too much.
- It depends on how easy you find it.
- 
### JIT learning

### comparison

- don't compare. Don't feel like you're the worst person ever. Instead of this you should compare yourself with your previous self.
- Write down how much you know about [topic] and then after 2 weeks write down how much you know then.

### Zooming out 

- filling out fog of war
- a lot of these concepts haven't changed in 40 years
- The goal of the next 2 weeks is conceptual. Filling in your map of distributed systems.
- It's helpful to talk a lot and discuss. 

-tangent questions:
  sometimes good, sometimes bad. Don't ask about putting a jet-engine in a mini-van
  - Questions will be directed to teams, rather than iterators.

- keep up
- Try to learn from a point of excitement, not a point of fear.
  - This is a useful tip for interviews.
  - You don't know everything. Of course you'll make mistakes, but be positive.

### Introduction
- if the application and code-level concerns are Earth, we're going to be zooming out and learning about the solar system. The solar system is the distributed system that supports the application.
- we'll learn through lots of conversation and discussion. Please ask questions!
- please default to having your video on, this helps facilitate conversation.
we'll have lots of homework, but think about it like a buffet.
- There are some things we definitely want you to eat, but you don't need to "finish" the buffet.
- This is not mastery-based learning. You're going for the gist of the material, learning enough to let you move forward.
We'll have homework for each learning type. Lots of reading, videos, and doing.
- lean into learning. Try to approach learning from a position of curiosity and excitement, not fear or anxiety. There are no assessments.

### 2 Main Goals during System Design Weeks
- learn a framework to use in approaching system design interviews
fill in your mental map of distributed system concepts to serve as a foundation for Capstone project research
building your conceptual knowledge and vocabulary will help in interviews as well
- Note: No project will give you "production" experience, but this will serve as a strong signal about your skill level and ability to learn.


### How is this Different than Core's LS215 or LS220 courses?
- designed to prepare you for a different type of interview
more conversational, less code
- no single "right" answer (although there are definitely wrong answers)
learn to talk in terms of tradeoffs
demonstrate understanding of the answer not selected, the path not taken


### Schedule for Weeks 1 and 2
Week 1 - narrative of building distributed systems
functional system design
introduction to 3-tier architecture
database design and ERD's 
computer resources (memory, cpu, storage)
splitting components of a single node system out into separate nodes
a node can be a server, VM, or a container
key components of a distributed system
horizontal scaling and n-tier architecture
caches, load balancers, databases, app servers
background jobs
building an application on your VPS as a team
Week 2 - deep dive into specific distributed system topics
building an application on your VPS as a team (continue)
database scaling and partitioning (sharding)
NoSQL vs. SQL databases
consistent hashing
monoliths vs. microservices
event-driven architecture
guest speakers coming to talk about actual distributed systems they're working on

### Capstone knowledge

- breadth but also deep knowedge about whatever your Capstone project is about (like feature flags)
- 1st 4 weeks is breadth.
- SO you won't get production level exprrience, but what you'll get may be better.

### SD interview

- How is the interview different?
- It's a conveerstaion
- There are many right answers, but also there are wrong answers.
### What is system design?
- The Todo app is not system design because even if 100s of people use it you don't have to scale it, you simply have to pay more money to Heroku, who are scaling for you. It's abstracted for you.
- Heroku is great, but not for everyone, not for Google:
  - the answer is the data -> the amount of data
  - Heroku is good for CRUD apps, but if you have loads of users & data Heroku is not optimised for that.
  - LS is deployed on Heroku
  - LSbot is not. It's on Railway. Pricing's better.
  - Data-access patterns will be covered later.
- System design is how your system can handle the quantity of data and the velocity of data
  - how your components interact
  - Data is like water. Request data is like bringing water into your system and you have to deal with it. Once the water is there it's hard to change your system. You can't modify the bathtub when it's full. You can';t make it bigger. And if the faucet is on it's harder.
  - First divert the water to a temporary bathtub
  - built a larger bathtub
  - switch water there
  - IT'S A LOT OF WORK (and you mustn't spill the water)

- the O code (the OO code)
- data is ephemeral to the code.
- Changing the data request is not a big deal, but migrating the code within the system is hard, when we're dealing with huge amounts of data.
- If the response slows down, Amazon loses money. So you have to do all of these things wihtout stopping the system.
- So you have to plan the Schema really carefully
- Functional System Design, then scaling.
- Choose your trade-off:
  - scale horizontally/vertically
  - You will need to explain why you did do this, why you didn't do that. The answer needn't be perfect, it's a matter of opinion. After 2 weeks, you won't know everything, but you'll know more.

### Performance v Scalability
- performance is the current state of the app
  - good is 200ms
  - Anything under 500ms is fine
  - over 1second is problem
  - over 2 seconds is bad.
- a lot of this depends on expectation. We know that payment takes longer for instance. AI is slow.
- users don't like to wait.
- Scalability:
  - you have a food of new users and your performance suffers
  - it's about the future
### 3 tier architecture:
- Web server (like Nginx, Apache WebServer, WEBrick(can be both)):
  - good at:
    - being fast
    - Serving static data. It can serve 100s of 1000s of requests.
    - Rate limiting
    - Load balancing
    - Prevent DDos attack
  - bad at:
    - SPOF (single point of failure)
    - Additional configuration complexity.
- Application server (NodeJS, Puma, Unicorn, Deno):
  - good at: serving dynamic responses
  - Bad (slow) at: everything else:
    - serving static assets
    - serving cached data
    - internet overhead (SSL encryption)
    - Rate limiting
- Database (like Postgres, MySQL, SQLite, Micrrosoft SQL server)
  - slow compared to web servers
  - 1 job -> data persistence

- you can have caches spotted all over this.
- How much of optimisation is based on software versus hardware:
  - 
### Question:
- difference between web server and app server

🔹 Web Server
Role: Handles HTTP requests from clients (browsers, mobile apps, etc.) and serves static content.
Examples: Nginx, Apache, Caddy.
Responsibilities:
Accept client requests over HTTP/HTTPS.
Deliver static files like HTML, CSS, JavaScript, images, videos.
Forward dynamic requests to an application server (reverse proxying).
Handle load balancing, caching, SSL termination, compression.
👉 Think of it as the doorman of a building: it greets everyone, quickly hands over things that are ready (static files), and passes along other requests to the right worker (the app server).
🔹 Application Server
Role: Runs the business logic of your app.
Examples: Node.js, Express, Ruby on Rails, Django, Spring Boot, .NET Core.
Responsibilities:
Process dynamic requests (e.g., user login, shopping cart checkout).
Interact with databases or external APIs.
Apply business rules (e.g., “only allow checkout if stock > 0”).
Return results (JSON, HTML, XML) back to the web server, which then sends them to the client.
👉 Think of it as the chef in the kitchen: when the doorman (web server) passes in an order, the chef prepares the meal (business logic + data) and hands it back.
🔹 Together in a 3-Tier Setup
Browser → Web Server
Request: “GET /index.html”
If it’s static, the web server sends it directly.
If it’s dynamic (e.g., “POST /checkout”), the web server forwards it to the app server.
Web Server → Application Server
App server checks stock in the DB, applies rules, updates records.
Application Server → Web Server → Browser
App server sends result → web server returns it to the client.
✅ Key distinction:
Web server = optimized for speed, concurrency, and serving static resources.
Application server = optimized for running your code and connecting with data sources.

### 2nd half
- creator of Rails is the co-owner of Basecamp

- process is a seperate part of memory 
- threads use the same memory, but it can multi-task very fast.
- There is a finite amount of requests that the app server can handle. You're bound by memory and the number of CPU cores.
- So for instance if you have 5 processes with 5 threads per process. That would be 25 requests/instances per second. => (125 per second somehow)
- 1 app instance can deal with 100 - 200 persecond. (1 droplet, EC2 instance on AWS). but you would check this with the interviewer:
  - "Can we assume that one app server instance can process 200 requests per second?"

  - When the request comes in our rails app is loaded into memory.
  - You have a Routes file:
    - These point to controllers (you needn't know a lot about it)
  - Controller
  - The controller has a class called `DocController` which has a method that fetches the document from the database
  - This is simplified, beause in real life you'll have a pool of open database connections.
  - Even with these open connections, this is slow. SO if you can avoid interacting with the database, that's best

  - The lower down you go the slower it gets and the more memory will be sued:
  <img width="959" height="637" alt="Screenshot 2025-08-25 at 18 47 47" src="https://github.com/user-attachments/assets/fb412d4a-80de-4646-aaf7-253afa7a6ed3" />
- RAM is expensive -> If you give a database RAM it will drink it up. Why? We'll talk about it tomorrow.
- Everything the database does it does from memory.
- The thing to remember is that Databases will use all the memory you give them. A LOT.
- 3rd party applications are also slowing down the app.
- Applications also use memory.
- If you have performance issue -?> always look at the database, becasue they're so slow. There's probably something to fix there.
- If you're looking at a scaling issue then you need to look at the applciation server. Scale vertically or horzontally.

- Databases can handle about 1000 Queries per second
- Fixing things higher up is also cheaper
- Greenfield projects -> vertically scale until it becomes too expensive. Most projects aren't greenfield systems, so you'll be figuring out if this is the most cost effective way.
- Scaling is a good problem
- having horizontal scaling requires load-balancing, which is a cost. ALso monitoring one server is easier. It's more work.
- Until you get users, you only have one server. Only get more when you get a lot of users.
- AJ question: AWS video said start horizonatally? Srjan says this is just marketing.
  - going vertical to horizontal is actually quite easy. So start vertical.
  - Saurabh question: is duplicating the app horizontal scaling? No.(?)

### 2 node system
- benefit: you can have specialized servers. A database in a seperate server which can optimise for memory,
- If you have 2 nodes, the first thing to go alone is the database.
- The web-server and app server interact

### interview roadmap

<img width="577" height="609" alt="Screenshot 2025-08-25 at 19 16 24" src="https://github.com/user-attachments/assets/3bb967c1-74c7-447c-90cf-c46022346c92" />

### Design Youtube

- first 2 parts of system design interview are quite easy:
  - Start with use cases:
    - what you as a user can do with this application?
      - design from the client's perspective
      - things that are specific for that app, so don't mention general features, like logging-in
      - Take 2 or 3 use cases and focus on them (30 minutes -> 2, 45 minutes , 3)
      - For our Youtube example we choose:
        - watching videos
        - uploading videos
        - searching videos
- If you aren;'t familiar with the app, you should say youdon't use it and ask for an explanation or a different prompt.
- Everyone on youtube can upload videos, so you needn't discuss admins or creators.
### Design Reddit
- create a post
- View a post
- Create subreddit
- Comment
- upvote/downvote
- join subreddits
- view a newsfeed (this is a whole question in itself, so don't say this)

- focus on 2 or 3 features, because you can't do everything.

- the interviewer may nudge you in a certain direction. It's always a conversation and you need to be able to respond.
- We are aiming for mid to senior engineer so we need to know this. The videos on this on youtube are aimed at system engineers, which is a much higher level than where we need to be. 

Step 2: Design services or functions:
  -create Post(creatorId, postContent subreddit)
  - getPost(postID, subredditId)
POST/subreddits/subredditId/posts body: postContent, userId)
GET /subreddits/:subredditId/ 

NO CODE HERE -> so no code.
Step 3: ERD Schema (tomorrow)


