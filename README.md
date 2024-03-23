# Generative-AI---Coursera
Note: Hugging face is the main hub for open source LLMs. most of the llms , tokenization, model etc are already built by hugging face
Basic framework for applying an llm model:- see "Helper file to apply LLMs" file
1) masked self attention in the decoder is the key ingredient for self supervised learning of an llm
2) Evaluation Metrics for a LLM: BLEU (for translation tasks) and ROUGE (for text summarization tasks). Additionally BLEU is recall oriented ie THE DENOMINATOR will have actual human made translations (if we are rating NMT process say) and rouge is precision oriented (ie in denominator we will have predictions by the model).
Note: BLEU and ROUGE metric do not include the semantic understanding of the complete text. Better metric to evaluate the output is maybe by semantic understanding like SBERT , SVD or topic modelling as well.

Prompt Engineering: / (In Context Learning)
1) Zero shot Learning : Basically prompt given in an instruction mode
2) One shot Learning or inference : Prompt + Instruction mode + one example of how the model should respond (llms learn from examples given in their context window also known as In context learning)
3) Few shot Learning or inference : Prompt + Instruction mode + More than one example 

Fine Tuning:
1)  Instruction Fine Tuning (training each and every parameter of the llm but in the form of instructions. There is a possibility of catastrophic forgetting. Solution : Try fine tuning on a diverse new set of data (memory requirements are higher for executing this)
2) PEFT / Parameter Efficient Fine Tuning . For eg LoRA (Low rand matrices) another set of parameters are added to the llm and fixing the original parameters of the llm. (Memory requirements are much lower)



You interact with an llm by language not by code (prompt)


1) evaluation of llm is generally done by BLEU, and ROUGE.  But most of the reliable is when the evaluation is done by a human (it is referred to be gold standard) when evaluating the model
2) when considering to compare 2 models for a specific use case, jitni kam shots chahiye us model ko achha response generate karne , the better that model is as compared to another one.
3) Pre Training of LLM (or base model training) is done via self -supervised learning (different than just supervised learning ~unsupervised learning) it makes the y ie the targets and X from the raw data only by randomly masking the tokens in the input data and trying to estimate them back. On the other hand fine tuning is a supervised learning method
4) Prompt Tuning is a fantastic way to improve the efficiency of a model. In this random tokens are inputed in context window, the tokens learns their values on themselves only, this is a better method to perform better as compared to prompt engineering (bigger models perform all the more better via prompt tuning) I believe , fine tuning + LoRa + Prompt Tuning (soft prompt) can significantly improve upon the performnace of an LLM.
5) Transfer learning is always used in an llm from pre trained model to fine tuned model (as fine tuned takes the learning of pre trained model and then does instruction fine tuning of PEFT). Note while fine tuning we should be very careful, because if we fine tune only on a specific task then a problem known as catastrophic forgetting might take place. ie the learnings the model learned while it was getting pre trained for different tasks, the fine tuned model might forget those learnings because while fine tuning we didnt fine tuned on all the tasks, due to which there is a chance the weights the model learned in pre training those weights might get updated. that is why sometimes PEFT techniques are very good.

4) One question : Can we use the data that is used for training that same data for prompt engineering, not sure will it value add in the model, then in some ways we can achieve an equilibirium in maybe the amount of data required to train an llm if it can be reduced or not.


Some additional important points:
1) Chinchilla model (there is a research paper popularly known as Chinchilla Model) says if model has 70B parameters the optimal data needed to perfectly train this model is ~20X ( 1.4 Trillion tokens). Basically it tells the trade off between the quantity of data and model paramteres size relation. 
2) Sirf model size se bhi nahi utna achha performance hoga and na Sirf data se
3) Sirf model ke parameters badhaenfe then over parameterize hoga sirf data badhaenge to training Data badhega but performance shayad utni na bade. Chinchilla model says ki optimal model 20X tokens of model parameters chahiye. Compute budget jitna zyada hoga utni better performance hogi (because ham model size ya gpu etc badha sakenge)
4) Question on whether we need or not a new llm from scratch depends upon the use case we have. If the use case is same with respect to which llm is trained then there is no need to learn an llm from scratch, else it further depends on compute budget of the project

##Configuration parameters of an llm
There are 4 generative configuration parameters which are set at the time of inference (and not calculated during training)temperature, max tokens, top p and top k.
1) Temperature: This alters the probability of the last softmax layer which lays distribution of output tokens. The higher temperature makes the distribution of tokens more flatter and NOT skewed. It makes peaks go down and maybe surrounding points probability it might decrease. T>1 -> more creative output . T=1 nullifies the impact of temperature, T<1 makes the distribution much more skewed
2) max tokens : It caps the total no of tokens that the llm can output (note it is not no of words, it is no of tokens)
3) top p : selects top tokens (from top in terms of highest probability) and select only those much tokens from top whose probability sum <=p. then out of these selected tokens, randomly (weighted on probability) is outputed.
4) top k tokens: it is very much similar to top p, only difference is it subsets top k tokens (in terms of their probability)

   
##Residual Connections in Transformer (Why even they exists?)
There are residual connections in transformers model which helps in efficient information flow in the deep neural nets... What happens is sometimes the information is not transferred due to low gradients... No learning happens and information is not passed... To solve this transmission of information residual connections are made.... This is very imp residual connections are just for information flow in between layers by bypassing the inefficiency of backpropagation ie problem of vanishing gradients


###2 problems with llm
1) hallucination : where the model generates an answer which is not correct or is artificially generated by the llm
2) complex mathematical reasoning.. Ie maths is not that good with llm

Solution to 1-> rag (retrieval augmented generation)
Solution to 2 - > pal (program aided language)



####Even for very lengthy input sequence even the attention mechanism will not be able to capture aal of its features because of Information bottleneck

1) Key are always the source jisme se info nikalni hai
2) It is a kind of information retrieval system
3) Context vector along with target encoding jaegi Neural network mein

### Note: There are 2 inputs and 2 outputs in each decoder step. That one hidden state, one output of previous decoder are the input and one hidden state and the output of the current decoder. The hidden state produced by previous decoder actuallys is utilized to calculate attention weights that would be applied on encoder hidden states. Attention is computed at each decoder state. This is very important
