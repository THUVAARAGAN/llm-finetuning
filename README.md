## Movie Genre Classification Bot
This project classifies movie genres based on a summary paragraph using fine-tuned large language models (LLMs). The models can predict one of five genres: action, family, romance, crime, or fantasy.

# Problem Statement
The goal is to classify a movie's genre based on its summary. Given a paragraph summarizing a movie, the bot outputs the genre from one of the following categories: action, family, romance, crime, or fantasy.

# Architecture
The classification pipeline leverages fine-tuned large language models to predict genres. The primary models used are 
- OpenAI's GPT-3.5-turbo (API)
- Meta's LLaMA-2-7B

# Prerequisites
- Python 3.7+
- OpenAI API key for GPT-3.5 usage
- GPU setup for LLaMA-2 finetuning

# Discussion
- For a sample of 14 data points, GPT-3.5 Turbo made 13 correct predictions and 1 incorrect prediction. In comparison, the fine tuned LLaMA-2 model (using PEFT) made 8 correct predictions and 6 incorrect predictions.
- With a total of 68 data points divided into 5 categories, each category has approximately 13 data points. In the test case, the "romance" category has 6 data points (ground truth), while the training set contains only 7 data points for "romance." This limited representation of "romance" features may have affected the model’s ability to learn these features effectively. Consequently, both GPT-3.5 Turbo and LLaMA-2 misclassified examples from the "romance" category. A review of the category distribution in the training set is recommended.
- In the LLaMA-2 inference, many "romance" instances were classified as "fantasy." This misclassification may be due to the low distance between "romance" and "fantasy" vectors in the 5-dimensional vector database, causing the model to confuse the two categories during prediction.
- The prediction accuracy of GPT-3.5 Turbo is comparatively higher than that of LLaMA-2. To enhance LLaMA-2's accuracy, it requires additional data—approximately 100 to 150 more samples. A similar approach applied to the Kaggle dataset has previously resulted in improved accuracy for LLaMA-2.

# Note - More information about workflow check finetune-report
