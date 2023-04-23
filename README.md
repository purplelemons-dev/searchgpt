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

