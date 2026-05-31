# Lua Skill Formula Experiment

## 목적

Selective Lua Scripting Layer를 바로 포트폴리오 본 구조에 넣지 않고, Skill Damage Formula 미니 실험으로 먼저 검증한다.

## 실험 목표

C# Fixed Damage Formula와 Lua Damage Formula를 비교한다.

Before:

```text
finalDamage = baseDamage + attackPower * ratio
```

After:

```lua
return baseDamage + attackPower * ratio + skillLevel * 10
```

## 실험 범위

- Lua Script 하나 실행
- Context에 baseDamage, attackPower, ratio, skillLevel 전달
- number 결과 반환
- 실행 시간 측정
- Script 오류 발생 시 C# fallback
- Metrics Panel에 결과 표시

## 성공 기준

- C# Formula와 Lua Formula 결과를 비교할 수 있다.
- Lua Script를 교체해도 C# Skill Instance 코드를 수정하지 않는다.
- Lua Script 오류가 발생해도 Skill System이 멈추지 않는다.
- 실행 시간과 에러 여부를 Metrics로 표시한다.

## 구현 후보

```text
NY_Scripting_Gateway
NY_Scripting_LuaRuntime
NY_Scripting_Context
NY_Scripting_Result
NY_Scripting_ErrorReporter
NY_Scripting_Metrics
NY_Skill_LuaFormulaAdapter
```

## 제외 범위

- 전체 스킬 로직 Lua화
- Animation / Rendering / Editor Tool Lua화
- 복잡한 Lua Debugger
- 서버 Hotfix 시스템

## Blog Draft 제목 후보

- Unity C# Skill System에 Lua Damage Formula만 선택적으로 붙여보기
- C# Core를 유지하면서 Lua Script Layer를 안전하게 붙이는 방법
- 라이브 서비스 Hotfix 관점에서 본 Selective Lua Scripting Layer
