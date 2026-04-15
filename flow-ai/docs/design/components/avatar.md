---
작성자: agent-designer
작성일: 2026-04-15
버전: 1.1.0
상태: draft
feature: DS-AVATAR
---

# Avatar 컴포넌트 스펙

## 개요

사용자 및 AI 프로필 이미지 표현 컴포넌트 스펙입니다.
관련 파일:
- [AvatarProfile.tsx](../../../design-system/common/common/AvatarProfile.tsx)
- [UserAvatar.tsx](../../../design-system/common/common/UserAvatar.tsx)
- [flowai-avatar.tsx](../../../design-system/common/common/flowai-avatar.tsx)
- [UserProfile.tsx](../../../design-system/common/common/ui/UserProfile.tsx)

---

## Sizes

| Size  | 지름   | font-size (이니셜) |
|-------|--------|-------------------|
| `xs`  | 20px   | 10px              |
| `sm`  | 24px   | 12px              |
| `md`  | 32px   | 14px              |
| `lg`  | 40px   | 16px              |
| `xl`  | 48px   | 18px              |
| `2xl` | 64px   | 24px              |

---

## 공통 스펙

| 속성           | 값                            |
|---------------|-------------------------------|
| border-radius  | `full` (원형)                 |
| border         | 없음 (기본)                   |
| overflow       | hidden                        |
| fallback 배경  | `brand.100` (#E9E5FF)        |
| fallback 텍스트| `brand.600` (#4C34D1), 이니셜 |

---

## Variants

### UserAvatar
- 사용자 프로필 이미지 표시
- 이미지 없을 때: 이름 이니셜 (최대 2글자) 표시
- 온라인 상태 표시: 우측 하단 dot (`w-2.5 h-2.5`, `bg-semantic-success-bg-emphasis`, ring 흰색)

### FlowAI Avatar (AI 아바타)

통일 AI 아바타 1종. 캐릭터 선택 없이 고정 디자인을 사용합니다.

**형태 및 구조**

| 속성 | 값 |
|------|----|
| 형태 | 원형 구체 (border-radius: 50%) |
| 배경 | radial-gradient (brand-400 → brand-500 → brand-700) |
| ::before (하이라이트) | radial-gradient, 좌상단 반사광 (흰색 20% → transparent) |

**바이저 (중앙 다크 영역)**

| 속성 | 값 |
|------|----|
| 위치 | 중앙 배치 |
| 너비 | 아바타 너비의 68% |
| 높이 | 아바타 높이의 38% |
| border-radius | 999px (캡슐형) |
| 배경 | linear-gradient (#1a1040 → #2a1860) |

**눈 (흰색 세로 타원 2개)**

| 사이즈 | 눈 크기 | 간격 |
|--------|---------|------|
| md (32px) | 4×6px | 6px |
| lg (56px) | 7×10px | 10px |

- 색상: `#FFFFFF`
- 애니메이션: glow 3초 ease-in-out infinite (opacity 0.7 ↔ 1.0, box-shadow 변화)

**사이즈 정의**

| Size | 지름 | 용도 |
|------|------|------|
| `md` | 32px | 채팅 헤더, AI 응답 버블, 홈 프로필 카드 |
| `lg` | 56px | 온보딩 Step 1 상단 |

### UserProfile (이름 + 아바타)
```
[Avatar]  이름 (sm-medium)
          이메일 또는 역할 (xs-regular, muted)
```

---

## Avatar Group (겹치기)
- 겹침 offset: `-8px` (음수 margin-left)
- 테두리: `2px solid white` (배경과 구분)
- 최대 표시: 3개 + `+N` 텍스트
