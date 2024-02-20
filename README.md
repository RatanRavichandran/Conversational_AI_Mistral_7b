# Conversational_AI_Mistral_7b
Using the Mistral 7b LLM to converse with and extract information from academic reports


## About Mistral
Mistral-7B is a decoder-based LLM, sourced by Mistral AI. For this project, I'm using Mistral-7B-Instruct-v0.1. It's an instruct fine-tuned version of the Mistral-7B-v0.1 generative text model using a variety of publicly available conversation datasets.

The reason I'm using it for this use case, i.e. information retrieval from academic records, is because of two key features of the model that caught my attention:

- Sliding Window Attention: This model is trained with an 8k context length and fixed cache size, with a theoretical attention span of 128K tokens. This allows the model to consider a large context when generating responses, which can be particularly useful when dealing with complex documents like academic reports.

- Grouped Query Attention (GQA): This feature allows for faster inference and lower cache size. Faster inference means the model can generate responses more quickly, and a smaller cache size can make the model more efficient to run.

# Datasets
The dataset used is an academic report on the fundamentals of cybersecurity. This report will be used as a reference for the retrieval of information by the LLM. 
It can be found in the Data folder. (Feel free to replace this with your own dataset while running the code.)

# Dependencies
The following libraries are required to run this project: 
- ctransformers
- faiss-cpu
- langchain==0.0.331
- pypdf
- python-box
- sentence-transformers

These can be installed by running:

`pip install -r requirements.txt`

In addition, download the quantized mistral-7b-instruct-v0.1.Q5_K_M.gguf model from: https://huggingface.co/TheBloke/Mistral-7B-Instruct-v0.1-GGUF/tree/main

# Executing the Program
Next, this text has to be stored as vector embeddings for quick retrieval. This is done by storing these vector embeddings in a FAISS Index. This is done by running:

`python ingest.py`

To process this data with the LLM and return the final answer, run:

`python main.py "<insert query here>"`



## Running Tests

<a href="https://ibb.co/9NbX9DM"><img src="https://i.ibb.co/BtyDVp1/Screenshot-2024-02-19-120532.png" alt="Screenshot-2024-02-19-120532" border="0"></a>

# Conclusion
The model did an excellent job, extracting relevant information without any hallucinations. As we move forward, we can consider fine-tuning the model with domain-specific data, optimizing the FAISS index for faster retrieval, or experimenting with different pooling methods for token embeddings. These improvements could potentially enhance the model’s performance even further.

# Contributions
If you have ideas for improvement or wish to contribute, please open an issue or submit a pull request. Collaboration is highly encouraged!
