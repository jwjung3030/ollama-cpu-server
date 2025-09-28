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
git clone -b feature/ollama-test-client --single-branch https://github.com/jwjung3030/ollama-cpu-server.git
cd ollama-cpu-server

```

### 실행 패턴

```bash
1) 둘 다 켜서 교차 접속 테스트 (권장)
docker compose --profile server --profile test up -d --build
docker exec -it ollama ollama pull gemma3:4b
docker exec -it ollama-test python /app/translate.py "강아지가 잔디밭을 뛰어다닌다."

2) 서버만 운영(개발/배포용)
docker compose --profile server up -d
# 필요 시 호스트에서 curl로 점검
curl -s http://localhost:11434/api/tags


3) 테스트 컨테이너만 (외부/공용 Ollama 서버에 붙일 때)
# 공용 서버가 10.0.0.5:11434 라면
docker compose --profile test run --rm \
  -e OLLAMA_HOST=http://10.0.0.5:11434 \
  -e OLLAMA_MODEL=gemma3:4b \
  ollama-test python /app/translate.py "…문장…"

```
