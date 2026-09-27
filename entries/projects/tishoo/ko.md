---
title: "Tishoo"
type: project
layout: case-study
lang: ko
slug: tishoo
permalink: /projects/tishoo/
date: 2025-11-30
year: 2025
period: "2025.08–2025.11"
image: "/images/projects/tishoo.png"
thumbnail: "/images/projects/tishoo.png"
cover: "/images/projects/tishoo.png"
cover_alt: "후기 입력과 데이터베이스 연결을 보여주는 게임 화면"
thumbnail_alt: "Tishoo 프로젝트 화면"
label: "직접 구현"
role: "7인 팀 · 프로그래머"
technologies: [PHP, JavaScript, MariaDB]
code: "https://github.com/jinu217/sideproject"
demo: ""
excerpt: "팀 웹 서비스에서 프로필 수정과 동료 후기의 입력·저장·조회 흐름을 구현했습니다."
resume_line: "PHP·JavaScript·MariaDB / 프로필·후기·DB 연동과 공통 화면"
---

## 프로젝트와 담당 범위

7인 팀(기획 2명, 프로그래머 1명, 디자이너 4명)의 웹 서비스 프로젝트입니다. 프런트엔드, 백엔드와 데이터베이스 연동을 담당했습니다.

## 후기 데이터 흐름

사용자·프로젝트·작성자의 관계를 데이터로 표현하고 후기 입력, 저장, 조회 화면을 연결했습니다. 입력을 검사한 뒤 데이터베이스에 기록하고, 조회 화면에서 후기와 집계 정보를 표시합니다.

[후기 입력 코드 보기](https://github.com/jinu217/sideproject/blob/1f6d4e2a5830e17113519ef9419b671a61682c67/page/view/07_03_view.php#L85)

## 프로필과 공통 화면

프로필 수정 시 기존 데이터 유무에 따라 갱신 또는 추가하고, 조회 화면에서는 관련 데이터가 없어도 기본 이미지를 표시하도록 했습니다. 공통 레이아웃에서 메뉴와 화면 구조를 관리했습니다.

[공통 레이아웃 코드 보기](https://github.com/jinu217/sideproject/blob/1f6d4e2a5830e17113519ef9419b671a61682c67/common/layout.php#L1)

이 경험은 게임 외 서비스 개발 사례로 분리했습니다. 자세한 흐름은 [상세 포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 38–40쪽에 있습니다.
