
# Fine-tuning the GPT Turbo-3.5 Model to Predict my Movie Preferences

>This project aims to fine-tune OpenAI's GPT-3.5 model for classifying movies into two categories: GOOD and BAD. The project leverages a rich dataset of IMDb top 1000 movies and uses the OpenAI API for model fine-tuning.

## Requirements
- Python 3.x
- OpenAI API
- pandas
- numpy
- matplotlib
- seaborn
- sklearn

### To install the required libraries, run:

```python
pip install openai pandas numpy matplotlib seaborn scikit-learn
```

### Dataset
The dataset used for this project is imdb_top_1000.csv, which includes various attributes like movie names, genres, and descriptions.


## Fine-Tuning Process
The model was fine-tuned using a custom prompt that mimics a movie critic's binary classification. The prompt takes three attributes as input: MOVIE_NAME, MOVIE_DESCRIPTION, and GENRE. Below is a sample prompt interaction:

```python
{
  "messages": [
    {
      "role": "system",
      "content": "You are a movie critic binary classifer..."
    },
    {
      "role": "user",
      "content": "MOVIE_NAME: The Godfather..."
    },
    {
      "role": "assistant",
      "content": "GOOD"
    }
  ]
}
>
```
## Results
The model was evaluated using various metrics, including accuracy, precision, and recall. The performance is visualized using bar plots and confusion matrices.

![ConfMatrix4](https://github.com/pramitij/Fine-tune-GPT/assets/19503874/159e4a73-c4b8-4f69-bd05-5ec3338629b9)


![BarPlot2](https://github.com/pramitij/Fine-tune-GPT/assets/19503874/49bf26ea-d3da-4179-9822-0d1532a8f5ec)
![BarPlot](https://github.com/pramitij/Fine-tune-GPT/assets/19503874/1dc8f16c-d590-4c12-ad5d-19f9c6054157)

## Usage
### API Setup
Before interacting with the model, make sure you have obtained an API key from OpenAI. Set up your environment variable with the API key as follows:

```python
export OPENAI_API_KEY=your_openai_api_key_here
```

Or you can set it programmatically in your Python script:

```python
import openai

openai.api_key = "your_openai_api_key_here"

```

### API Call Syntax
To interact with the fine-tuned GPT-3.5 model, you can use the OpenAI API as shown below:

```python
import openai

response = openai.Completion.create(
engine="text-davinci-002",
prompt={
"role": "user",
"content": "MOVIE_NAME: [Your Movie Name] MOVIE_DESCRIPTION: [Description] GENRE: [Genre]"
},
max_tokens=10
)
```
### Extract the model's response

```python
model_response = response.choices[0].text.strip()
```

In this example, text-davinci-002 is the engine ID for the fine-tuned GPT-3.5 model. Replace it with the engine ID corresponding to your fine-tuned model.

### Result

The model will output one of two categories: GOOD or BAD. You can extract this from the model_response variable in the Python script.





