---
title: "Indie Go"
type: project
layout: case-study
lang: ko
slug: indie-go
permalink: /projects/indie-go/
date: 2026-04-01
year: 2026
period: "2026.04 시작"
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
excerpt: "로컬 참가 입력, 캐릭터 선택, 턴 이벤트 UI와 오디오 설정을 연결했습니다."
resume_line: "Unity·C# / 로컬 입력·캐릭터 선택·턴 UI·오디오, 기능 분담과 통합"
---

## 프로젝트와 역할

8인 팀의 PM·프로그래머로 참여했습니다. 키보드·게임패드의 참가 입력, 캐릭터 선택, 공통 UI와 오디오 설정을 구현하고 기능 분담과 통합 과정을 맡았습니다.

## 플레이어별 입력과 선택 상태

참가 상태를 플레이어 슬롯별로 관리하고, 각자의 커서 위치와 선택 완료 여부를 보관했습니다. 선택 전에는 이동·확정 입력을, 확정 후에는 취소 입력을 처리합니다. 선택 결과는 캐릭터 ID와 데이터로 다음 화면에 전달합니다.

[캐릭터 선택 코드 보기](https://github.com/jinu217/HK-INDIE-GO/blob/e3a8a29c43fb40c2e26f28d65adb32cd851e0859/unity/INDIE-GO/Assets/Scripts/UI/CharacterScene/CharacterSelectController.cs#L308)

## 턴 이벤트와 UI

턴 시작과 단계 변경 이벤트를 구독해 플레이어 패널, 현재 턴, 스킬 화면을 갱신합니다. `OnEnable`에서 구독하고 `OnDisable`에서 해제해 UI의 활성화 상태에 맞춰 연결을 관리했습니다.

[턴 UI 코드 보기](https://github.com/jinu217/HK-INDIE-GO/blob/e3a8a29c43fb40c2e26f28d65adb32cd851e0859/unity/INDIE-GO/Assets/Scripts/UI/InGameUIManager.cs#L53)

음량과 음소거 상태의 채널별 적용은 [상세 포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 27–30쪽에 정리했습니다.
