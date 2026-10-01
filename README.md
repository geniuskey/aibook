# AIBook — 인터랙티브 AI 교과서

벡터 하나에서 대규모 언어 모델까지. 공대 학부생을 위한 한국어 신경망·Transformer·LLM 학습 사이트입니다.
13개 챕터, 100개가 넘는 시뮬레이터, 3D 모델(three.js)로 구성되며, MoE·하이브리드 어텐션·FP4·추론 모델·에이전트 등 2026년 동향을 반영합니다. 임베딩 공간과 어텐션 행렬을 직접 끌어 바꿔 보고, 작은 신경망과 언어 모델을 브라우저에서 실제로 학습시킵니다.

## 실행
빌드 과정이 없는 정적 사이트입니다.

```bash
python3 -m http.server 8000   # → http://localhost:8000
```
`index.html`을 브라우저로 바로 열어도 동작합니다. KaTeX, three.js, 폰트는 CDN에서 불러오므로 인터넷 연결이 필요합니다.

## 구성
| 장 | 파일 | 주제 |
|---|---|---|
| 01 | chapters/vector.html | 벡터·내적·코사인 유사도, 행렬 = 선형 변환, 행렬곱, 고차원 직관 |
| 02 | chapters/neuron.html | 퍼셉트론, 활성화 함수, MLP가 공간을 접는 원리, 신경망 플레이그라운드 |
| 03 | chapters/training.html | 손실 함수, 경사하강, 역전파, 옵티마이저, 초기화, 과적합, Muon, 저정밀(FP8·NVFP4) 학습 |
| 04 | chapters/embedding.html | BPE 토큰화, 임베딩 룩업, 3D 임베딩 공간, 벡터 산술, word2vec, Matryoshka 임베딩 |
| 05 | chapters/attention.html | Q·K·V, 어텐션 행렬 직접 편집, 마스크, 멀티헤드, FlashAttention, MLA, 하이브리드 선형 어텐션 |
| 06 | chapters/transformer.html | 위치 인코딩·RoPE, 잔차 스트림, 정규화, FFN, 세분화 MoE, MTP, 2026 블록 비교, 파라미터 계산기 |
| 07 | chapters/llm.html | 언어 모델, 브라우저 학습 문자 LM, 스케일링 법칙, SFT·RLHF·DPO, 추론 모델 개요, 디퓨전 언어 모델 |
| 08 | chapters/generation.html | 온도·top-k·top-p, 빔 서치, KV 캐시, PagedAttention, 추측 디코딩, EAGLE-3 트리 드래프트, 추론 토큰 비용 |
| 09 | chapters/quantization.html | FP/INT 비트 구조, 스케일·영점, 그룹 양자화, SmoothQuant, GPTQ, NVFP4·MXFP4 |
| 10 | chapters/rag.html | 청킹, 벡터 검색, 하이브리드·HNSW, MMR, 프롬프트 조립, 긴 컨텍스트 vs RAG, 에이전트형 RAG |
| 11 | chapters/agent.html | 추론 모델, 테스트타임 계산, RLVR·GRPO, 에이전트 루프, MCP, 컨텍스트 엔지니어링 |
| 12 | chapters/design.html | GPU 메모리 예산, 루프라인, 연속 배칭, 분리 서빙, MoE 서빙, 서빙 플레이그라운드 |
| 13 | chapters/glossary.html | 용어집, 종합 퀴즈 |

공통 코드: `css/style.css`(디자인 토큰, 라이트/다크), `js/common.js`(전역 `AB`: 내비게이션, 캔버스·차트·3D 헬퍼, 벡터·소프트맥스·시드 난수·히트맵 색).
챕터 작성 규칙은 [CONTRIBUTING.md](CONTRIBUTING.md)를 참고하세요.

시뮬레이터의 임베딩·코퍼스·언어 모델은 교육용으로 만든 작은 예시이며, 수치는 단순화한 모델입니다.

배포: GitHub Pages + 커스텀 도메인 `aibook.euiyun.com` (`CNAME`).

## 라이선스

Copyright © 2026 Edwin (geniuskey) 및 AIBook 기여자.

이 프로젝트는 파일 확장자가 아니라 해당 부분의 용도에 따라 다음 라이선스를 적용합니다. 별도 고지가 있는 자료는 해당 고지를 따릅니다.

| 적용 대상 | 라이선스 | 이용 조건 |
|---|---|---|
| JS·CSS·Python·HTML의 실행 코드 | [MIT](LICENSE-MIT) | 수정·재배포·상업적 이용 가능. 저작권 및 라이선스 고지 유지 |
| 교재 본문·그림·문제·해설 | [CC BY 4.0](LICENSE-CC-BY-4.0) | 수업 자료·번역·상업적 교재에 활용 가능. 저작자·출처·라이선스 표시 및 변경 사실 명시 |

HTML·JS 안의 실행 코드와 교육 콘텐츠도 이 구분을 따릅니다. README 및 작성 가이드의 설명 문장은 CC BY 4.0, 문서 안의 실행 코드 예제는 MIT입니다. 상세 적용 범위·재사용 조건·출처 표시 예시·외부 자료 안내는 [LICENSE.md](LICENSE.md)를 참고하세요.
