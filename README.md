# text-summarizer-project

# Text Summarizer

This project is an end-to-end text summarizer designed to summarize conversational texts, using `google/pegasus-cnn_dailymail` fine-tuned on the SAMSum dataset. The project is modular and designed to be extensible, with FastAPI endpoints for easy integration.

## Overview

The text summarizer processes conversational data from ingestion to model prediction through a series of automated steps, including data validation, transformation, model training, evaluation, and prediction.

### Model & Dataset

- **Model**: [google/pegasus-cnn_dailymail](https://huggingface.co/google/pegasus-cnn_dailymail)
- **Dataset**: [SAMSum dataset](https://huggingface.co/datasets/Samsung/samsum) — suitable for conversational text summarization.

## Workflow

1. **Data Ingestion**: Downloads and unzips raw data into a structured format.
2. **Data Validation**: Confirms the existence of required datasets (train, test, validation).
3. **Data Transformation**: Tokenizes the data using `google/pegasus-cnn_dailymail` for compatibility with the model.
4. **Model Training**: Fine-tunes the model on the SAMSum dataset.
5. **Model Evaluation**: Evaluates model performance using ROUGE metrics (`rouge1`, `rouge2`, `rougeL`, `rougeLsum`).
6. **Prediction**: Generates summaries using the fine-tuned model.


## Configuration

Configuration files include:

- `config.yaml`: Specifies file paths and dataset details for each pipeline step.
- `params.yaml`: Configures training hyperparameters such as epochs, batch size, and logging settings.


## FastAPI Endpoints

The project includes a FastAPI app (app.py) with the following endpoints:
1. Training: Trigger model training via a /train endpoint.
2. Prediction: Generate text summaries via a /predict endpoint by providing conversational text as input.

## Usage 
1. Clone the repository
- pip install -r requirements.txt
2. Run the main pipeline script to perform all stages from data ingestion to evaluation. 
python main.py
3. Access the API:
- Training: Send a POST request to /train.
- Prediction: Send a POST request to /predict with conversational text data.
