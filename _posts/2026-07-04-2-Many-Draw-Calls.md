---
layout: single
title: "2 Many Draw Calls"
date: 2026-07-04
categories: [tech, unity]
tags: [unity, rendering, optimization]
---

# "Draw Call이 너무 많습니다"

Draw Call 이 많을 때 어떻게 해야할까? Fam, let's break down!

![E0B92587-BD06-4D73-A6C6-C70CA1073D09_4_5005_c](/assets/images/2026-07-04-2-Many-Draw-Calls/E0B92587-BD06-4D73-A6C6-C70CA1073D09_4_5005_c.jpeg)

## Draw Call 이란?

CPU는 GPU에게 오브젝트를 렌더링하라고 명령을 내린다. 이때 오브젝트의 수에 따라 내리는 명령의 가짓수를 draw call이라 칭한다.

## HTS (How To Solve)

1. Profiler에서 Rendering 병목인지 확인한다.

2. Stats 또는 Profiler(Rendering)에서
**Draw Calls, Batches, SetPass Calls**를 확인한다.

3. **Frame Debugger**로 어떤 오브젝트가 Draw Call을 발생시키는지 분석한다.

4. 원인에 따라 최적화를 적용한다.

만약 UI 가 원인이라면 : **Sprite Atlas**를 활용하여 텍스쳐를 묶고, Canvas가 불필요하게 나누어져있는지 확인

만약 3D 오브젝트가 원인이라면 : **Culling**(애초에 그릴 대상을 줄이자), **Batching**(한 번에 묶어서 그리자)

## Culling 이 도대체 뭐길래?

> Culling : 카메라에 보이지 않는 오브젝트는 렌더링하지 않는 것

**Occlusion Culling** : 카메라 시야 안에 있지만, 다른 불투명 오브젝트에 가려져서 보이지 않는 부분의 데이터를 Bake하여 런타임에 렌더링하지 않는 최적화 기법.

Frustum Culling : 카메라 시야 밖에 있는 오브젝트를 렌더링 하지 않는 기법.

Occlusion Culling을 원활하게 사용하기 위해서는 

1. Occluder(가리는 object)와 Occludee(가려지는 Object)를 Static으로 설정하고
2. 사전에 Occlusion을 **baked**해둬야 한다.

![Screenshot 2026-07-09 at 8.15.12 PM](/assets/images/2026-07-04-2-Many-Draw-Calls/Screenshot%202026-07-09%20at%208.15.12%E2%80%AFPM.png)

![Screenshot 2026-07-09 at 8.15.19 PM](/assets/images/2026-07-04-2-Many-Draw-Calls/Screenshot%202026-07-09%20at%208.15.19%E2%80%AFPM.png)

### Bake는 또 뭐고?

> Bake : 실행 전에 미리 계산한 결과를 저장해 두고, 런타임에서는 그 결과를 사용하는 최적화 기법

즉, **런타임의 계산량을 줄이기 위해**
에디터에서 미리 계산 가능한 데이터를 저장해두는 과정이다.

Unity의 대표적인 Bake 기법으로는

* **Occlusion Bake**
* Light Bake
* NavMesh Bake

가 있다. (자세한 것은 클릭)

## Batching이 도대체 뭐길래?

> Batching : 여러 개의 Draw Call을 효율적으로 묶어 CPU가 GPU에 보내는 렌더링 명령 수를 줄이는 최적화 기법이다.

조건 : 오브젝트들이 **같은 Material**, **같은 Shader**를 사용

Unity 의 대표적인 Batching 기법으로는

* Static Batching
* Dynamic Batching
* GPU instancing

등이 있다. 

추가적으로) - SRP Batcher는 Draw Call을 줄이는 기술이 아니라, Material 상태 변경 비용을 줄이는 CPU 최적화 기술이다.

![D937A94B-8F66-42E1-9791-F7C5596BD4AA_4_5005_c](/assets/images/2026-07-04-2-Many-Draw-Calls/D937A94B-8F66-42E1-9791-F7C5596BD4AA_4_5005_c.jpeg)

사회초년생이 된 dazzang2의 미래 상상도입니다. 
저 진짜 취업하고싶어요!
