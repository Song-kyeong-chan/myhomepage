---
title: "LifeSync AI: AI 기반 24시간 라이프 관리 안드로이드 앱"
date: 2026-06-22
description: "루틴·할 일·감정 일기를 기록하면 AI가 패턴을 분석하고 정해진 시간에 먼저 피드백을 보내 주는 안드로이드 앱과 FastAPI 서버를 혼자 만든 모바일프로그래밍 최종 프로젝트입니다."
toc: true
displayInMenu: false
displayInList: true
resources:
- name: featuredImage
  src: "screen-chat-analysis.jpg"
  params:
    description: "LifeSync AI의 AI 채팅, 분석과 코칭, 데이터 기록 화면"
---

| 항목 | 내용 |
|---|---|
| 기간 | 2026년 6월 (최종 제출 2026년 6월 22일) |
| 상태 | 완료 (모바일프로그래밍 최종 프로젝트 제출) |
| 형태 | 개인 프로젝트 |
| 저장소 | [lifesync-android](https://github.com/Song-kyeong-chan/lifesync-android) · [lifesync-server](https://github.com/Song-kyeong-chan/lifesync-server) |
| 기술 | Kotlin, Jetpack Compose, Room, Retrofit2, Python, FastAPI, Gemini API, AWS EC2·S3 |

## 목적

집에 있을 때 침대에서 유튜브 쇼츠를 몇 시간씩 보고 있는 제 모습을 자주 발견했습니다.
이렇게 무의식적으로 흘려보내는 자투리 시간을 줄이고, 그 시간을 자기계발에 쓰도록 돕는 앱을 만들고 싶었습니다.

단순한 일정 관리에서 그치지 않고, 루틴·할 일·일기·앱 사용 기록을 한곳에 모은 뒤
AI가 패턴을 분석하고 정해진 시간에 스스로 피드백을 보내는 에이전트 구조를 목표로 했습니다.

## 맡은 역할

개인 프로젝트로, 기획부터 배포까지 모든 작업을 직접 했습니다.

- 기획: 문제 정의, MVP 범위 결정, ERD 설계
- 안드로이드 앱: 화면, 로컬 DB, 알림 예약, 서버 통신
- 서버: FastAPI로 AI 채팅·데이터 동기화·사진 업로드 API 구현
- 인프라: AWS EC2 서버 운영, S3 사진 저장소 연결
- 형상 관리: 앱과 서버를 각각 GitHub 저장소로 관리


