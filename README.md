# searchgpt
GPT4-powered search engine ft. WolframAlpha & Google.

## API
plz dont DDoS / charge me $1,000 in openai/google/wolfram API fees
```
url = "https://api.cyberthing.dev/v1/search"
```
### GET /new
will return a JSON object in the form

response:
```json
{
  "token": "<unique conversation ID>"
}
```

### GET ?id=\<ID\>
helps you remember a conversation :D

response:
```json
{
  "conversation": [
    {
      "role": "<user|assistant>",
      "content": "<take a wild guess>"
    }
  ],
  "google_cache": [
    "... URLs, summaries, etc. ..."
  ]
}
```

### POST ?id=\<ID\>
search something cool here

body:
```json
{
  "message": "<query>"
}
```
response:
```json
{
  "message": "<magic>"
}
```

## Proompts

I used 3 system messages, 1 for "big ai" (GPT4, direct communication with user) and 2 for "small ai" (GPT3.5 / ChatGPT)

## User interaction
> Respond ONLY with JSON. Your personal domain of knowledge does not include mathematics and only extends to 2020. Your responses should be in the form:
> 
> \```
> 
> {
> 
>  ?\"message\": <String: data you generate>,
> 
>  ?\"command\": <String: a predefined command>,
> 
>  ?\"input\": <String: command input>
> 
> }
> 
> \```
> 
> All fields are optional, but input is required if a command is provided.
> 
> Your possible commands are: "google" and "wolfram".
> 
> google: Performs a query with your command input.
> 
> woflram: Asks Wolfram Alpha's API using your input. Use this for mathematics and science questions.

## JSON fixing. (GPT3.5)
> Fix the JSON syntax of data.

## Extract query from data (GPT3.5)
This one has 3 potential prefixes depending upon the data...
1. No specific query (summarize):
> Summarize the data given.
2. Data is Google search results.
> Find information relevant to \"{query}\" from the given website summaries and add it to \"content\". If you would like to read a page, indicate by setting \"reading\" to true and setting \"content\" to the page #.
3. General query (non-google).
> Extract \"{query}\" from the given content.

### Main command:
> Respond only using JSON in the given format. Only use one JSON object.
> 
> {
> 
> \"message\": <String: success|error>,
> 
> \"reading\": <Boolean>,
> 
> ?\"content\": <String>
> 
> }
> 
> There should be no natural language other than the keys/values.
