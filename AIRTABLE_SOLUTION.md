# 🎯 Airtable로 구글 아이디 무료할당량 관리

> **최고의 대안! Glide도 Clappia도 필요 없습니다** ✨

---

## 🏆 왜 Airtable인가?

| 항목 | Glide ❌ | Clappia ❌ | **Airtable ✅** |
|------|---------|------------|-----------------|
| **사용 난이도** | 중간 | 어려움 (파일 인식 문제) | **매우 쉬움** |
| **무료 플랜** | 제한적 | 제한적 | **1,200 records** |
| **데이터 입력** | Google Sheets | Excel 업로드 | **Form 자동 생성** |
| **모바일 앱** | 웹 앱 | 웹 앱 | **네이티브 앱** |
| **자동화** | 유료 | 무료 (복잡) | **무료 + 쉬움** |
| **학습 시간** | 1시간 | 2시간 | **10분** |
| **설정 시간** | 30분 | 1시간 | **5분** |

**결론: Airtable이 압도적 1위!** 🥇

---

## ⚡ 5분 빠른 시작

### 1️⃣ Airtable 가입 (1분)

```
1. https://airtable.com 접속
2. "Sign up for free" 클릭
3. Google 계정으로 로그인
```

**무료 플랜 혜택:**
- ✅ 무제한 Bases (프로젝트)
- ✅ 1,200 records per base
- ✅ 5 editors (협업자)
- ✅ 1 GB 첨부파일
- ✅ 모바일 앱
- ✅ Forms
- ✅ 기본 자동화

---

### 2️⃣ Base 생성 (2분)

#### 방법 A: 템플릿 사용 (추천!)

```
1. 대시보드에서 "Start from scratch" 클릭
2. Base 이름: "구글 아이디 관리"
3. 아래 구조대로 테이블 생성
```

#### Base 구조:

**Table 1: 📧 Accounts (구글 아이디)**
```
필드:
- account_id (Single line text)
- email (Email)
- memo (Single line text)
- active (Checkbox)
```

**Table 2: 🌐 Services (사이트)**
```
필드:
- service_id (Single line text)
- site_name (Single line text)
- url (URL)
- daily_limit (Number)
- reset_cycle (Single select: DAILY, WEEKLY, MONTHLY)
```

**Table 3: 📊 Daily Usage (매일 사용량)** ⭐
```
필드:
- date (Date)
- account (Link to Accounts)
- service (Link to Services)
- usage (Number)
- remaining (Formula: {daily_limit} - {usage})
- status (Formula: IF(remaining <= 10, "🔴 위험", IF(remaining <= 30, "🟡 주의", "🟢 안정")))
```

---

### 3️⃣ 데이터 입력 (2분)

#### 샘플 데이터 입력:

**Accounts 테이블:**
```
account_id | email              | memo | active
A01        | user1@gmail.com    | 주력 | ✅
A02        | user2@gmail.com    | 서브 | ✅
```

**Services 테이블:**
```
service_id | site_name | url                    | daily_limit | reset_cycle
S01        | ChatGPT   | chat.openai.com        | 50          | DAILY
S02        | Gemini    | gemini.google.com      | 60          | DAILY
S03        | Claude    | claude.ai              | 45          | DAILY
```

**Daily Usage 테이블:**
```
date       | account | service | usage
2025-01-15 | A01     | S01     | 10
2025-01-15 | A01     | S02     | 20
```

---

## 📱 실전 사용법

### 매일 사용량 입력 (30초!)

#### Form 만들기:

1. **Daily Usage** 테이블 열기
2. 오른쪽 상단 **"Create form"** 클릭
3. Form에 표시할 필드 선택:
   - date (오늘 날짜 기본값 설정)
   - account (드롭다운)
   - service (드롭다운)
   - usage (숫자 입력)
4. **"Share form"** 클릭 → 링크 복사

**Form 사용:**
- 링크를 북마크/홈화면에 추가
- 매일 아침 링크 열기
- 드롭다운 선택 + 사용량 입력
- Submit!

**자동으로:**
- ✅ remaining 계산
- ✅ status 판정 (🔴🟡🟢)
- ✅ 테이블에 기록

---

### View 활용 (강력!)

Airtable의 핵심 기능은 **View**입니다!

#### View 1: 📅 오늘 사용량

```
1. Daily Usage 테이블에서 "Grid view" 옆 "+" 클릭
2. View 이름: "오늘"
3. Filter 추가:
   - date is today
4. Sort 추가:
   - remaining (ascending) → 남은량 적은 것부터
```

#### View 2: 🔴 위험 항목

```
1. View 이름: "위험"
2. Filter:
   - status contains "🔴"
3. Group by: account
```

#### View 3: 📊 아이디별 요약

```
1. View type: Kanban
2. Group by: account
3. Card 표시: service, remaining, status
```

---

## 🔄 자동화 설정

Airtable 무료 플랜: **월 100회 자동화** 가능!

### 자동화 1: 남은량 위험 시 알림

```
1. 오른쪽 상단 "Automations" 클릭
2. "Create automation" 클릭
3. Trigger:
   - "When record matches conditions"
   - Table: Daily Usage
   - Conditions: remaining <= 10
4. Action:
   - "Send email"
   - To: 내 이메일
   - Subject: "⚠️ {account} - {service} 남은량 위험!"
   - Message: "남은량: {remaining}개"
```

### 자동화 2: 매일 아침 요약

```
1. Trigger:
   - "At a scheduled time"
   - Every day at 9:00 AM
2. Action:
   - "Find records"
   - Table: Daily Usage
   - Conditions: date is today AND status contains "🔴"
3. Action:
   - "Send email"
   - Subject: "오늘 위험한 항목 {record count}개"
```

---

## 📱 모바일 앱 사용

### iOS / Android

1. **App Store** 또는 **Google Play**에서 "Airtable" 검색
2. 앱 설치 및 로그인
3. Base 자동 동기화됨!

**모바일에서 할 수 있는 것:**
- ✅ 실시간 데이터 확인
- ✅ Form으로 즉시 입력
- ✅ View 전환
- ✅ 필터링/정렬
- ✅ 알림 받기

**장점:**
- 네이티브 앱이라 빠름
- 오프라인 지원 (나중에 동기화)
- 푸시 알림

---

## 🎨 고급 기능

### 1️⃣ Formula 활용

**남은 비율 계산:**
```
{remaining} / {daily_limit} * 100 & "%"
```

**상태 판정 (고급):**
```
IF(
  {remaining} <= {daily_limit} * 0.2,
  "🔴 위험 (" & {remaining} & "개)",
  IF(
    {remaining} <= {daily_limit} * 0.5,
    "🟡 주의 (" & {remaining} & "개)",
    "🟢 안정 (" & {remaining} & "개)"
  )
)
```

**오늘 안 쓴 아이디 표시:**
```
IF(
  AND({date} = TODAY(), {usage} = 0),
  "❗ 미사용",
  ""
)
```

---

### 2️⃣ Interface Builder (무료!)

**대시보드 만들기:**

1. 상단 "Interfaces" 클릭
2. "Create interface" 선택
3. Layout 선택:
   - Dashboard
   - Timeline
   - Gallery

**구성 요소:**
- 📊 Chart: 아이디별 사용량
- 📋 Record list: 오늘 위험 항목
- 🔢 Number: 전체 남은량 합계
- 🎯 Button: "사용량 입력" Form 바로가기

---

### 3️⃣ Extensions (앱스토어 같은 것)

**추천 Extensions:**

**Chart:**
```
1. Extensions → Add extension
2. "Chart" 선택
3. Table: Daily Usage
4. X-axis: date
5. Y-axis: remaining
6. Group by: account
```

**Calendar:**
```
1. "Calendar" extension
2. Date field: date
3. Title: account + service
4. Color: status
```

---

## 💡 실전 팁

### ✅ DO (권장)

1. **Form을 북마크에 추가**
   - 매일 접근이 쉬워짐

2. **View를 목적별로 만들기**
   - "오늘", "이번 주", "위험", "아이디별" 등

3. **색상 활용**
   - Conditional formatting으로 시각화

4. **모바일 앱 사용**
   - 어디서나 확인/입력 가능

5. **주간 리뷰**
   - 매주 일요일 사용 패턴 분석

### ❌ DON'T (비추천)

1. 직접 테이블 수정 (Form 사용!)
2. Formula 필드 값 수정 (자동 계산됨)
3. Base 여러 개 만들기 (한 Base에서 관리)

---

## 🆚 Glide/Clappia 대비 장점

| 기능 | Glide | Clappia | **Airtable** |
|------|-------|---------|--------------|
| **데이터 입력** | Google Sheets 수동 | Excel 업로드 | **Form 자동** |
| **필터링** | App 설정 필요 | App 설정 필요 | **View로 즉시** |
| **모바일** | PWA (웹앱) | PWA | **네이티브 앱** |
| **자동화** | 유료 플랜 | 복잡함 | **무료 + 직관적** |
| **협업** | 어려움 | 어려움 | **매우 쉬움** |
| **확장성** | 제한적 | 제한적 | **무한** |
| **학습 곡선** | 가파름 | 매우 가파름 | **완만** |

---

## 📊 실제 사용 시나리오

### 매일 아침 (30초)

```
1. 모바일에서 Airtable 앱 열기
2. Form 열기
3. 드롭다운 선택 2번 (아이디, 사이트)
4. 사용량 입력
5. Submit
```

### 주간 리뷰 (5분)

```
1. "이번 주" View 확인
2. 어떤 아이디가 많이 쓰였는지 분석
3. 다음 주 사용 계획 수립
```

### 새 아이디 추가 (1분)

```
1. Accounts 테이블 열기
2. + 클릭
3. 정보 입력
4. 즉시 Form 드롭다운에 반영됨!
```

---

## 🎓 학습 리소스

### 공식 튜토리얼
- [Airtable Basics](https://support.airtable.com/docs/introduction-to-airtable-basics)
- [Formula Field Guide](https://support.airtable.com/docs/formula-field-reference)
- [Automation Guide](https://support.airtable.com/docs/automations-overview)

### 비디오
- [Airtable in 10 minutes](https://www.youtube.com/results?search_query=airtable+tutorial+2025)

### 커뮤니티
- [Airtable Community](https://community.airtable.com/)
- [Airtable Universe](https://airtable.com/universe) - 템플릿 갤러리

---

## 🚀 다음 단계

### 지금 바로:

1. ✅ Airtable 가입
2. ✅ Base 생성 (위 구조대로)
3. ✅ 샘플 데이터 입력
4. ✅ Form 생성
5. ✅ 모바일 앱 설치

### 이번 주:

1. 매일 Form으로 사용량 입력
2. View 만들어보기
3. 자동화 1개 설정

### 다음 주:

1. Interface Builder로 대시보드 만들기
2. Chart Extension 추가
3. 주간 리뷰 루틴 확립

---

## 💬 왜 Airtable이 최고인가?

### 1. **진입 장벽 제로**
- 스프레드시트처럼 보여서 익숙함
- 하지만 데이터베이스의 강력함

### 2. **확장성**
- 처음엔 단순하게 시작
- 나중에 자동화, Interface, Extension 추가
- 프로젝트가 커져도 OK

### 3. **에코시스템**
- Zapier, Make 연동
- API 제공
- 수천 개 템플릿

### 4. **무료로 충분**
- 1,200 records = 매일 3개씩 1년 사용 가능
- 자동화 월 100회 = 하루 3번 자동화
- 개인 사용엔 완벽!

---

## 🎁 보너스 팁

### 템플릿 복사하기

나중에 다른 프로젝트에도 사용:

```
1. Base 우측 상단 "..." 클릭
2. "Duplicate base" 선택
3. 새 프로젝트로 즉시 재사용!
```

### CSV 내보내기

데이터 백업:

```
1. View 열기
2. "..." → "Download CSV"
3. Excel에서도 열림!
```

### API 사용

고급 사용자:

```python
# Python으로 자동 데이터 입력
import requests

url = "https://api.airtable.com/v0/{base_id}/{table_name}"
headers = {"Authorization": "Bearer {api_key}"}
data = {"fields": {"account_id": "A01", "usage": 10}}

requests.post(url, json=data, headers=headers)
```

---

## 🏁 결론

**Airtable = 최고의 선택!**

- ✅ 가장 쉬움 (10분 학습)
- ✅ 가장 강력함 (무한 확장)
- ✅ 가장 예쁨 (UI/UX 최고)
- ✅ 완전 무료 (개인 사용)

**Glide, Clappia 다 필요 없습니다.**

**지금 바로 시작하세요!** 🚀

---

## Sources
- [Airtable Plans Overview](https://support.airtable.com/docs/airtable-plans)
- [How to Use Airtable: Beginner's Guide | SitePoint](https://www.sitepoint.com/how-to-use-airtable-a-beginners-guide/)
- [Airtable 2025 Guide | GAP Consulting](https://www.gapconsulting.io/blog/getting-started-in-airtable-updated-for-2025)
- [What is Airtable? | Retoolers](https://www.retoolers.io/blog-posts/what-is-airtable)
- [Complete Guide to Airtable | Appairium](https://appairium.com/en/blog/how-to-use-airtable)
