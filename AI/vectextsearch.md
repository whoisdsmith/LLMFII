---
tags:
  - "#search-engine"
  - "#openai"
  - "#golang"
  - "#api"
  - "#docker"

  - "#vector-search"
  - "#weaviate"
  - "#text-similarity"
---
# VecTextSearch

[![version](https://img.shields.io/github/v/tag/szpnygo/VecTextSearch?label=version)](https://github.com/szpnygo/VecTextSearch)
![GitHub issues](https://img.shields.io/github/issues/szpnygo/VecTextSearch)
![GitHub forks](https://img.shields.io/github/forks/szpnygo/VecTextSearch)
![GitHub stars](https://img.shields.io/github/stars/szpnygo/VecTextSearch)
![GitHub license](https://img.shields.io/github/license/szpnygo/VecTextSearch)
![Docker Pulls](https://img.shields.io/docker/pulls/neosu/vec-text-search)

VecTextSearchOpenAIWeaviate。Weaviate，。Golang，REST API | [English](README_en.md)

## VecTextSearch  OpenAI  Weaviate 。 Weaviate ，。 Golang ， REST API 。

## [1](history/chat1.md) - [2](history/chat2.md) - DockerfileMakefile

[3](history/chat3.md) - ，[4](history/chat4.md) - [5](history/chat5.md) - ChatGPTMarkdown[6](history/chat6.md) - ，make run[7](history/chat7.md) - [8](history/chat8.md) - [9](history/chat9.md) - weaviateclassName## ### postman
![image](images/postman.png)

### web
![image](images/web_demo.jpeg)

### flutter
![image](images/flutter_demo.jpeg)

## ，。，，。。VecTextSearch  OpenAI ， Weaviate 。

## VecTextSearch ：

- 、、。
- ，。
- ，。
- 。

## TODO - [ ] ****： VecTextSearch 。
- [ ] ****：， Weaviate 。
- [ ] ****： VecTextSearch ，。
- [ ] ****： API 、。
- [ ] ****： VecTextSearch 。
- [ ] ****：。
- [ ] ** OpenAI **： OpenAI ， VecTextSearch。
- [ ] ****： VecTextSearch 。


## VecTextSearch  REST API ：

### - URL: /add-text
- Method: POST
- Content-Type: application/json
- Request Payload:

```json
{
  "name": "",
  "content": ""
}
```
- Response: ， ID  JSON 。

```json
{
  "id": ""
}
```

### - URL: /search-similar-texts
- Method: POST
- Content-Type: application/json
- Request Payload:

```json
{
  "content": ""
}
```

Response: ， JSON 。

```json
[
  {
    "name": "",
    "content": "",
    "distance": （）,
    "certainty": （）
  },
  ...
]
```

## Makefile - `make init`： `.env` ，。
- `make build`： Docker 。
- `make push`： Docker  Docker Hub。
- `make run`：。

## Weaviate```bash
docker run -d \
  --name weaviate \
  -p 8888:8080 \
  --restart on-failure:0 \
  -e QUERY_DEFAULTS_LIMIT=25 \
  -e AUTHENTICATION_ANONYMOUS_ACCESS_ENABLED=true \
  -e PERSISTENCE_DATA_PATH='/var/lib/weaviate' \
  -e DEFAULT_VECTORIZER_MODULE='none' \
  -e ENABLE_MODULES='' \
  -e AUTOSCHEMA_ENABLED=true \
  -e CLUSTER_HOSTNAME='node1' \
  semitechnologies/weaviate:1.18.1 \
  --host 0.0.0.0 \
  --port 8080 \
  --scheme http
```

## ChatGPT  Markdown Chrome ChatGPT  Markdown  ChatGPT  Chrome ， ChatGPT  OpenAI  Markdown 。 Markdown ，。，。

：

-  ChatGPT  " Markdown" -  Markdown -  "Neo"（） "ChatGPT"（），[ChatGPTMarkdown](history/extension/)。


##  VecTextSearch ，：

1. ：

```bash
git clone https://github.com/szpnygo/VecTextSearch.git
```

2. ：

```bash
cd VecTextSearch
go get -u
```

3.  config.yml  OpenAI API 。

4. ：

```bash
go run main.go
```

 VecTextSearch ， Issue  Pull Request。！

## VecTextSearch  MIT 。， LICENSE 。

##  VecTextSearch ，。：

-  GitHub  Issue
- ：st2udio@gmail.com
