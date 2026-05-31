# Recruiter Mode

## 목적

현재 문서는 개발자 관점이 강하다. 실제 채용 과정에서는 면접관과 채용 담당자가 짧은 시간 안에 “왜 이 기능이 어려운가”, “왜 실무적인가”, “무엇을 증명하는가”를 이해해야 한다.

Recruiter Mode는 각 기능을 채용 관점으로 요약하기 위한 규칙이다.

## 기능별 Recruiter Summary 템플릿

```markdown
# Recruiter Summary - Feature Name

## 이 기능이 어려운 이유

## 이 기능이 실무적인 이유

## 이 기능이 증명하는 역량

## 실행 화면에서 봐야 할 것

## 코드에서 봐야 할 것

## 문서에서 봐야 할 것

## 어떤 회사에 어필되는가

## 30초 설명

## 3분 설명
```

## Skill System Recruiter Summary

증명하는 역량:

- Data Driven Design
- SOLID
- Runtime Assembly
- Tool 제작
- Editor 확장
- Validation
- Feature Toggle 통합
- Before/After 비교

면접관이 봐야 할 것:

- 하드코딩 Skill이 모듈형 Skill로 바뀌는 과정
- SkillDefinitionSO가 Runtime SkillInstance로 조립되는 구조
- Effect / Target / Condition / Cooldown 분리
- Skill Editor에서 값 변경 후 Runtime에 반영되는 흐름

## Animation Tool Recruiter Summary

증명하는 역량:

- Animation Pipeline 이해
- Bone Hierarchy 이해
- Tool 제작 능력
- DX11 Animation 경험의 Unity 재해석
- Playables API 활용

면접관이 봐야 할 것:

- Clip Preview
- Bone Viewer
- Event Timeline
- Skill Event 연동

## Shader Showcase Recruiter Summary

증명하는 역량:

- HLSL 이해
- URP Shader 구조 이해
- 렌더링 파이프라인 기초
- 시각 효과 구현 능력
- SRP Batcher 고려

면접관이 봐야 할 것:

- 기본 Material과 커스텀 Shader 비교
- 파라미터 변경에 따른 결과 변화
- Feature Module ON/OFF

## Optimization Showcase Recruiter Summary

증명하는 역량:

- 병목 분석
- Profiler 기반 판단
- Object Pooling
- GPU Instancing
- LOD / Culling
- Metrics 기반 비교

면접관이 봐야 할 것:

- 적용 전후 FPS, GC, Draw Call 변화
- Feature Toggle로 최적화 기능을 켜고 끄는 흐름

## 핵심 질문

Codex는 모든 기능마다 반드시 다음 질문에 답해야 한다.

```text
이 기능이 일반 Unity 포트폴리오와 비교해서 어떤 차별성을 만들고 있는가?
```

이 질문에 답하지 못하면 기능을 추가하지 않는다.
