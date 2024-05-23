# TASK 4 --> NLP

### Approach to the Problem
- First I skimmed throught the paper and searched on the internet for understanding what RAG model are.
- Found out RAG models consist of 2 parts, the retriever and the generator.
- To make the retriever I first cleaned the data, removed the NA values, converted the words column to lower case(so that there is uniformity), also there were several special charectors mid-sentences in the Paragraph column so removed them using regular expression,  and then finally tokenized the words, using tf-idf vectorizer.
- Next in the retriever I first converted the question to tokens , found out which words have the highest tf-idf score and then used those words to find the most similar paragraph using cosine similarity.
- Then sorted the paragraphs in descending order of similarity and then used the top 5 paragraphs to form the context for the generator.If less than 5 paragraphs were found then I reported that question could not be answered. 
- For the generator I used the T5 model from the transformers library, I used the T5ForConditionalGeneration model and the T5Tokenizer.I experimented with different transformers like BART, distilBART, etc but T5 gave the best results.

### Roadblocks and Measures to Increase Accuracy

During the task, I encountered several challenges:

-  There were several special charectors mid-sentences in the Paragraph column so had removed them using regular expression.
-  The dataset was not cleaned properly, there were NA values in the dataset, so had to remove them.
- Majority of the time was spent on implementing the retriever part of the RAG model, had to deal with sparse matrix, sorting the matrix,finding the words with highest tf-idf score,converting the tokens of words back to the original word and then finally finding the most similar paragraph using cosine similarity.
- After this there were some duplicate paragraphs in the dataset, so had to remove them using the drop_duplicates function on similarity score.
- Finding the appropriate model for the generator part of the RAG model was also a challenge, experimented with different models like BART, distilBART, etc but T5 gave the best results of all.

## Instructions to Run the Code

To run the code:

1. Clone this repository to your local machine.
2. Upload the file `task_4-->Aarush_singh_kushwaha.ipynb` in colab and read the comments as a guide to run the notebook.
3. Upload the `paragraphs.xlsx` dataset to colab.  <br>
OR  

Directly run in colab though this [Notebook link](https://colab.research.google.com/drive/1DZ2keeWM7XdJIJJNk3lAsGXcresv1tu1?usp=sharing)


## Screenshots
Some results<br><br>
<img src="Screenshots/Screenshot from 2024-05-23 11-32-22.png" alt="Alt Text"  height="400">
<img src="Screenshots/Screenshot from 2024-05-23 11-35-21.png" alt="Alt Text"  height="400">
<img src="Screenshots/Screenshot from 2024-05-23 11-41-54.png" alt="Alt Text"  height="400">

