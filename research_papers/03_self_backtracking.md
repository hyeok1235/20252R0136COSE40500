# Step Back to Leap Forward: Self-Backtracking for Boosting Reasoning of Language Models

**Core Insight:** Backtracking 과정을 학습시켜 LLM의 추론 성능을 높인다.

## Abstract

- Slow-thinking mechanism → Level 2 AGI Reasoner에 근접
- **문제점**: Overthinking, 외부 모델 과의존
- **해결책**: 탐색 과정 내재화 → Self-Backtracking
- **결과**: Slow-thinking을 fast-thinking으로 내재화, 추론 능력 + 효율성 향상

## Key Contributions

1. Backtracking 능력을 LLM에 내재화
2. 외부 모델 의존 없이 동적 탐색 가능
3. Slow-thinking → Fast-thinking 전달 (Self-Improvement)

---

## 1. Introduction

### 기존 방법의 문제점

| Problem | Description |
|---------|-------------|
| **Overthinking** | 쉬운 문제에서도 과도한 연산 |
| **외부 의존성** | 외부 모델 사용으로 어려운 문제에서 성능 제한 |

### Self-Backtracking의 장점

1. 불필요한 백트래킹 방지 → Overthinking 감소
2. 외부 모델 의존 제거

---

## 3. Preliminary

### Problem Setup (MDP)

- Reasoning 문제를 **Markov Decision Process**로 모델링
- State → Action → Next State (with Reward)
- Solution = Trajectory (state-action sequence)

### Backtracking

- Tree 구조에서 solution 탐색
- 핵심: 언제(when), 어디로(where) 백트래킹할지 학습

---

## 4. Self-Backtracking Framework

### 3단계 구성

| Stage | Description |
|-------|-------------|
| **Training** | 최적화 목표와 포맷에 맞는 데이터셋 구성 |
| **Inference** | 외부 도구 없이 백트래킹 기반 탐색 |
| **Self-Improvement** | Slow-thinking 결과로 fast-thinking 학습 |

### 4.1 Learn to Backtrack

**데이터셋 구성:**
1. 최적 solution에서 일부 추출
2. Error action 추가
3. `<backtrack>` 토큰 삽입

**Loss 설계:**
- Optimal solution 찾기 + `<backtrack>` 토큰 예측
- Error 예측 loss는 제외 (목표: 잘못된 path 회피)

**특성:** 한 번의 백트래킹 학습 → 재귀적으로 multiple-step 백트래킹 가능

### 4.2 Inference with Backtracking

| Step | Description |
|------|-------------|
| **① Expansion** | N개 예측, `<backtrack>` 유무로 분류 |
| **② Backtracking** | route(n)개 선택, 한 step 전으로 돌아가 재확장 |
| **③ Selection** | Negative perplexity 기준 최고 점수 path 선택 |

### 4.3 Self-Improvement

1. Slow-thinking으로 데이터 생성
2. 정확한 데이터 선별
3. SFT로 fast-thinking 모델 학습

---

## 5. Experiments

### Dataset: Countdown Task

**Training Set:** 최적 solution + backtracking 데이터

**Test Set:**
1. 기존 target의 새로운 조합
2. 완전히 새로운 target

### Error Types (with `<backtrack>` token)

| Type | Description |
|------|-------------|
| **Exploration Errors** | DFS 탐색 중 올바르지 않은 solution |
| **Computational Errors** | 계산 실수 |
| **Rule Violations** | 불가능한 연산자 사용 |

### Main Results

- **b** = backtracking 가능 횟수
- **N** = reasoning path 개수

**Findings:**
- Self-Backtracking → Reasoning 능력 크게 향상
- Self-Improve 가능 확인
- Slow-thinking → Fast-thinking 전달 성공

### Analysis

| Finding | Detail |
|---------|--------|
| Backtracking 유무 | Dramatic 차이 |
| Backtracking 횟수 증가 | 큰 성능 향상 없음 |
| N 증가 | "Not reached target" 감소, 연산 실수 증가 |

---

## 6. Conclusion

- 탐색 과정과 백트래킹을 내재화하지 못한 기존 추론 모델의 문제 해결
- Overthinking 문제 해결
- 외부 도구 의존 제거

### Limitations & Future Work

- General reasoning task 검증 필요
- Scale up 필요
