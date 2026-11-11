---
title: "Indie Go"
type: project
layout: case-study
lang: ko
slug: indie-go
permalink: /projects/indie-go/
date: 2026-04-01
year: 2026
period: "2026.04–진행 중"
image: "/images/projects/indie-go.png"
thumbnail: "/images/projects/indie-go.png"
cover: "/images/projects/indie-go.png"
cover_alt: "로컬 참가와 턴 UI를 보여주는 게임 화면"
thumbnail_alt: "Indie Go 프로젝트 화면"
label: "직접 구현"
role: "8인 팀 · PM / 프로그래머"
technologies: [Unity, C#, UI, Input]
code: "https://github.com/jinu217/HK-INDIE-GO"
demo: ""
excerpt: "윷놀이 게임의 PM 겸 프로그래머로 공통 구조와 UI 전반, 윷 던지기를 구현하고 팀 작업을 통합하고 있습니다."
resume_line: "Unity·C# / 공통 구조·UI 전반·윷 던지기·설정, PM으로 기능 분담과 통합"
---

## 프로젝트와 역할

온라인과 로컬 플레이를 모두 지원하는 윷놀이 게임입니다. 8인 팀(기획 2명, 개발 4명, 디자인 2명)에서 PM 겸 프로그래머를 맡아 지금도 개발하고 있습니다. 초기 프로젝트 구조와 공통 정의, 시작·로비·캐릭터 선택·인게임·종료 화면의 UI, 윷 던지기, 오디오·그래픽·접근성 설정을 구현했습니다.

스크립트 약 1만 4,600줄 중 약 6,500줄(약 44%)을 작성했고, 커밋은 74개로 팀에서 가장 많습니다(2026-11 기준).

## 서로 기다리지 않고 동시에 개발하는 구조

개발자 4명이 동시에 작업하면 서로의 완료를 기다리거나 수정 범위가 겹칠 수 있었습니다. PM으로서 작업량을 똑같이 나누기보다 기다리는 상황을 줄이는 데 중점을 뒀습니다.

- 개발 초기에 공통 영역을 나누고 보드·규칙·플레이어·턴·윷 결과·시작 설정을 공통 정의 6개로 만들었습니다. [커밋 보기](https://github.com/jinu217/HK-INDIE-GO/commit/8ed3af3)
- 기능 간 선후 관계를 먼저 정리해 각자 독립적으로 구현하고, develop 기준 기능 브랜치와 PR로 합쳤습니다.
- 작업 경계는 문서로 넘겼습니다. 팀전 모드에서는 값이 전달되는 경로와 사용 예시를 적고, 어디부터가 인게임 담당의 범위인지 표시했습니다. [커밋 보기](https://github.com/jinu217/HK-INDIE-GO/commit/c7348ba)

## 결과를 먼저 정하는 윷 던지기

![윷을 던진 장면]({{ '/images/projects/indie-go-yut.jpg' | relative_url }})

던진 결과가 게임 진행을 정하므로 물리 엔진에 맡기지 않았습니다. 결과를 먼저 정한 뒤, 윷이 항상 원판 안에 그 결과대로 착지하도록 궤적을 계산합니다.

겹쳐 떨어지는 윷은 서로 파고들거나 판을 뚫지 않도록 접촉 조건을 모두 만족하는 가장 낮은 받침 자세를 찾습니다. 판 관통, 원판 밖 이탈, 윷끼리의 겹침을 시드 100개로 검사하는 검증 스크립트도 만들었습니다.

[착지 계산·검증 커밋](https://github.com/jinu217/HK-INDIE-GO/commit/fbc303a)

## 입력과 화면, 설정

![설정 화면 일부]({{ '/images/projects/indie-go-settings.jpg' | relative_url }})

키보드·게임패드 참가를 플레이어 슬롯 단위로 관리하고, 슬롯마다 커서와 선택 완료 여부를 둡니다. 선택 결과는 캐릭터 ID와 데이터로 다음 화면에 전달합니다.

[캐릭터 선택 코드 보기](https://github.com/jinu217/HK-INDIE-GO/blob/e3a8a29c43fb40c2e26f28d65adb32cd851e0859/unity/INDIE-GO/Assets/Scripts/UI/CharacterScene/CharacterSelectController.cs#L308)

턴 시작과 단계 변경 이벤트를 `OnEnable`에서 구독하고 `OnDisable`에서 해제해, 꺼진 UI가 이벤트를 받지 않게 했습니다. 연출 속도(1배·1.5배)와 UI 글자 크기(3단계)를 고르는 설정도 넣었고, 말 이동과 윷 던지기 연출이 이 속도를 따릅니다.

[턴 UI 코드 보기](https://github.com/jinu217/HK-INDIE-GO/blob/e3a8a29c43fb40c2e26f28d65adb32cd851e0859/unity/INDIE-GO/Assets/Scripts/UI/InGameUIManager.cs#L53)

자세한 내용은 [포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 18–23쪽, 오디오 채널 규칙은 35쪽에 정리했습니다.
