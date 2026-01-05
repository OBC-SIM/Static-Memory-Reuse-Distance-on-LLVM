# LLVM Reuse Distance Analysis Pass

LLVM 기반의 메모리 재사용 거리(Reuse Distance) 분석 도구입니다. C 코드의 메모리 접근 패턴을 분석하여 캐시 성능 최적화에 활용할 수 있는 정보를 제공합니다.

## Related Publication

**CAAS:Cache Affinity Aware Scheduling Framework for Orbital Edge Computing**  
Jiwoo Shin, Hyeonsoo Jeon, Junyong Park, Jaehyeok Jang, Joonhyouk Jang, Jinman Jung

*The 41st ACM/SIGAPP Symposium On Applied Computing, March 2026*

📄 Paper: (modified after publication)

## 프로젝트 개요

이 프로젝트는 LLVM의 커스텀 패스를 활용하여 프로그램의 메모리 접근 패턴을 분석합니다. 각 메모리 접근에 대한 재사용 거리(Reuse Distance)를 측정합니다.

### 주요 기능
- ✅ C 코드의 메모리 접근 패턴 자동 분석
- ✅ Reuse Distance (RD) 측정 및 통계 제공
- ✅ Docker를 통한 간편한 실행 환경
- ✅ JSON 형식의 분석 결과 출력
- ✅ 포인터 별칭 분석 및 GEP 오프셋 추적

## 🚀 빠른 시작

### 1. Docker 이미지 빌드
```bash
docker build -t llvm-reuse-pass:latest .
```

### 2. 분석할 C 코드 준비
`tasks` 디렉토리에 분석할 C 파일(`.c`)을 배치하세요.

### 3. Docker 컨테이너 실행 및 분석
```bash
docker run -it --rm \
  -v $(pwd):/app \
  llvm-reuse bash

# 컨테이너 안에서 재빌드 (경로 문제 해결)
cd /app
rm -rf build
mkdir build && cd build
cmake ..
make
cd ..

# 분석 실행
python3 rd_analysis_auto.py
```
