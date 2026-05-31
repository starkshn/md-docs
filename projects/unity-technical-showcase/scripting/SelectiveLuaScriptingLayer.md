# Selective Lua Scripting Layer

## 목적

Unity Technical Showcase의 기본 구현 언어는 C#이다. 모든 Core Framework, ModuleHub, Skill System, Tool System, Comparison System, Metrics System은 C#으로 구현한다.

Lua는 전체 게임 로직을 대체하는 메인 구조가 아니다. Lua는 특정 기능의 확장 포인트로만 사용한다.

목표는 다음과 같다.

- C# 기반 안정적인 Core Framework 유지
- 일부 Gameplay Logic만 Lua로 교체 가능하게 구성
- Skill Effect, Condition, Trigger, Formula 같은 작은 단위 로직을 Lua로 확장
- 런타임 중 데이터 기반으로 Script Module을 연결
- 라이브 서비스에서 Hotfix / Script Layer 개념을 이해하고 있음을 보여주기

## 적용 대상

Lua 적용 후보:

- Skill Damage Formula
- Skill Condition
- Buff Trigger
- Effect Parameter Calculation
- AI Test Behavior
- Debug Command

Lua를 적용하지 않을 대상:

- ModuleHub
- Core Framework
- Rendering
- Animation Tool Core
- Editor Tool Core
- Optimization System
- Comparison Framework

## 우선순위

Selective Lua Scripting Layer는 MVP 필수 기능이 아니다. Skill System과 Skill Tool이 안정화된 이후 확장 기능으로 구현한다.

우선순위:

1. Skill System
2. Skill Tool
3. Before / After Comparison
4. ModuleHub
5. Selective Lua Scripting Layer

## 권장 구조

C# Core:

```text
NY_Core_ModuleHub
NY_Skill_SystemModule
NY_Skill_Factory
NY_Skill_Instance
NY_Skill_EffectModule
NY_Skill_ConditionModule
```

Lua Script:

```text
damage_formula.lua
burn_condition.lua
buff_trigger.lua
```

C#에서 Lua 호출 흐름:

```text
NY_Skill_Instance
 -> NY_Scripting_Gateway
 -> NY_Scripting_LuaRuntime
 -> Lua Script
 -> NY_Scripting_Result 반환
```

## 핵심 원칙

- Lua는 C# 구조를 침범하지 않는다.
- Lua는 C# 모듈의 확장 지점에서만 실행된다.
- Lua Script가 실패해도 C# Core Framework가 깨지면 안 된다.
- Lua 실행은 Gateway를 통해서만 접근한다.
- Lua 호출 결과는 반드시 `NY_Scripting_Result`로 감싼다.
- 오류, Timeout, Metrics, Debug Log를 남긴다.

## 필수 설계 요소

1. Script Gateway
2. Lua Runtime Wrapper
3. Script Execution Context
4. Script Result
5. Error Handling
6. Timeout / Safe Execution
7. Debug Log
8. Metrics
9. Before / After 비교
10. Blog Draft

## 추천 클래스명

```text
NY_Scripting_Gateway
NY_Scripting_LuaRuntime
NY_Scripting_Context
NY_Scripting_Result
NY_Scripting_ErrorReporter
NY_Scripting_Metrics
```

## Skill System 연동 예시

Before:

```text
C# Fixed Damage Formula
```

After:

```text
Lua Damage Formula Script
```

비교 항목:

- 데미지 결과
- 실행 시간
- 에러 여부
- 스크립트 교체 가능 여부
- C# 코드 수정 여부

## 데이터 흐름

1. `NY_Skill_Instance`가 Damage Formula 실행을 요청한다.
2. ScriptableObject 또는 Skill Definition에서 Lua Script Id를 확인한다.
3. `NY_Scripting_Gateway`가 실행 가능 여부를 검사한다.
4. `NY_Scripting_Context`에 caster, target, skill level, base damage 등 실행 데이터를 담는다.
5. `NY_Scripting_LuaRuntime`이 Lua Script를 실행한다.
6. 실행 결과를 `NY_Scripting_Result`로 반환한다.
7. 오류가 있으면 `NY_Scripting_ErrorReporter`가 기록한다.
8. `NY_Scripting_Metrics`가 실행 시간, 성공/실패 횟수, Timeout 여부를 기록한다.
9. Comparison / Metrics Panel에서 C# Fixed Formula와 Lua Formula를 비교한다.

## 안전 실행 규칙

- Lua Runtime 직접 접근 금지
- Script Gateway 우회 금지
- 실행 Timeout 적용
- 예외 발생 시 C# 기본 로직으로 fallback
- Script Result에 success / errorCode / value / elapsedMs 포함
- Debug Log와 Metrics 기록
- Hotfix 개념은 보여주되, Core Framework 교체는 허용하지 않음

## Before / After Showcase

Before:

- C# 코드에 고정된 Damage Formula
- 스킬 수식 변경 시 C# 코드 수정 필요
- 런타임 교체 어려움

After:

- Lua Script로 Damage Formula 교체
- C# Core 수정 없이 Script 교체 가능
- 실행 결과, 실행 시간, 에러 여부 비교 가능
- 라이브 서비스 Hotfix / Script Layer 개념 설명 가능

## 기술 블로그 포인트

- Unity C# Core 위에 Lua Script Layer를 얹는 이유
- Lua를 전체 게임 로직으로 쓰지 않고 선택적 확장 포인트로 제한한 이유
- Skill Damage Formula를 C# 고정 방식에서 Lua Script 방식으로 바꾸기
- Script Gateway와 Safe Execution 설계
- Lua Script 실패 시 C# Core를 보호하는 구조
- 라이브 서비스 Hotfix 경험과 포트폴리오 연결

## 면접 설명 포인트

이 기능의 핵심은 “Lua를 쓸 줄 안다”가 아니다. C# Core Framework를 안정적으로 유지하면서, 변경 가능성이 높은 작은 Gameplay Logic만 Script Layer로 분리할 수 있다는 점이다.

면접에서는 다음처럼 설명한다.

```text
Core Framework와 Skill Runtime은 C#으로 유지했습니다. Lua는 Damage Formula, Condition, Trigger처럼 라이브 중 수정 가능성이 높은 작은 단위에만 제한적으로 적용했습니다. Lua 호출은 NY_Scripting_Gateway를 통과하고, Result/Error/Timeout/Metrics를 모두 기록해 Script 실패가 Core Framework로 전파되지 않게 설계했습니다.
```
