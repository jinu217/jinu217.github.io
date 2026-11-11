---
title: "전기톱 키우기"
type: project
layout: case-study
lang: ko
slug: chainsaw-growth
permalink: /projects/chainsaw-growth/
date: 2025-11-01
year: 2025
period: "2025.10–2025.11"
image: "/images/projects/chainsaw-growth.png"
thumbnail: "/images/projects/chainsaw-growth.png"
cover: "/images/projects/chainsaw-growth.png"
cover_alt: "벌목과 성장 흐름을 보여주는 게임 화면"
thumbnail_alt: "전기톱 키우기 프로젝트 화면"
label: "직접 구현"
role: "7인 팀 · 프로그래머"
technologies: [Unity, C#, WebGL]
code: "https://github.com/jinu217/app-in-toss/tree/game"
demo: ""
excerpt: "전기톱 공격·과열과 성장 흐름을 구현하고, 토스 앱 미니게임으로 출시한 뒤 업데이트까지 맡았습니다."
resume_line: "Unity·C#·WebGL / 전기톱·과열·성장 구현, 앱인토스 진동 연동, 출시·운영"
---

## 프로젝트와 담당 범위

7인 팀(기획 1명, 프로그래머 4명, 디자이너 2명)에서 전기톱의 이동·공격·과열·반동과 성장 수치, 나무·바위·몬스터, 보스 구간, 앱인토스 진동 연동을 맡았습니다. WebGL 빌드와 앱인토스 적용에도 일부 참여했습니다.

앱인토스 게임 공모전에 출품해 토스 앱 미니게임으로 출시했고 지금도 서비스 중입니다. 광고 수익이 작게 발생했습니다. 출시 뒤에도 보스 추가와 수치 수정 같은 업데이트를 이어 갔습니다.

## 연타로 과열을 피하던 허점

과열 수치는 기획에서 받은 값 그대로 구현했습니다. 그런데 아주 짧게 눌렀다 떼기를 반복하면 열은 거의 쌓이지 않고 피해는 계속 들어갔습니다. 직접 테스트하다 발견했고, 누르는 시간에 따라 오르는 열과 뗐을 때 식는 열을 비교해 연타가 이득이 되는 구간을 확인했습니다.

기획자와 협의해 0.5초 안에 뗀 짧은 입력은 열 누적을 2배로 하고 최소치를 더했습니다. 뗀 뒤 0.2초는 식지 않게 하고, 누른 길이에 따라 냉각 속도를 나눴습니다. 출시 뒤에는 과열 강화 보너스를 고정값에서 기본 한계의 비율로 바꿨습니다.

[짧은 입력 보정 커밋](https://github.com/jinu217/app-in-toss/commit/dd42cf6) · [출시 뒤 조정 커밋](https://github.com/jinu217/app-in-toss/commit/d4a2bfa)

## Unity와 토스 앱을 잇는 진동

Unity WebGL 코드는 앱인토스 진동 기능을 바로 부를 수 없어서, C# 코드가 WebGL 템플릿의 JavaScript 함수를 부르고 그 함수가 진동 API를 호출하게 연결했습니다.

처음에는 300ms 안에 들어온 요청을 버렸는데, 실제 휴대폰에서 연달아 나무를 쓰러뜨리면 진동이 빠졌습니다. 요청을 큐에 쌓아 120ms 간격으로 차례로 재생하고, 앱이 가려지면 재생을 멈추도록 바꿨습니다.

[진동 연결 커밋](https://github.com/jinu217/app-in-toss/commit/97661ff) · [큐 처리 커밋](https://github.com/jinu217/app-in-toss/commit/f2ea160)

## 1차 빌드 직후 고친 문제

- 게임오버 화면이 뜰 때 일시정지 패널이 겹쳐 보여, 게임오버 시 일시정지 패널을 숨기고 버튼을 비활성화했습니다. [커밋 보기](https://github.com/jinu217/app-in-toss/commit/a3d87c2)
- 쓰러진 나무를 치우는 처리가 게임 시간에 묶여 있어 게임이 멈추면 사라지지 않을 수 있었습니다. 실제 시간 기준으로 비활성화해 풀로 돌려보냈습니다. 풀에서 다시 꺼낼 때의 초기화(체력·크기·생존 상태)는 팀원과 함께 설계했습니다. [커밋 보기](https://github.com/jinu217/app-in-toss/commit/67624fc)

## 전기톱 상태와 보스 구간

누르는 시간만큼 열을 쌓고 한계에 닿으면 과열로 바꿉니다. 가까운 나무가 바뀌면 대상과 첫 타격을 갱신하고, 손을 떼면 공격 타이머를 초기화합니다. 강화 결과는 공격력·공격 간격·과열 한계·반동에 반영합니다.

보스 전용 구간에는 일반 나무와 바위를 만들지 않도록 생성기에 보스 구간을 따로 두고, 보스를 앞뒤 나무 사이에 배치했습니다. 기존 나무의 이동·재활용 규칙은 그대로 유지했습니다.

[전기톱 상태 코드 보기](https://github.com/jinu217/app-in-toss/blob/938e170a5296c053d6f15476376a2c78a83efd0d/private/unity-project/Assets/Scripts/ChainSaw_Move.cs#L266) · [보스 구간 커밋](https://github.com/jinu217/app-in-toss/commit/4431974)

자세한 과정과 코드는 [포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 13–17쪽에서 볼 수 있습니다.
