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

## 라이선스

Copyright © 2026 Edwin (geniuskey) 및 AIBook 기여자.

이 프로젝트는 자료의 종류에 따라 다음 라이선스를 적용합니다. 별도 고지가 있는 자료는 해당 고지를 따릅니다.

| 적용 대상 | 라이선스 | 이용 조건 |
|---|---|---|
| JS·CSS·Python·HTML의 실행 코드 | [MIT](LICENSE) | 수정·재배포·상업적 이용 가능. 저작권 및 라이선스 고지 유지 |
| 교재 본문·그림·문제·해설 | [CC BY 4.0](LICENSE-CONTENT) | 수업 자료·번역·상업적 교재에 활용 가능. 저작자·출처·라이선스 표시 및 변경 사실 명시 |

`js/`, `css/`, HTML의 페이지 구조·스크립트·스타일, 교재에 포함된 실행 가능한 코드 예제와 향후 추가되는 Python 코드는 MIT를 적용합니다. 개발·기여 안내인 `README.md`, `CONTRIBUTING.md`도 MIT를 적용합니다.

`index.html`, `chapters/*.html`에 포함된 교재 본문·수식·그림(인라인 SVG 및 시뮬레이터가 그리는 교육용 도표 포함)·문제·해설은 CC BY 4.0을 적용합니다. 그림을 생성하는 실행 코드는 MIT, 그 결과인 교재 그림은 CC BY 4.0을 적용합니다. 프로젝트 자체 제작 아이콘(`favicon.svg`, `favicon.ico`, `apple-touch-icon.png`)도 CC BY 4.0을 적용합니다. HTML 파일 전체를 재배포하는 경우 코드와 교재 내용에 각각 적용되는 고지를 함께 유지하세요.

교재 내용의 출처 표기 예시(수정한 경우 실제 변경 사항을 덧붙이세요):

> AIBook — 인터랙티브 AI 교과서, Edwin (geniuskey) 및 AIBook 기여자, © 2026. 출처: https://aibook.euiyun.com/ · CC BY 4.0: https://creativecommons.org/licenses/by/4.0/ · 변경 사항: 일부 번역 및 그림 수정.

KaTeX, three.js, 외부 폰트 등 제3자 자료는 각 저작권자의 라이선스를 따르며, 위 라이선스로 재허가하지 않습니다. 교재를 비롯한 자료는 각 라이선스의 보증 부인 및 책임 제한 조건에 따라 제공됩니다.
