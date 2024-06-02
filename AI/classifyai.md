---
tags:
  - "#python"
  - "#openai"
  - "#api"
  - "#classification"
  - "#software-development"

  - "#flask"
  - "#rest-api"
  - "#data-classification"
---
# ClassifyAI

ClassifyAI is a python project, which uses the OpenAI API to sort data with personalized classification models. It has a REST API that lets you send requests for classifying information and get answers from the GPT model.

This API sends back responses in the format of the specified model, making it easy for applications to work with the results.
<br/><br/>

## Requirements

- Python 3.7 or higher
- Flask
- OpenAI Python library
- python-dotenv

## Alpha Versions

- 0.1.0
  - First Version that is able to take user inputs and respond with the given model
- 0.2.0
  - You can now define and run tests for your models in /test
  - New default models finance and healthcare + Tests
  - New Approach on healthcare model to not set the value key but let openAI API decide what to fill
- 0.3.0 - create, edit and delete models over python API - TBA
  - New Endpoints models for listing, retrieving, creating, changing and deleting models
  - You can see it [here](#api-reference)
- 0.4.0 - Management Website to create, edit and delte models - TBA
- 0.5.0 - Documentation on https://docs.wen.solutions/docs/Intro - TBA
- 0.6.0 - Add pip package to use in python projects

Within those Versions we will always try to adjust the prompts to get the best results.

If you encounter problems, please open an Issue
<br/><br/>

# Installation

1.  Clone the repository:

        git clone https://github.com/WenServices/ClassifyAI.git

2.  Change to the project directory:

        cd ClassifyAI/service

3.  Start environment

        python3 -m venv venv

4.  Activate environment

        source venv/bin/activate

5.  Install the required dependencies:

        pip install -r requirements.txt

6.  Create a `.env` file in the project directory with the following variables:

        #Loggin Level (INFO, DEBUG, WARNING, ERROR, CRITICAL)
        LOG_LEVEL=INFO

        #Port to run the server on (Default is 5000)
        PORT=5000

        # OpenAI API Key
        OPENAI_API_KEY=your_openai_api_key

        # Maximum input text length (Unset if 0)
        MAX_INPUT_LENGTH=0

        # Maximum context text length (Unset if 0)
        MAX_CONTEXT_LENGTH=0

        # OpenAI model to call
        MODEL=text-davinci-003

        # Maximum tokens you want to pay per response
        MAX_TOKENS=150

Replace `your_openai_api_key` with your actual OpenAI API key and set the other variables as desired.
<br/><br/>

# Usage

1.  Start the Flask API server:

        python3 app.py

2.  Send a POST request to the `/classify` endpoint with the required data in the JSON body. Example:

        {
            "model": "basic",
            "input": "You are great!"
        }

3.  The API will return a JSON object with the classification result.

            {
                "requestScope": "Personal",
                "request_type": "Statement"
            }

    <br/><br/>

# Models

### The API can use models that are within the /service/models folder. We currently have 2 examples in there

- basic.json
- ecommerce.json

## The .json file needs to be JSON object and have the objects: model and model_description like in our basic.json

        {
        "model": {
            "request_type": "",
            "requestScope": ""
        },
        "model_description": {
            "request_type": {
            "values": [
                {
                "key": "Question",
                "description": "Choose this if the user request is a question"
                },
                {
                "key": "Statement",
                "description": "Choose this if the user request is a statement"
                }
            ]
            },
            "requestScope": [
            {
                "dependsOn": "request_type",
                "dependsOnValue": "Question",
                "key": "Personal",
                "description": "Choose this if the question is about the user himself or other persons"
            },
            {
                "dependsOn": "request_type",
                "dependsOnValue": "Question",
                "key": "Other",
                "description": "Choose this if the question is neither of the above"
            },
            {
                "dependsOn": "request_type",
                "dependsOnValue": "Statement",
                "key": "Personal",
                "description": "Choose this if the statement is about the user himself or other persons"
            },
            {
                "dependsOn": "request_type",
                "dependsOnValue": "Statement",
                "key": "Other",
                "description": "Choose this if the statement is neither of the above"
            }
            ]
        }
        }

## Users are able to pass the name of the .json file in the POST request like this

        {
            "model": "ecommerce",
            "input": "What is WenServices all abbout?",
            "context": "WenServices is a software company",
            "reference_id": "WhoIsDis",
            "reference_id_name": "_id"
        }

## Response:

        {
            "_id": "WhoIsDis",
            "requestScope": "Company",
            "request_type": "Question"
        }

## Users are also able to pass the model and it's description directly in the POST request like this

        {
        "model": {
            "model": {
                "request_type": "",
                "requestScope": ""
            },
            "model_description": {
                "request_type": {
                "values": [
                    {
                    "key": "Question",
                    "description": "Choose this if the user request is a question"
                    },
                    {
                    "key": "Statement",
                    "description": "Choose this if the user request is a statement"
                    }
                ]
                },
                "requestScope": [
                {
                    "dependsOn": "request_type",
                    "dependsOnValue": "Question",
                    "key": "Product",
                    "description": "Choose this if the question is about a product"
                },
                {
                    "dependsOn": "request_type",
                    "dependsOnValue": "Question",
                    "key": "Order",
                    "description": "Choose this if the question is about an order"
                },
                {
                    "dependsOn": "request_type",
                    "dependsOnValue": "Question",
                    "key": "Company",
                    "description": "Choose this if the question is about a company"
                },
                {
                    "dependsOn": "request_type",
                    "dependsOnValue": "Question",
                    "key": "Other",
                    "description": "Choose this if the question is neither of the above"
                },
                {
                    "dependsOn": "request_type",
                    "dependsOnValue": "Statement",
                    "key": "Product",
                    "description": "Choose this if the statement is about a product"
                },
                {
                    "dependsOn": "request_type",
                    "dependsOnValue": "Statement",
                    "key": "Order",
                    "description": "Choose this if the statement is about an order"
                },
                {
                    "dependsOn": "request_type",
                    "dependsOnValue": "Statement",
                    "key": "Company",
                    "description": "Choose this if the statement is about the company"
                },
                {
                    "dependsOn": "request_type",
                    "dependsOnValue": "Statement",
                    "key": "Other",
                    "description": "Choose this if the statement is neither of the above"
                }
                ]
            }
        },
            "input": "What is WenServices all abbout?",
            "context": "WenServices is a software company",
            "reference_id": "WhoIsDis",
            "reference_id_name": "_id"
        }

## Response

        {
            "_id": "WhoIsDis",
            "requestScope": "Company",
            "requestType": "Question"
        }

<br/><br/>

# Tests

## Define tests

After you have created a model you can add a new file into the /test/data folder e.g. healthcare.py

The structure looks like this

        test_cases = [
            # Acute Symptom
            {
                "name": "acute_symptom_case",                # Test Name
                "input": {
                    "model": "healthcare",                   # Model Name
                    "input": "I have a headache.",           # User Input
                    "reference_id": "AcuteSymptomQuery1",    # Optional
                    "reference_id_name": "_id",              # Optional
                },
                "expected_output": {
                    "_id": "AcuteSymptomQuery1",
                    "category": "Symptom",
                    "subCategory": "Acute symptom",
                },
                "repeat": 1,    #Repeat test n times
            }
        ]

## Run tests

1.  Go to ./test

        cd test

2.  Run all tests
    ! This makes multiple openAI requests!

        python3 test.py

3.  Run specific model tests with adding the name

        python3 test.py healthcare

<br/><br/>

# API Reference

### POST /classify

- URL: /classify
- Method: POST
- Headers: Content-Type: application/json
- Data Params:
  - input: (string, required) The input text to be classified.
  - model: (string or JSON object, required) The model name or model JSON object to be used for classification.
  - context: (string, optional) Additional context to be provided to the GPT model.
  - reference_id: The response will contain this reference ID
  - reference_id_name: The response will call the reference ID according to this field
- Success Response:
  - Code: 200
  - Content: { "result": "classification_result" }
- Error Response:
  - Code: 400 BAD REQUEST
  - Content: { "error": "Error message" }

## API Endpoints

### POST /classify

- URL: /classify
- Method: POST
- Headers: Content-Type: application/json
- Data Params:
  - input: (string, required) The input text to be classified.
  - model: (string or JSON object, required) The model name or model JSON object to be used for classification.
  - context: (string, optional) Additional context to be provided to the GPT model.
  - reference_id: The response will contain this reference ID
  - reference_id_name: The response will call the reference ID according to this field
- Success Response:
  - Code: 200
  - Content: { "result": "classification_result" }
- Error Response:
  - Code: 400 BAD REQUEST
  - Content: { "error": "Error message" }

### GET /models

- URL: /models
- Method: GET
- Headers: None
- Success Response:
  - Code: 200
  - Content: [ "model1", "model2", ... ]
- Error Response:
  - Code: 500 INTERNAL SERVER ERROR
  - Content: { "error": "Error message" }

### GET /models/:model_name

- URL: /models/:model_name
- Method: GET
- Headers: None
- URL Params:
  - model_name: (string, required) The name of the model to retrieve.
- Success Response:
  - Code: 200
  - Content: { "model": "model_content", "model_description": "model_description" }
- Error Response:
  - Code: 404 NOT FOUND
  - Content: { "error": "Error message" }
  - Code: 500 INTERNAL SERVER ERROR
  - Content: { "error": "Error message" }

### POST /models/:model_name

- URL: /models/:model_name
- Method: POST
- Headers: Content-Type: application/json
- URL Params:
  - model_name: (string, required) The name of the model to create or update.
- Data Params:
  - model: (JSON object, required) The model JSON object.
  - model_description: (string, required) The description of the model.
- Success Response:
  - Code: 200
  - Content: { "message": "Model 'model_name' created or modified successfully." }
- Error Response:
  - Code: 400 BAD REQUEST
  - Content: { "error": "Error message" }
  - Code: 500 INTERNAL SERVER ERROR
  - Content: { "error": "Error message" }

### DELETE /models/:model_name

- URL: /models/:model_name
- Method: DELETE
- Headers: None
- URL Params:
  - model_name: (string, required) The name of the model to delete.
- Success Response:
  - Code: 200
  - Content: { "message": "Model 'model_name' deleted successfully." }
- Error Response:
  - Code: 404 NOT FOUND
  - Content: { "error": "Error message" }
  - Code: 500 INTERNAL SERVER ERROR
  - Content: { "error": "Error message" }

<br/><br/>

# Contributing

If you'd like to contribute to the project, please submit a pull request or open an issue with your proposed changes.
<br/><br/>

# License

This project is licensed under the MIT License. See the LICENSE file for details.

<br/><br/>

# Acknowledgments

This project uses the OpenAI GPT models to perform the data classification.
