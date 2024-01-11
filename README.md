# Generative-AI---Coursera
Note: Hugging face is the main hub for open source LLMs. most of the llms , tokenization, model etc are already built by hugging face
Basic framework for applying an llm model:- see "Helper file to apply LLMs" file
1) masked self attention in the decoder is the key ingredient for self supervised learning of an llm
2) Evaluation Metrics for a LLM: BLEU (for translation tasks) and ROUGE (for text summarization tasks)

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
4) Prompt Tuning is a fantastic way to improve the efficiency of a model. In this random tokens are inputed in context window, the tokens learns their values on themselves only, this is a better method to perform better as compared to prompt tuning (bigger models perform all the more better via prompt tuning) I believe , fine tuning + LoRa + Prompt Tuning (soft prompt) can significantly improve upon the performnace of an LLM.
4) One question : Can we use the data that is used for training that same data for prompt engineering, not sure will it value add in the model, then in some ways we can achieve an equilibirium in maybe the amount of data required to train an llm if it can be reduced or not.


Some additional important points:
1) Chinchilla model (there is a research paper popularly known as Chinchilla Model) says if model has 70B parameters the optimal data needed to perfectly train this model is ~20X ( 1.4 Trillion tokens). Basically it tells the trade off between the quantity of data and model paramteres size relation. 
2) Sirf model size se bhi nahi utna achha performance hoga and na Sirf data se
3) Sirf model ke parameters badhaenfe then over parameterize hoga sirf data badhaenge to training Data badhega but performance shayad utni na bade. Chinchilla model says ki optimal model 20X tokens of model parameters chahiye. Compute budget jitna zyada hoga utni better performance hogi (because ham model size ya gpu etc badha sakenge)
4) Question on whether we need or not a new llm from scratch depends upon the use case we have. If the use case is same with respect to which llm is trained then there is no need to learn an llm from scratch, else it further depends on compute budget of the project
 

   
