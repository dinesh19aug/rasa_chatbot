# rasa_chatbot
Simple chat bot built using Rasa and Rasa NLU

# How to train the core
python -m rasa_core.train -d domain.yml -s ./data/stories.md -o models/dialogue
 - This will train the core that is defined in domain and and stories. Domain file contains what intents and actions area allowed, while the story is flow chart of conversation.

# How to test the trained core
python -m rasa_core.run -d models/dialogue
- Think of core testing as testing a rest resoure. When you train and test the core, you are basically testing the flowchart. Ex - The first flow is happy path. 
Bot: How are you?
You: I am good.
Bot: Great Carry on.
If you want to test the above flow, the conversation follows greet: utter_greet -> mood_great:utter_happy. So ifpe  you test this, when the program runs, you type /greet. Then you type /mood_great.



python -m rasa_nlu.train -c config_spacy.yml --data ./data/nlu_md.md -o models --fixed_model_name nlu --project current --verbose

python -m rasa_core.run -d models/dialogue -u models/current/nlu
