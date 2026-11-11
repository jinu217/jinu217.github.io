---
title: "컴공과 키우기"
type: project
layout: case-study
lang: ko
slug: computer-science-growth
permalink: /projects/computer-science-growth/
date: 2025-11-15
year: 2025
period: "2025.08–2025.11"
image: "/images/projects/computer-science-growth.png"
thumbnail: "/images/projects/computer-science-growth.png"
cover: "/images/projects/computer-science-growth.png"
cover_alt: "보스의 부채꼴 탄막을 보여주는 게임 화면"
thumbnail_alt: "컴공과 키우기 프로젝트 화면"
label: "직접 구현"
role: "7인 팀 · PM / 프로그래머"
technologies: [Unity, C#, ScriptableObject]
code: "https://github.com/jinu217/MiniGame_2025_2/tree/dev"
demo: ""
excerpt: "PM 겸 개발자로 보스 전투와 팀 작업을 연결하고, Android 빌드로 학교 축제에서 시연했습니다."
resume_line: "Unity·C# / 보스 전투·PM·통합, Android APK 학교 축제 시연"
---

## 프로젝트와 역할

교내 게임 개발 동아리의 7인 팀(기획 1명, 개발 4명, 디자인 2명)에서 PM·프로그래머를 맡았습니다. 기능 분담과 통합, 보스 공통 구조와 스테이지별 발사 패턴(Stage 2~5 보스)을 구현했습니다. 게임을 Android APK로 빌드해 학교 축제 방문객을 대상으로 시연했습니다.

저장소 커밋 149개 중 59개가 제 커밋으로 팀에서 가장 많습니다. 공식 기간이 끝난 뒤에도 2026년 2월까지 기획 담당의 플레이 피드백을 받아 보스 체력과 탄 피해, 스테이지 타이머 등을 고쳤습니다.

## 공통 실행과 페이즈 데이터

`BossBase`에서 체력, 발사 주기, 탄환 생성을 처리하고 스테이지별 클래스가 패턴을 구현하게 했습니다. 페이즈 시작 시간과 탄속·탄 수 등의 값은 `ScriptableObject`에 두고, `BossManager`가 경과 시간에 맞춰 페이즈를 적용합니다.

[보스 구조 코드 보기](https://github.com/jinu217/MiniGame_2025_2/blob/c27a1250ea92c0ba11b0a28b70a47c4098bfa146/Assets/Scripts/Boss/BossBase.cs#L59)

## 부채꼴 발사 방향 계산

탄이 2개 이상이면 전체 각도를 `탄 수 - 1`로 나누어 간격을 구합니다. 가운데를 기준으로 시작 각도를 잡고, 각 탄의 회전을 플레이어 방향의 기준 회전에 더해 발사합니다. 탄이 한 개일 때는 나눗셈을 하지 않도록 별도 처리했습니다.

[탄막 패턴 코드 보기](https://github.com/jinu217/MiniGame_2025_2/blob/c27a1250ea92c0ba11b0a28b70a47c4098bfa146/Assets/Scripts/Boss/Boss_Stage2.cs#L41)

관련 설명은 [상세 포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 29쪽과 부록 33쪽에 있습니다.
