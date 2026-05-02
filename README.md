# Robot Intelligence Lectures

**APRL, DGIST · RT604 Spring 2026**  
Giseop Kim

---

대학원 강의 자료 모음입니다. 각 강의는 Welch Labs 영상을 기반으로 재구성한 슬라이드와 발표 대본으로 구성됩니다.

## 강의 목록

### Lecture 01 · Vision-Language-Action 모델
**RT2에서 π₀까지, 그리고 그 너머**

| 파일 | 설명 |
|---|---|
| [pdf/lec01_vla_lecture.pdf](pdf/lec01_vla_lecture.pdf) | 강의 슬라이드 |
| [pdf/lec01_vla_script.pdf](pdf/lec01_vla_script.pdf) | 발표 대본 |
| [tex/lec01_vla_lecture.tex](tex/lec01_vla_lecture.tex) | 슬라이드 소스 |
| [tex/lec01_vla_script.tex](tex/lec01_vla_script.tex) | 대본 소스 |

원본 영상: [Inside the World's Smartest Robot Brain \[VLA\]](https://www.youtube.com/watch?v=2mrGMMmrVNE) — Welch Labs

**커버 내용**
- SayCan → RT1 → PaLM-E → RT2 진화 경로
- π₀ 아키텍처: PaliGemma + Action Expert + Flow Matching
- Attention head의 언어-시각 grounding
- KV cache 공유를 통한 두 모듈 결합
- World model 패러다임과 VLA의 한계

---

### Lecture 02 · LeCun의 JEPA와 세계 모델
**LLM 너머의 로봇 지능을 향해**

| 파일 | 설명 |
|---|---|
| [pdf/lec02_vla_lecture.pdf](pdf/lec02_vla_lecture.pdf) | 강의 슬라이드 |
| [pdf/lec02_vla_script.pdf](pdf/lec02_vla_script.pdf) | 발표 대본 |
| [tex/lec02_vla_lecture.tex](tex/lec02_vla_lecture.tex) | 슬라이드 소스 |
| [tex/lec02_vla_script.tex](tex/lec02_vla_script.tex) | 대본 소스 |

원본 영상: [Yann LeCun's Billion Dollar Bet](https://youtu.be/kYkIdXwW2AE?si=asUnIL7EKPRMRwDp) — Welch Labs

**커버 내용**
- CNN → 자기지도학습의 역사 (케이크 슬라이드)
- GPT 계보: 트랜스포머와 다음 토큰 예측이 성공한 이유
- 생성형 방식의 흐릿함 문제와 이산 vs 연속 출력 공간
- 결합 임베딩 + 샴 신경망: 생성 없이 표현 배우기
- 표현 붕괴와 Barlow Twins (교차상관 행렬 = 단위 행렬)
- DINO v3: 자기지도학습이 지도학습을 따라잡다 (ImageNet 88.4%)
- JEPA 아키텍처: 인코더 × 2 + 예측기 → 세계 모델
- 행동 조건화 (V-JEPA 2) → 고전 최적 제어 + 학습된 표현

---

## 원본 대본

| 파일 | 내용 |
|---|---|
| [md/lec01_vla_script.md](md/lec01_vla_script.md) | Lec01 원본 한국어 대본 |
| [md/lec02_vla_script.md](md/lec02_vla_script.md) | Lec02 원본 한국어 대본 |

## 빌드 방법

```bash
docker run --rm \
  -v "$(pwd):/data" \
  texlive/texlive:latest \
  bash -c "
    apt-get update -qq && \
    apt-get install -y -qq fonts-noto-cjk fonts-noto-cjk-extra fonts-dejavu && \
    fc-cache -f && \
    mkdir -p /data/__build && \
    cd /data/tex && \
    xelatex -interaction=nonstopmode -output-directory=/data/__build lec02_vla_lecture.tex && \
    xelatex -interaction=nonstopmode -output-directory=/data/__build lec02_vla_lecture.tex && \
    cp /data/__build/*.pdf /data/pdf/
  "
```

**요구사항**: Docker, XeLaTeX (`texlive/texlive:latest`), Noto CJK 폰트

## 라이선스

강의 자료는 교육 목적으로 작성되었습니다.  
원본 영상 저작권은 [Welch Labs](https://www.youtube.com/@WelchLabs)에 있습니다.
