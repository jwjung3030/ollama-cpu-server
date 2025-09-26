# Ollama + Gemma 3 CPU Translation Server

이 저장소는 **[Ollama](https://github.com/ollama/ollama)** 런타임 위에서 **Google Gemma 3** 모델을 CPU 환경에서 실행하여  
간단한 **번역 서버**(REST API)를 구축하는 예제를 제공합니다.

## 🚀 특징
- **CPU 기반 실행**: GPU 없이도 Gemma 3 모델 구동 가능 (느릴 수 있음).
- **간단한 배포**: `docker-compose up` 만으로 서버 실행.
- **REST API 지원**: `curl` 또는 다른 클라이언트로 번역 요청 가능.
---

## 📦 설치 방법

### 1. 저장소 클론
```bash
git clone https://github.com/jwjung3030/ollama-cpu-server
cd ollama-gemma3-cpu-server
