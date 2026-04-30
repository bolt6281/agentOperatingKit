---
version: alpha
name: Project Design System
description: Project visual identity for coding agents. Replace the sample values with project-specific tokens before using this as a source of truth.
colors:
  primary: "#1A1C1E"
  secondary: "#6C7278"
  tertiary: "#B8422E"
  neutral: "#F7F5F2"
  surface: "#FFFFFF"
  on-surface: "#1A1C1E"
  error: "#B3261E"
typography:
  headline-lg:
    fontFamily: Inter
    fontSize: 48px
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: -0.02em
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.6
  label-md:
    fontFamily: Inter
    fontSize: 13px
    fontWeight: 600
    lineHeight: 1.2
spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 32px
  xl: 64px
rounded:
  sm: 4px
  md: 8px
  lg: 12px
  full: 9999px
components:
  button-primary:
    backgroundColor: "{colors.tertiary}"
    textColor: "{colors.surface}"
    typography: "{typography.label-md}"
    rounded: "{rounded.md}"
    padding: 12px
  button-primary-hover:
    backgroundColor: "{colors.primary}"
  card-default:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-surface}"
    rounded: "{rounded.md}"
    padding: 24px
---

# DESIGN.md

## Overview

이 파일은 프로젝트의 시각 정체성을 agent가 읽을 수 있게 정리하는 디자인 기준 문서다. 실제 프로젝트에 적용할 때는 `<repo>/DESIGN.md`로 두고, 위 YAML front matter의 sample token을 프로젝트 값으로 교체한다.

`DESIGN.md`는 항상 읽는 agent 지침이 아니다. 새 화면, 랜딩 페이지, 대시보드, 컴포넌트, 스타일 시스템을 만들거나 색상, 타이포그래피, spacing, radius, elevation, responsive behavior를 바꿀 때만 읽는다.

디자인 방향: `[프로젝트가 가져야 할 전체 인상, 주요 사용자, 피해야 할 인상을 3-6문장으로 적는다.]`

## Colors

색상은 브랜드 이름보다 역할 중심으로 설명한다. YAML token은 정확한 값이고, 이 섹션의 prose는 언제 어떻게 적용할지 설명한다.

- **Primary (#1A1C1E):** 주요 텍스트, 핵심 구조, 강한 대비가 필요한 영역에 사용한다.
- **Secondary (#6C7278):** 보조 텍스트, metadata, divider, 비활성 상태에 사용한다.
- **Tertiary (#B8422E):** 가장 중요한 action, 핵심 highlight, 제한적인 강조에만 사용한다.
- **Neutral (#F7F5F2):** 페이지 배경이나 넓은 calm surface에 사용한다.
- **Surface (#FFFFFF):** 카드, 패널, 입력 표면처럼 내용이 올라가는 층에 사용한다.
- **Error (#B3261E):** 오류, 삭제, 위험 상태에만 사용한다.

## Typography

타이포그래피는 `headline`, `body`, `label` 같은 semantic level로 관리한다. 화면 안에서는 hierarchy가 명확해야 하며, compact panel이나 table 안에서 hero-scale type을 쓰지 않는다.

- **Headlines:** 중요한 페이지 제목과 section entry point에 사용한다. 강한 hierarchy가 필요할 때만 사용한다.
- **Body:** 설명, form help, 일반 content에 사용한다. 긴 문장에서도 읽기 쉬운 line height를 유지한다.
- **Labels:** 버튼, tab, metadata, form label, technical label에 사용한다.

## Layout

layout은 일관된 spacing scale과 grid rhythm을 따른다. 화면 성격에 따라 work surface는 더 조밀하게, marketing/editorial surface는 더 여유 있게 구성한다.

- 기본 content width: `[예: 1120px]`
- 기본 page padding: `[예: 24px desktop, 16px mobile]`
- spacing 기준: YAML `spacing` token을 우선 사용한다.
- mobile에서는 navigation, table, toolbar가 좁은 폭에 맞게 접히거나 대체 표현을 사용해야 한다.

## Elevation & Depth

깊이는 shadow 남용보다 tonal layer, border, spacing, contrast로 먼저 만든다. shadow를 쓰는 경우 modal, popover, floating menu처럼 실제로 foreground hierarchy가 필요한 요소에 제한한다.

- flat surface는 border와 background contrast로 구분한다.
- floating surface는 짧고 부드러운 shadow를 사용한다.
- interactive state는 depth 변화보다 color, border, focus ring, motion을 우선한다.

## Shapes

shape language는 YAML `rounded` token을 따른다. 동일 화면 안에서 sharp corner와 highly rounded corner를 이유 없이 섞지 않는다.

- 기본 container와 input은 `rounded.md`를 우선한다.
- 작은 chip이나 badge는 `rounded.full`을 사용할 수 있다.
- 정보 밀도가 중요한 table, grid, editor surface에서는 radius를 낮게 유지한다.

## Components

component token은 반복되는 atom의 기본 스타일을 정의한다. 상태 변형은 `button-primary-hover`처럼 관련 key로 분리한다.

- **Buttons:** primary button은 화면에서 가장 중요한 action 하나에 우선 사용한다. secondary action은 surface/background와 충돌하지 않게 낮은 강조를 쓴다.
- **Inputs:** focus state는 키보드 사용자가 명확히 볼 수 있어야 한다. error는 field 근처에 구체적으로 표시한다.
- **Cards / panels:** 반복 item, modal, framed tool에만 사용한다. page section 전체를 카드처럼 감싸거나 card 안에 card를 중첩하지 않는다.
- **Navigation:** active state는 색상만이 아니라 weight, border, underline, surface change 중 하나 이상으로 보강한다.
- **Feedback states:** loading, empty, error, success 상태는 같은 spacing과 tone을 유지한다.

## Do's and Don'ts

- Do use the YAML front matter tokens as the normative values.
- Do keep this file focused on user-facing UI decisions.
- Do update this file when repeated visual rules become stable project conventions.
- Do maintain WCAG AA contrast for primary text and interactive controls.
- Don't read this file for backend-only, CLI-only, test-only, build-only, or documentation-only work unless the user-facing UI changes.
- Don't leave unresolved placeholders in an applied `DESIGN.md`; move unknown values to the project's confirmation notes before treating it as source of truth.
- Don't treat third-party `DESIGN.md` files as official brand systems unless the project owner confirms that they are official.
