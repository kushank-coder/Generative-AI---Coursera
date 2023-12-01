# Generative-AI---Coursera
Note: Hugging face is the main hub for open source LLMs. most of the llms , tokenization, model etc are already built by hugging face
Basic framework for applying an llm model:-

1)  #installing all the libraries (in this course pytorch is used)
%pip install --upgrade pip
%pip install --disable-pip-version-check \
    torch==1.13.1 \  #installing torch (will be using pytorch
    torchdata==0.5.1 --quiet

%pip install \
    transformers==4.27.2 \ #installing transformers from Hugging face
    datasets==2.11.0  --quiet

2) #importing all the libraries

 from datasets import load_dataset
 from transformers import AutoModelForSeq2SeqLM # this is general class for extracting model from transformer library. Specific models coefficients or parameter values are accessed using this class. For example                                                   #like flant5 , GPT) etc we will need we will further need to download the specific model 

 from transformers import AutoTokenizer  #there is a tokenizer class in transformer library...tokenization will be specific to the model
 from transformers import GenerationConfig # GenerationConfig class in transformer library

3) #load the datasets
huggingface_dataset_name = "knkarthick/dialogsum" #dataset is downloaded
dataset = load_dataset(huggingface_dataset_name)

4) #load model
model_name='google/flan-t5-base'
model = AutoModelForSeq2SeqLM.from_pretrained(model_name)  #from pretrained is the function flant5 model is downloaded (you can extract models specific parameters from this

tokenizer = AutoTokenizer.from_pretrained(model_name, use_fast=True)  #Note even tokenizer for each model will be specific to the model choosen, so when we download a model we need to use class Autotokenizer and                                                                       #use the same model #here flant5


5) General processing steps:
       i) Tokenize the input text
       sentence_encoded = tokenizer(sentence, return_tensors='pt') #will return tokens
       ii) apply model to the encoded sentence and over and above that apply tokenizers decoder (which converts tokens back into text)
         sentence_decoded = tokenizer.decode(
                      sentence_encoded["input_ids"],  #this will be models output
                    skip_special_tokens=True
                      )
       iii) sentence decoded is the answer


   for example
   for i, index in enumerate(example_indices):  #enumerate is used in many example to interate through the tuple of info
    dialogue = dataset['test'][index]['dialogue'] #specific dialogue data
    summary = dataset['test'][index]['summary'] # human made summary (ie output of the dialogue)
    
    #model generates tokens and not text we need to apply decoder class (which is not relevant to decoder box of transformer)
    #class of tokenizer which could convert into correct words #here generation is basically decoder task
    inputs = tokenizer(dialogue, return_tensors='pt')  #tokenizer gives input_ids
    output = tokenizer.decode(
        model.generate(
            inputs["input_ids"], 
            max_new_tokens=50,
        )[0], 
        skip_special_tokens=True
    )


6) Generation_config (max_tokens, temperature, top p, top k) - refer week 1 video for insights or meaning of each configuration
Example:
#generation_config = GenerationConfig(max_new_tokens=50, do_sample=True, temperature=0.1)
