@'
# Performance Optimization Analysis

## 기존 DX11 프로젝트에서 확인되는 최적화 요소

### Deferred Rendering

조명 계산을 오브젝트별 Forward 방식으로 반복하지 않고 GBuffer 생성 후 Fullscreen pass에서 처리한다. 많은 동적 조명 또는 후처리 효과를 다룰 때 유리하다.

### MRT

Diffuse, Normal, Depth, PickingWorld, OuterPre 등을 한 번의 Geometry Pass에서 기록한다. 렌더링 단계가 명확해지고 Debug View 구현이 쉽다.

### Alpha Sorting

`RG_BLEND`는 `CAlphaObject::GetViewZ()` 기준으로 정렬 후 렌더링한다. 투명 오브젝트의 기본적인 시각 오류를 줄인다.

### UI Depth Sorting

`RG_UI`는 `CUIObject::GetDepth()` 기준으로 정렬한다.

### Frustum

`CFrustum`이 존재하고 `IsInFrustumWorldSpace`, `IsInFrustumLocalSpace`를 제공한다. GameObject의 `m_bIsInFrustum` 플래그도 존재한다.

### RenderTarget Downsample

Glow 처리에서 half resolution target을 사용한다. Blur 비용을 낮추는 좋은 접근이다.

### Debug RTV

Debug build에서 RenderTarget을 화면에 표시할 수 있는 구조가 있다. 렌더링 디버깅 능력을 보여주는 포인트다.

## 부족하거나 강화할 수 있는 부분

- 범용 Object Pooling 체계가 약하다.
- Layer 충돌 검사가 list 순회 중심이라 대량 객체에서 Broad Phase가 필요하다.
- Resource async loading 구조가 부족하다.
- GPU Instancing / Draw indirect 구조는 명확히 드러나지 않는다.
- CPU/GPU profiler overlay가 없다.

## Unity 포트폴리오 최적화 Showcase 설계

한 씬에서 다음 최적화를 ON/OFF 비교해야 한다.

- LOD Group
- Frustum Culling
- Occlusion Culling
- GPU Instancing
- SRP Batcher
- Object Pooling
- Addressables Async Loading
- Texture MipMap / Compression
- Particle overdraw control
- Animator Culling Mode
- C# GC allocation tracking

## 측정 UI

- FPS
- CPU frame time
- GPU frame time 가능 시 표시
- Batches
- SetPass Calls
- Triangles / Vertices
- GC Alloc per frame
- Loaded Addressables count
- Active pooled object count

## 기술적으로 좋은 시연 방식

단순 토글만 만들지 말고, 토글 전후 수치 변화를 같은 화면에서 보여준다.

예시:

- Projectile 500개 발사: Pooling ON/OFF에 따른 GC와 spike 비교
- 몬스터 200개 배치: LOD/Frustum ON/OFF에 따른 vertex count 비교
- 동일 Mesh 1000개 배치: GPU Instancing/SRP Batcher ON/OFF 비교
- 큰 VFX 여러 개: Overdraw view로 비용 확인

## README에 강조할 문장

이 포트폴리오의 최적화 기능은 성능을 개선했다는 주장보다, 성능 문제를 측정하고 원인을 분해하고 개선 효과를 눈으로 확인하는 클라이언트 개발 역량을 보여주는 데 목적이 있다.
