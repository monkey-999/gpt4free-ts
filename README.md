This is a replication project for the typescript version of [gpt4free](https://github.com/xtekky/gpt4free)




## Run local

```shell
# install module
yarn
# start server
yarn start
```

## Deploy with docker-compose

first, you should create file .env
```env
http_proxy=http://host:port
# you should config this if you use forefront api, this apikey is used for receive register email
# get api key here https://rapidapi.com/calvinloveland335703-0p6BxLYIH8f/api/temp-mail44
rapid_api_key=xxxxxxxxxx
```
deploy
```
docker-compose up --build -d
```

## Test with curl

### params in query

```
prompt: string; // required
```

forefront options
```
chatId?: string;
actionType?: Action; // 'new' or 'continue'
defaultPersona?: string;
gptmodel?: Model; // gpt-4 or gpt-3.5-turbo
resignup?: number; // default 0 if set 1, auto sign up when gpt4 times use up
// event: error
// data: GPT-4 rate limit exceeded (>5 messages every 3 hours). Time remaining: 179 minutes
// if you see this try set resignup=1 or use gpt-3.5-turbo
```

### test now!

common request
```shell
# test default model chat.forefront.at
curl "http://127.0.0.1:3000/ask?prompt=hello&model=forefront&gptmodel=gpt-4&resignup=1"

# test you.com
curl "http://127.0.0.1:3000/ask?prompt=hello&model=you"
```

request event-stream 
```shell
# test default model chat.forefront.at
curl "http://127.0.0.1:3000/ask/stream?prompt=hello&model=forefront&gptmodel=gpt-4&resignup=1"

# test you
curl "http://127.0.0.1:3000/ask/stream?prompt=hello&model=you"
```

