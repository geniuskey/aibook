# AIBook — 인터랙티브 AI 교과서

벡터 하나에서 대규모 언어 모델까지. 공대 학부생을 위한 한국어 신경망·Transformer·LLM 학습 사이트입니다.
12개 챕터, 80개의 시뮬레이터, 3D 모델(three.js)로 구성됩니다. 임베딩 공간과 어텐션 행렬을 직접 끌어 바꿔 보고, 작은 신경망과 언어 모델을 브라우저에서 실제로 학습시킵니다.

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
| 03 | chapters/training.html | 손실 함수, 경사하강, 역전파, 옵티마이저, 초기화, 과적합 |
| 04 | chapters/embedding.html | BPE 토큰화, 임베딩 룩업, 3D 임베딩 공간, 벡터 산술, word2vec |
| 05 | chapters/attention.html | Q·K·V, 어텐션 행렬 직접 편집, 마스크, 멀티헤드, FlashAttention |
| 06 | chapters/transformer.html | 위치 인코딩·RoPE, 잔차 스트림, 정규화, FFN, MoE, 파라미터 계산기 |
| 07 | chapters/llm.html | 언어 모델, 브라우저 학습 문자 LM, 스케일링 법칙, SFT·RLHF·DPO |
| 08 | chapters/generation.html | 온도·top-k·top-p, 빔 서치, KV 캐시, PagedAttention, 추측 디코딩 |
| 09 | chapters/quantization.html | FP/INT 비트 구조, 스케일·영점, 그룹 양자화, SmoothQuant, GPTQ |
| 10 | chapters/rag.html | 청킹, 벡터 검색, 하이브리드·HNSW, MMR, 프롬프트 조립 |
| 11 | chapters/design.html | GPU 메모리 예산, 루프라인, 연속 배칭, 병렬화, 서빙 플레이그라운드 |
| 12 | chapters/glossary.html | 용어집(125개), 종합 퀴즈(20문항) |

공통 코드: `css/style.css`(디자인 토큰, 라이트/다크), `js/common.js`(전역 `AB`: 내비게이션, 캔버스·차트·3D 헬퍼, 벡터·소프트맥스·시드 난수·히트맵 색).
챕터 작성 규칙은 [CONTRIBUTING.md](CONTRIBUTING.md)를 참고하세요.

시뮬레이터의 임베딩·코퍼스·언어 모델은 교육용으로 만든 작은 예시이며, 수치는 단순화한 모델입니다.

배포: GitHub Pages + 커스텀 도메인 `aibook.euiyun.com` (`CNAME`).
