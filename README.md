# huggingface-tapas
TAPAS
It’s a BERT-based model specifically designed (and pre-trained) for answering questions about tabular data.
It uses relative position embeddings and has 7 token types that encode tabular structure.
TAPAS is pre-trained on Masked language Modelling (MLM)
For question Answering, TAPAS has 2 heads on top: a cell selection head and an aggregation head, for performing aggregations among selected cells.
TAPAS is fine-tuned on:
•	SQA (Sequential Question Answering by Microsoft)
•	WTQ (Wiki Table Questions by Stanford University)
•	WikiSQL (by Salesforce)
Achieved State of art performance on SQA and WTQ datasets, while comparable performance in WikiSQL 
TAPAS trains from weak supervision and predicts the denotion by selecting table cells and optionally applying a corresponding aggregation operator to such selection
For table-entailment they have done training prior to fine tuning the model with TabFact dataset
 
Some Parameters in TAPAS:
•	reset_position_index_per_cell = True for relative embeddings
•	revision="no_reset" for absolute embeddings
•	Advised to pad the inputs on the right rather than the left.
TAPAS has checkpoints fine-tuned on SQA, which can answer questions related to a table in a conversational set-up. This means that you can ask follow-up questions such as “what is his age?” related to the previous question
TAPAS is like BERT and therefore relies on the masked language modelling (MLM) objective. It is therefore efficient at predicting masked tokens and at NLU in general but is not optimal for text generation. 

TAPAS Fine Tuning for Q&A:
SQA: generally, for conversational setup, if you ask to follow up questions. Here questions don’t involve aggregation.
WTQ: Conversational setup, follow up questions and it involves aggregation.
Example of aggregation: 
•	How much runs Virat Kohli scored in his entire career, this type of case comes under weak supervision
WikiSQL-supervised:  model being given the ground truth aggregation operator during training (Strong Supervision)




