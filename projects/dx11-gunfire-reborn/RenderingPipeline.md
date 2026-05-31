# Rendering Pipeline Analysis

## 개요

Gunfire Reborn Clone의 렌더러는 `CRenderer` 중심의 RenderGroup 기반 Deferred Rendering 파이프라인이다. GameObject는 LateUpdate 또는 Render 준비 단계에서 자신을 특정 RenderGroup에 등록하고, Renderer는 프레임 말에 그룹별 패스를 순서대로 수행한다.

## RenderGroup

`CRenderer::RENDER_GROUP`은 다음 패스 구성을 가진다.

- `RG_PRIORITY`: Skybox 등 우선 렌더 대상
- `RG_HEIGHT`: Height map 렌더링용 그룹. 현재 일부 주석 처리
- `RG_SHADOW`: Light depth / Shadow map 생성
- `RG_NONBLEND`: GBuffer에 들어가는 일반 불투명 오브젝트
- `RG_NONPICKING`: Picking 제외 불투명 오브젝트
- `RG_NONLIGHT`: Light 연산 없이 바로 렌더링할 대상
- `RG_BLEND`: Alpha sorting 대상
- `RG_UI`: UI depth sorting 대상
- `RG_GLOW`: Glow 추출 대상
- `RG_OUTER`: Outline 대상
- `RG_DISTORTION`: Distortion 대상

## RenderTarget / MRT 구성

Renderer 초기화 시 생성되는 주요 RenderTarget은 다음과 같다.

- `TargetDiffuse`: GBuffer diffuse
- `TargetNormal`: GBuffer normal
- `TargetDepth`: depth reconstruction용 depth 값
- `TargetPickingWorld`: Picking world position
- `TargetOuterPre`: outline pre-pass
- `TargetShade`: light diffuse accumulation
- `TargetSpecular`: specular accumulation
- `TargetLightDepth`: shadow depth
- `TargetFinal`: final color
- `TargetBlurX`: blur intermediate
- `TargetOuter`: outline result
- `TargetGlow`, `TargetGlowCopy`, `TargetGlowCopyBlurX`, `TargetGlowCopyBlurY`, `TargetGlowFinal`: bloom/glow chain
- `TargetDistortion`: screen distortion mask

MRT 구성은 다음과 같다.

- `MRTGameObjects`: Diffuse + Normal + Depth + PickingWorld + OuterPre
- `MRTLightAcc`: Shade + Specular
- `MRTShadow`: LightDepth
- `MRTFinal`: Final
- `MRTBlurX`: BlurX
- `MRTGlow*`: Glow extraction/downsample/blur/final
- `MRTDistortion`: Distortion
- `MRTOuter`: Outline

## 프레임 렌더링 순서

1. Priority render
2. Shadow pass
3. NonBlend GBuffer pass
4. Light accumulation pass
5. Outline pass
6. Final shade/composite pass
7. Optional blur X/Y
8. Glow extraction/copy/blur/final
9. Distortion pass
10. NonLight pass
11. Alpha blend pass with view Z sorting
12. UI pass with depth sorting
13. Debug RTV preview in debug build

## 기술적 가치

이 구조는 Unity 포트폴리오의 Shader Showcase와 Rendering Debug View로 강하게 연결된다.

- Deferred GBuffer 이해
- RenderTexture 기반 Debug View 설계
- Shadow map / Light depth 이해
- Fullscreen pass 합성 이해
- Glow/Bloom 다운샘플 및 Blur 이해
- Distortion mask 합성 이해
- Outline pre-pass 사고
- Alpha sorting 이슈 이해

## Unity 이식 방향

Unity에서는 URP 기반으로 아래처럼 번역하는 것이 현실적이다.

- `ScriptableRendererFeature` / `ScriptableRenderPass`로 Debug/Outline/Distortion pass 작성
- RenderTexture 기반 `DebugViewPanel` 구현
- ShaderGraph와 HLSL Custom Function 병행
- Normal, Depth, Overdraw, Wireframe, Shadow Map을 동시에 표시
- DX11의 RenderGroup 개념은 Unity의 Layer, RenderQueue, RendererFeature, CommandBuffer로 매핑

## 포트폴리오에서 강조할 포인트

단순히 예쁜 셰이더를 나열하지 말고, 각 효과에 대해 다음을 함께 보여줘야 한다.

- 입력 데이터: Depth, Normal, Noise, Mask, ViewDir, Fresnel 등
- 렌더링 패스: Opaque, Transparent, Fullscreen, PostProcess
- 비용: DrawCall, SetPass, Texture Sample 수, Overdraw
- 최적화 토글: SRP Batcher, GPU Instancing, LOD, Culling
