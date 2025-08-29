### Twitter Pull/push strategy:

celebrity: pull model
no celeb: push model (model)

project - when you're hosting a db on mongo, make sure it's not a ...  public? (I missed it)

### Tyler McGraw's RBin system design

### Cache busters

<img width="1045" height="642" alt="Screenshot 2025-08-29 at 16 50 05" src="https://github.com/user-attachments/assets/0a5b286e-7bbf-4eb2-bf46-051a733bff2d" />

- it's a hexadecimal number that ... ? Tells the browser something about where it's getting resources from the cache/CDN ?

### LRU Cache

- the most ofter used
- Also most used in interview
- At least 1 person in each cohort will have this.

#### How it's implemented in theory:

- with 2 db structures:
  - hash -> see if it's present ion the cache
  - doubley linked list -> track what item is most recently and least recently used.
- Hash will contain a pointer to the LL
- Remember LLs are bad at insertion & removal
- (In practice hash/object/dict data structures DO preserve insertion order)
- Don't try and do it now, but DO review it when the job hunt begins.

#### in practice

- You don't need to remember this now, bt in a few months you'll need it.
- Use Map (or some kind of hash structure) with a LL.
- implement Get and Put functions
- If the cache is full the least recently used value gets replaced
- has, delete, get, set -> these are the methods we'll use in JS
- GET
  - IF the cache doesn't jave the key, return -1
  -  Otherwise get the value
  -  delete it
  -  set it at the end, pushing the other values up
-  then return the value
-  PUT
  -  if the cache has the key
    -  delete the value
    -  set it ... somewhere (i missed this)
  -  otherwise
    -  if the cache is full
      - fisrt item 
    - otherwise
      -
