# Ollama CPU Server

이 저장소는 **[Ollama](https://github.com/ollama/ollama)** 런타임 위에서 **Google Gemma 3** 모델을 CPU 환경에서 실행하여  
간단한 REST API를 구축하는 예제를 제공합니다.

## 🚀 특징
- **CPU 기반 실행**: GPU 없이도 Gemma 3 모델 구동 가능 (느릴 수 있음).
- **간단한 배포**: `docker-compose up` 만으로 서버 실행.
- **REST API 지원**: `curl` 또는 다른 클라이언트로 번역 요청 가능.
---

## 📦 설치 방법

### 1. 저장소 클론
```bash
git clone https://github.com/jwjung3030/ollama-cpu-server
cd ollama-cpu-server

```

### 2. 기동 & 모델 풀
```bash
docker compose up -d
docker exec -it gemma3-ollama ollama pull gemma3:4b

```

### 3. REST 호출 (Ollama Chat API)
```bash
curl http://localhost:11434/api/chat -d '{
  "model":"gemma3:4b",
  "messages":[
    {"role":"system","content":"You are a translation engine. Output only the translation."},
    {"role":"user","content":"한국어를 자연스러운 영어로 번역: 우리는 색보정을 자동화하고 있습니다."}
  ],
  "options":{"temperature":0.2}
}'
