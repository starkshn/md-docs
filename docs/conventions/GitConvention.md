# Git Convention

## 원칙

Commit은 기능 단위가 아니라 설명 가능한 기술 단위로 수행한다.

## 좋은 예

```text
feat: implement runtime skill assembly
feat: add effect-target-condition separation
feat: add skill validation framework
feat: implement feature toggle architecture
docs: add module naming convention
docs: add architecture governance process
```

## 나쁜 예

```text
feat: update
feat: fix
feat: skill system complete
```

## 문서 작업 규칙

- 설계 변경은 docs commit으로 남긴다.
- 코드 구현과 문서 대규모 변경은 가능하면 분리한다.
- Codex가 작업한 경우 `CODEX_SESSION_NOTES.md`에 요약을 남긴다.
