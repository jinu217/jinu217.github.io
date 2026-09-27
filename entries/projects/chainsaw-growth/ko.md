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
excerpt: "전기톱 공격·과열과 벌목·성장 흐름을 구현하고 WebGL 게임의 앱인토스 출시에 참여했습니다."
resume_line: "Unity·C#·WebGL / 전기톱·벌목·성장 구현, 앱인토스 출시·운영"
---

## 프로젝트와 담당 범위

7인 팀(기획 1명, 프로그래머 4명, 디자이너 2명)에서 전기톱 동작과 성장 수치 반영, 나무·보스·장애물, 행 진행과 객체 생명주기를 담당했습니다.

앱인토스 게임 공모전에 출품한 뒤 실제 토스 앱의 미니게임으로 출시했습니다. WebGL 빌드와 플랫폼 적용에도 일부 참여했으며, 출시 후 광고를 통한 수익이 발생했습니다.

## 입력과 과열 상태

입력을 유지하는 동안 목표 나무를 향해 공격하고 열을 누적합니다. 한계에 도달하면 과열 상태로 전환하고 입력과 타격 연출을 정리합니다. 목표가 바뀌거나 입력을 놓을 때는 공격 타이머와 위치를 다시 맞춥니다.

[전기톱 상태 코드 보기](https://github.com/jinu217/app-in-toss/blob/938e170a5296c053d6f15476376a2c78a83efd0d/private/unity-project/Assets/Scripts/ChainSaw_Move.cs#L266)

## 행 진행과 객체 재사용

행 이동 중 중복 진행 요청을 막고, 이전 구간을 정리한 뒤 다음 구간을 생성합니다. 풀에서 나무를 다시 가져올 때 체력·생존·크기를 복구하고, 비활성화할 때 코루틴과 연출을 정리했습니다.

[나무 재사용 코드 보기](https://github.com/jinu217/app-in-toss/blob/938e170a5296c053d6f15476376a2c78a83efd0d/private/unity-project/Assets/Scripts/In-game/Tree.cs#L45)

성장 수치와 보스를 공통 표시 흐름에 연결한 내용은 [상세 포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 14–17쪽에서 볼 수 있습니다.
