# How to setup a coding co-pilot almost for free  
The purpose of this reading is to give a guidance on setting up and running personal co-pilot similar to one that you can buy from Github.  
1. There is a great company [anyscale](https://www.anyscale.com/) that develops [ray](https://www.ray.io/) framework and those folks are offering serving of open source LLMs. All you need is to REGISTER [HERE](https://app.endpoints.anyscale.com/welcome)
2. Once you register - [generate and API key](https://app.endpoints.anyscale.com/credentials)
3. Models that are avialable at anyscale:
   - Open-Orca/Mistral-7B-OpenOrca
   - mistralai/Mixtral-8x7B-Instruct-v0.1
   - HuggingFaceH4/zephyr-7b-beta
   - codellama/CodeLlama-34b-Instruct-hf
   - Meta-Llama/Llama-Guard-7b
   - BAAI/bge-large-en-v1.5
   - thenlper/gte-large
   - mistralai/Mistral-7B-Instruct-v0.1
   - meta-llama/Llama-2-70b-chat-hf
   - meta-llama/Llama-2-13b-chat-hf
   - meta-llama/Llama-2-7b-chat-hf
4. You can query the api that is compatible with OpenAI, for instance to get a list of models:
```sh
curl --location 'https://api.endpoints.anyscale.com/v1/models' \
--header 'accept: application/json' \
--header 'Authorization: Bearer esecret_key-goes-here'
```
5. The nice stuff is that once registerd you get a 10USD of credits for generation requests.
6. Now install [continue](https://continue.dev/docs/quickstart) plugin for vscode - its on of opensource analogs of github co-pilot.
7. Add CodeLlama model as an engine for co-pilot in `config.json` configuration file of continue :
   ```json
       {
      "title": "CodeLlama-34b",
      "model": "codellama/CodeLlama-34b-Instruct-hf",
      "contextLength": 16384,
      "apiBase": "https://api.endpoints.anyscale.com",
      "completionOptions": {},
      "apiKey": "esecret_your-key-goes-here",
      "provider": "openai"
    }
   ```
8. You are set and can query the model to assist you with your coding. 
