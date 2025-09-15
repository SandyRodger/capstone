### prework1 poetry workflow

- install pipx:
  1. `brew install pipx`
  2. `pipx ensurepath`
- install Poetry:
  1. `pipx install poetry`
  2. `pipx ensurepath`
- `poetry config virtualenvs.in-project true`

### prework_2_openai_api_key

- `https://help.openai.com/en/collections/13193904-secure-sign-in`
- log in  (top right)
- Create API key:
  - name: `Capstone_key`
  - default project
  - API key stored in capstone/monkey_faces
- Add $10 API credit.

- create a new project and virtual environment:

```
mkdir dotenv_test
cd dotenv_test
poetry init --no-interaction
poetry add python-dotenv
eval $(poetry env activate)
```

- install `python-dotenv`
  - `poetry add python-dotenv` (it was already there) 
- Create a `.env` file and add your API key
  - `OPENAI_API_KEY=your_api_key_here`
  - Create a .gitignore file and add .env
  - Load the environment variable in your code
  - test with `python my_app.py`

### prework_3_jupyter_setup
- step 1:
  - `pipx ensurepath`
  - `poetry install`
  -`eval $(poetry env activate)`
  - `poetry add jupyter ipykernel` -> already present.
- step 2:
  - `poetry env info`
- step 3:
  - `poetry add openai`

- 3:36 -> 4:25 lost to trying to set the right kernel to the project. (49 minutes) So read the instructions very carefully, and take copious notes. and if you're using chatgpt write a summary of each command before you copy and paste it.

### Jupyter videos:

#### [Jupyter Notebook](https://www.youtube.com/watch?v=5pf0_bpNbkw)

- [25:11]
- python shell
- Script = a file on which you run python
- `ipython` -> similar to phython but has a little more functionality. Is what Jupyter is built from.
  - import panda as pd
- `pip install jupyterlab`
- `jupyter notebook`
- port 8888

### After completing the homework, write up your personal reflections on the following questions. These will come up in the next session:

1. What are foundational models?
- Foundational LLMs are the basis
2. Explain how LLMs generate text
3. What are some ways foundation models differ from each other?
4. What unique challenges do AI applications pose versus traditional applications?
5. What are the components of a good prompt?
6. What is a context window? Why does it exist?
7. Beyond your prompt instructions, what might go into context?


#### [second](https://www.youtube.com/watch?v=1Z8T36sZ9WI)



