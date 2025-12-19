# Do I Know This Entity? Knowledge Awareness and Hallucinations in Language Models

**Venue:** ICLR 2025

**Core Insight:** 모델 내부 공간에는 모델이 무엇을 알고 있고 무엇을 모르는지가 나타나는 부분이 존재한다.

## Abstract

- Hallucination은 심각한 문제이나 예측 방법은 잘 이해되지 않음
- **Sparse Autoencoder (SAE)** 를 사용하여 entity 인지 여부가 핵심임을 발견
- Known entity → steering으로 제거 가능 / Unknown entity → 답변 거부 유도 가능
- Base 모델의 SAE가 chat 모델에도 적용됨 → chat finetuning이 SAE 메커니즘과 유사
- SAE direction이 downstream head의 attention을 방해할 수 있음

## Key Contributions

1. SAE를 통해 entity recognition direction 발견
2. Known/Unknown entity latent가 knowledge refusal에 인과적 영향
3. Base model → Chat model로의 transferability 확인
4. Uncertainty direction으로 정답/오답 구분 가능

## Methodology

### Sparse Autoencoders (SAE)

- Model representation x ∈ R^d를 sparse latent a(x) ∈ R^(d_SAE)로 분해
- Dictionary learning: 중첩된 feature들을 분리
- W_dec의 latent 벡터 선형 결합 → activation steering과 동일 효과

### Dataset Construction

- 4개 entity 유형: 농구 선수, 영화, 도시, 노래 (Wikidata 기반)
- Template: entity type, name, relation, attribute
- 2개 이상 attribute 정답 시 "known entity"로 분류

## Results

### Entity Recognition Directions (Section 4)

- 중간 layer에서 separation score 최고 → known/unknown 구분 최적
- 초기 layer: 특화된 것들 낮은 품질 이해
- 중간 layer: general한 것들 고품질 이해
- 후반 layer: next token prediction에 overfitting
- Cutoff 이후 데이터: unknown latent ↑, known latent ↓

### Causal Effects on Knowledge Refusal (Section 5)

| Steering | Effect on Refusal |
|----------|-------------------|
| Unknown latent ↑ | Refusal 증가 |
| Known latent ↑ | Refusal 감소 |
| Orthogonalized (unknown 차단) | Refusal 크게 감소 |

- Gemma 2 9B, Llama 3.1 8B에서 동일 패턴 확인

### Mechanistic Analysis (Section 6)

**Attention Regulation:**
- Known entity latent steering → attention score ↑
- Unknown entity latent steering → attention score ↓
- Entity recognition latent는 attention의 "key" 연산과 연관

**Direct Query:**
- Unknown latent ↑ → "모른다" 응답 증가
- Known latent ↑ → "안다" 응답 증가

### Uncertainty Directions (Section 7)

- End-of-instruction 토큰에 질문 관련 정보 집중
- Unknown latent activation: 오답 시 평균적으로 더 높음
- Uncertainty 관련 토큰 activation 증가 확인

## Conclusions

- SAE로 entity 인지 여부를 나타내는 internal direction 발견
- Base → Chat model transferability 확인
- Entity recognition을 활용한 steering 방법 제시
- 정답/오답 구분에도 활용 가능
