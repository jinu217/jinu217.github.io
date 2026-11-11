---
title: "MapleLikeClient"
type: project
layout: case-study
lang: ko
slug: maplelikeclient
permalink: /projects/maplelikeclient/
date: 2026-08-01
year: 2026
period: "2026.07–2026.08"
image: "/images/projects/maplelikeclient.png"
thumbnail: "/images/projects/maplelikeclient.png"
cover: "/images/projects/maplelikeclient.png"
cover_alt: "발판과 플레이어 이동을 보여주는 게임 화면"
thumbnail_alt: "MapleLikeClient 프로젝트 화면"
label: "직접 구현"
role: "개인 프로젝트"
technologies: [C++, SFML, JSON]
code: "https://github.com/jinu217/MapleLikeClient"
demo: ""
excerpt: "C++·SFML로 2D 액션의 이동·충돌·전투·카메라·레벨 로딩을 직접 구성했습니다."
resume_line: "C++·SFML / 이동·충돌·입력 보정·전투·카메라·JSON 레벨 로딩"
---

## 프로젝트 개요

C++와 SFML로 만든 2D 액션 개인 프로젝트입니다. `Game`이 입력·업데이트·렌더링을 조율하고, `World`가 환경 객체와 적을 소유하며, `Player`가 이동·충돌·전투를 처리하도록 구성했습니다.

## 단방향 발판의 착지 조건

첫 버전은 모든 발판을 막힌 지형으로 처리해, 얇은 발판 아래에서 점프하면 머리가 부딪히고 옆에서는 벽처럼 막혔습니다. 발판을 Solid와 OneWay로 나누고 단방향 발판의 착지 조건을 따로 만들었습니다. ([첫 버전](https://github.com/jinu217/MapleLikeClient/commit/bdebe40) → [수정](https://github.com/jinu217/MapleLikeClient/commit/8d23f2d))

현재 프레임의 겹침만 보면 발판 아래에서 올라오는 경우와 위에서 내려오는 경우를 구분하기 어렵습니다. 이전 프레임의 발 하단 위치와 수직 속도를 함께 확인해 위에서 접근한 하강 상태일 때 착지시켰습니다. 아래로 내려가기 입력을 받으면 짧은 타이머 동안 착지를 건너뜁니다.

[충돌 판정 코드 보기](https://github.com/jinu217/MapleLikeClient/blob/8d23f2d7833fab796f05cebd5a2d8ca4b8c8f66d/MapleLikeClient/Player.cpp#L477)

## 점프 입력 버퍼와 코요테 타임

착지 직전에 누른 점프를 잠시 보관하고, 발판에서 막 떨어진 뒤에도 짧은 시간 점프를 허용합니다. 점프가 실행되면 두 타이머와 공중 점프 사용 횟수를 함께 갱신합니다. 등반에 진입할 때는 접지·타이머·점프 횟수를 정리해 상태가 섞이지 않게 했습니다.

[입력 처리 코드 보기](https://github.com/jinu217/MapleLikeClient/blob/8d23f2d7833fab796f05cebd5a2d8ca4b8c8f66d/MapleLikeClient/Player.cpp#L290)

## 레벨 데이터와 객체 소유

`LevelLoader`가 JSON을 읽고 좌표·크기·발판 종류를 검증해 `LevelData`를 만듭니다. `World`는 검증된 데이터를 받아 발판과 적을 생성합니다. 환경 객체는 `vector`로 소유하고, 필요한 조회 범위는 `span<const Platform>`으로 전달해 복사 없이 읽게 했습니다.

[레벨 검증 코드 보기](https://github.com/jinu217/MapleLikeClient/blob/8d23f2d7833fab796f05cebd5a2d8ca4b8c8f66d/MapleLikeClient/LevelLoader.cpp#L14) · [World 구조 보기](https://github.com/jinu217/MapleLikeClient/blob/8d23f2d7833fab796f05cebd5a2d8ca4b8c8f66d/MapleLikeClient/World.cpp#L9)

공격 ID를 이용한 연속 피격 구분, 카메라 추적과 화면 비율 처리도 [전체 포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 24–27쪽과 부록 32쪽에 담았습니다.
