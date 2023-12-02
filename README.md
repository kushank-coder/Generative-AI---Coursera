# Generative-AI---Coursera
Note: Hugging face is the main hub for open source LLMs. most of the llms , tokenization, model etc are already built by hugging face
Basic framework for applying an llm model:- see "Helper file to apply LLMs" file

Prompt Engineering: / (In Context Learning)
1) Zero shot Learning : Basically prompt given in an instruction mode
2) One shot Learning or inference : Prompt + Instruction mode + one example of how the model should respond (llms learn from examples given in their context window also known as In context learning)
3) Few shot Learning or inference : Prompt + Instruction mode + More than one example 

Fine Tuning:
1)  Instruction Fine Tuning (training each and every parameter of the llm but in the form of instructions. There is a possibility of catastrophic forgetting. Solution : Try fine tuning on a diverse new set of data (memory requirements are higher for executing this)
2) PEFT / Parameter Efficient Fine Tuning . For eg LoRA (Low rand matrices) another set of parameters are added to the llm and fixing the original parameters of the llm. (Memory requirements are much lower)



You interact with an llm by language not be code (prompt)


1) evaluation of llm is generally done by BLEU, and ROUGE.  But most of the reliable is when the evaluation is done by a human (it is referred to be gold standard) when evaluating the model
2) when considering to compare 2 models for a specific use case, jitni kam shots chahiye us model ko achha response generate karne , the better that model is as compared to another one.
3) Pre Training of LLM (or base model training) is done via self -supervised learning (different than just supervised learning). On the other hand fine tuning is a supervised learning method

4) One question : Can we use the data that is used for training that same data for prompt engineering, not sure will it value add in the model, then in some ways we can achieve an equilibirium in maybe the amount of data required to train an llm if it can be reduced or not.

 

   
