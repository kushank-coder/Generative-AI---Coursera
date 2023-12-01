# Generative-AI---Coursera
Note: Hugging face is the main hub for open source LLMs. most of the llms , tokenization, model etc are already built by hugging face
Basic framework for applying an llm model:- see "Helper file to apply LLMs" file

Zero shot Learning : Basically prompt given in an instruction mode
One shot Learning or inference : Prompt + Instruction mode + one example of how the model should respond (llms learn from examples given in their context window also known as In context learning)
Few shot Learning or inference : Prompt + Instruction mode + More than one example 


You interact with an llm by language not be code (prompt)


1) evaluation of llm is generally done by BLEU, and ROUGE.  But most of the reliable is when the evaluation is done by a human (it is referred to be gold standard) when evaluating the model
2) when considering to compare 2 models for a specific use case, jitni kam shots chahiye us model ko achha response generate karne , the better that model is as compared to another one
   
