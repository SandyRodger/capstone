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

#### [second](https://www.youtube.com/watch?v=1Z8T36sZ9WI)

### After completing the homework, write up your personal reflections on the following questions. These will come up in the next session:

1. What are foundational models?
- Foundation models are large, general-purpose AI models trained on massive, diverse datasets. They can be adapted (**fine-tuned**) for many downstream tasks, rather than being designed for one narrow application.
- Examples include large language models (LLMs) like GPT-4 or Gemini, and large multimodal models that handle both text and images (and sometimes audio, code, or video).
- They are called “foundation” models because they provide a base layer of general capabilities that can be specialized into many different applications.
- This represents a shift from earlier AI approaches, where separate models were built for specific tasks (e.g., one model for text classification, another for image recognition).
- A multimodal foundation model can integrate across domains, e.g., answering a question about an image using natural language.

2. Explain how LLMs generate text

- LLMs generate text by predicting the most likely next token (a word fragment, word, or symbol) given the sequence of tokens so far.
  - **Training** During training, the model learns statistical patterns in language by adjusting billions of parameters in a neural network to minimize the error in predicting the next token.
  - **Generation** At inference time, the model computes a probability distribution over possible next tokens.
  - **Sampling** The next token is chosen either by taking the highest probability (greedy decoding) or by sampling, sometimes from the less probable options (using methods like temperature scaling or top-k sampling) the make the text more natural and varied. The process repeats, token by token, until a full passage of text is produced.

3. What are some ways foundation models differ from each other?

- Foundation models can differ in several important ways:
  - **training data** They may be trained on text, images, proteins, code, or mixtures of modalities.
  - **architecture** Some are transformer-based LLMs (eg GPT-4), others adapt the transformer to vision (eg Vision transformers), or biology (protein sequence models)
  - Training objective - some predict the next token (causal LMs), others predict masked tokens (BERT-style), or even reconstruct multimodal outputs.
  - **scale and efficiency** - They vary in number of parameters, compute budgets and scale and efficiency.
  - **alignment and fine-tuning** They may be tuned for safety, helpfulness, or domain expertise.

4. What unique challenges do AI applications pose versus traditional applications?

- **unpredictability** AI outputs are probablistic, not deterministic, so ensuring consistent, safe behaviour is harder
- **alignment & safety** Outputs may conflict with user values, creator intent, or ethical norms.
- **security & misuse** - The low barrier to use (natural lanuage prompts) means attackers/bad actors can easily probe systems for weaknesses.
- **bias/unfairness** - AI systems can amplify harmful biases present in training data.
- **Explainability** - unline traditional software, where logic is transparent, AI decisions are often opaque ("black box")
- **Data dependence** - Performace depends heavily on the quantity and provenance of training data, creating risks of data poisoning or leakage.

5. What are the components of a good prompt?

- A good prompt clearly communicates the task, context and expectations. Key components include:
  - **Role/Instruction** - define who the model should act as (eg, "you are a helpful tutor")
  - **Context** - supply background info or constraints relevant to the task.
  - **Task clarity** state exactly  what you want (eg. summarize in 3 bullet points)
  - **Examples** provide sample input-output pairs (few-shot prompting)
  - **Format specification** - indicate the desired output style (eg JSON, essay, bullet points)
  - **constraints** - include boundaries (length limits, tone, domain)

6. What is a context window? Why does it exist?

- a context window is the maximum span of text (measured in tokens) that a large language model can process at once when generating outputs. It includes the user's prompt, system instructions and prior conversation history.
- It exists because transformer models compute attention over all tokens in the input, and this has high computational and memory cost. Limiting the context window keeps training and inference feasible.
- Example: GPT-4 may have an 8K, 32k, or even 128K token context window, meaning it can "remember" and reason over that many tokens at once.
- Anything beyond the window is forgotten unless explicitly re-provided

7. Beyond your prompt instructions, what might go into context?

- **system prompts** hidden or framework-level instructions (e.g. "you are ChatGPT...")
- **conversation history** - previous user and assistant turns in a chat.
- **retrieved documents** extra information pulled in by retrieval-augmented generation (RAG)
- **examples/few-shot demonstrations** - sample Q&As or problem-solution pairs.
- **metadata/formatting tokens** seperators, role indications, special tokens.
- **External tools' outputs** if the model is augmented with search, code execution, etc., those results may also be fed into the context window.





