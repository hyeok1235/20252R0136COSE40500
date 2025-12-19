# LLM Post-Training: A Deep Dive into Reasoning Large Language Models

**Type:** Survey Paper

**Core Insight:** LLM post-training에 대한 종합적인 survey - Fine-tuning, RL, Test-time Scaling을 모두 커버

## Abstract

- Pretraining: 넓은 범위의 언어 베이스 학습
- Post-training: 지식 정제, reasoning/정확도 향상, 사용자 의도 및 윤리적 alignment

## Post-Training 3가지 분류

| Category | Description | Challenges |
|----------|-------------|------------|
| **Fine-Tuning** | 특정 task에 LLM 맞춤화 | Overfitting, 높은 연산 비용, generalization 약화 |
| **Reinforcement Learning** | Continuous action space, subjective/delayed reward | 복수 objective 핸들링 |
| **Test-Time Scaling** | Inference 시 동적 연산 자원 조절 | Adaptability 향상 |

---

## 2. Background

- **기본**: Maximum Likelihood Estimation (MLE) - 다음 토큰 예측
- **문제**: 긴 sequence에서 일관성/문맥 유지 어려움
- **해결**: RL로 return (discounted reward sum) 최대화

### Early RL Methods

| Method | Description |
|--------|-------------|
| **REINFORCE** | Action으로부터 얻은 reward로 policy 조정 |
| **MIXER** | MLE → RL로 점진적 가중치 이동 |
| **SCST** | Sampled vs greedy output 차이 최소화 |
| **MRT** | Output 분포에 대해 risk 직접 최소화 |
| **A2C/A3C** | Actor-Critic으로 variance 감소, 안정적 학습 |

---

## 3. Reinforced LLMs

### 3단계 프로세스

1. **SFT**: Supervised dataset으로 baseline 구축
2. **RM Training**: Human preference 라벨링 학습
3. **RL Fine-Tuning**: Reward model output 최대화

### 3.1 Reward Modeling

| Type | Description |
|------|-------------|
| **Explicit** | 직접적인 reward structure로 학습 |
| **Implicit** | Latent reward 구조 간접 파악 |
| **Outcome (ORM)** | 결과만 보고 학습 (short-response 적합) |
| **Process (PRM)** | Step별 피드백 및 reward 부여 |
| **Iterative** | Reward model 반복 refine |

### 3.2 Policy Optimization Methods

| Method | Key Feature |
|--------|-------------|
| **ORPO** | Pairwise preference로 직접 업데이트 (RM 불필요) |
| **PPO** | 변화폭 제한으로 안정성 확보 |
| **RLHF** | Human feedback으로 reward function 생성 |
| **RLAIF** | 더 좋은 LLM output으로 preference label 생성 |
| **TRPO** | 실제 최적화 문제 해결 (계산량 높음) |
| **DPO** | 선호도를 loss function에 직접 반영 |
| **OREO** | Sparse final + fine-grained step reward |
| **GRPO** | 여러 output 상대적 reward (DeepSeek-R1) |

### 3.3 Pure RL Based Refinement

1. **Cold-Start RL**: 소량 고품질 데이터로 초기 base
2. **Rejection Sampling**: 고품질 response 필터링
3. **Reasoning-Oriented RL**: GRPO로 structured output 선호
4. **Second RL Stage**: Human alignment 2차 학습
5. **Distillation**: 작은 모델로 능력 전달

---

## 4. Supervised Finetuning

| Type | Description |
|------|-------------|
| **Instruction** | Prompt-completion pair 학습 |
| **Dialogue** | Multi-turn context 유지 |
| **CoT Reasoning** | 단계별 추론 과정 학습 |
| **Domain-Specific** | 특정 도메인 curated corpus |
| **Distillation** | Teacher → Student 지식 전달 |
| **Preference/Alignment** | Human-labeled data로 value 고려 |
| **Efficient (PEFT)** | 일부 파라미터만 학습 (LoRA 등) |

---

## 5. Test-Time Scaling Methods

### Search-Based

| Method | Description |
|--------|-------------|
| **Beam Search** | 여러 reasoning chain explore, 최고 likelihood path |
| **Best-of-N** | Full solution N개 생성 후 최선 선택 |
| **Compute-Optimal** | 난이도별 동적 자원 할당 (BoN 대비 4배 효율) |

### Prompting-Based

| Method | Description |
|--------|-------------|
| **Chain-of-Thought** | "Let's think step by step" |
| **Self-Consistency** | Majority voting (다양한 temperature) |
| **Tree-of-Thoughts** | Branching reasoning (lookahead, backtracking) |
| **Graph-of-Thoughts** | 그래프 형태 (aggregation, refinement, generation) |

### Advanced

| Method | Description |
|--------|-------------|
| **Confidence-based** | Confidence로 sampling/branching 결정 |
| **Search Against Verifiers** | ORM/PRM으로 candidate 평가 |
| **Self-Improvement** | Self-evaluation + revision 반복 |
| **MCTS** | Random simulation으로 decision tree 구축 |
| **Chain-of-Action-Thought** | Self-improve 과정 포함 2-stage 학습 |

### Pretraining vs TTS

| Aspect | Pretraining | Test-Time Scaling |
|--------|-------------|-------------------|
| 강점 | 핵심 능력 구축 | 기존 모델 성능 향상 |
| 연산 | 높음 (일회성) | 낮음 (동적 할당) |
| 권장 | Hybrid 접근 결합 |

---

## 7. Future Directions

| Challenge | Description |
|-----------|-------------|
| **Catastrophic Forgetting** | 업데이트 시 예전 지식 망각 |
| **Safe Fine-tuning** | 민감 정보로 인한 취약점 |
| **Human Feedback 한계** | 주관적, 비용 높음 → AI feedback |
| **TTS 효율성** | 난이도별 연산 자원 배치 (메타 인지) |
| **Reward Modeling** | Sparse reward → step-wise reward |
| **Efficient RL** | Hybrid 접근 (SL 안정성 + RL 탐색) |
| **Privacy-Preserving** | E2E 암호화, noise 추가, federated learning |
| **Multi-Model Systems** | Backprop 없는 multi-agent 협력 |
| **Multimodal RL** | 계층적 구조와 truncation 전략 |
| **Overthinking** | 길이 패널티, MCTS+GRPO 결합 |

---

## 8. Conclusion

| Technique | Main Benefit |
|-----------|--------------|
| Fine-tuning | Efficiency 개선, Alignment |
| RL | 추론/계획/일반화 능력 향상 |
| TTS | 더 복잡한 문제 해결 |

Survey는 현재 LLM의 한계와 open challenges도 포괄적으로 서술함.
