# 🚀 Google AppSheet로 앱 만들기

> **Google의 공식 노코드 앱 빌더**

---

## 🏆 왜 AppSheet인가?

| 장점 | 설명 |
|------|------|
| **🆓 완전 무료** | 개발 & 테스트 영구 무료 |
| **⚡ 초간단** | Google Sheets → 앱 자동 생성 |
| **📱 네이티브 앱** | iOS/Android 앱 자동 생성 |
| **🔄 실시간 동기화** | Sheets 수정 = 앱 즉시 반영 |
| **🎨 커스터마이징** | 드래그앤드롭으로 UI 수정 |
| **🔒 Google 통합** | Gmail, Drive 완벽 연동 |

---

## ⚡ 3분 빠른 시작

### 1️⃣ Google Sheets 준비 (1분)

이미 만들었다면 스킵!

**아직 안 만들었다면:**
- `GOOGLE_SHEETS_SETUP.md` 참고
- 또는 CSV 파일 가져오기

---

### 2️⃣ AppSheet 접속 (30초)

```
https://www.appsheet.com
→ "Get started" 클릭
→ Google 계정으로 로그인
```

**무료 플랜 선택!**

---

### 3️⃣ 앱 생성 (1분 30초)

#### Step 1: 앱 만들기 시작

```
1. 대시보드에서 "Create" → "App" 클릭
2. "Start with existing data" 선택
3. App name: "구글아이디관리"
4. Category: "Other"
5. "Choose your data" 클릭
```

#### Step 2: Google Sheets 연결

```
1. Data source: "Google Sheets" 선택
2. Google Drive에서 파일 선택:
   "구글아이디_무료할당량_관리"
3. 3개 시트 모두 선택:
   ✅ Accounts
   ✅ Services
   ✅ Daily_Usage
4. "Create app" 클릭
```

#### Step 3: 자동 생성 완료!

```
✅ 앱이 자동으로 생성됨!
✅ 3개 테이블 인식됨
✅ 기본 UI 자동 구성됨
```

**바로 사용 가능합니다!** 🎉

---

## 📱 앱 사용하기

### 즉시 테스트

**웹 미리보기:**
```
오른쪽 화면에 앱 미리보기가 보임
→ 클릭해서 테스트 가능
→ 데이터 입력해보기
→ 즉시 Google Sheets에 반영됨!
```

---

### 모바일 앱 설치

#### iOS / Android

**방법 1: AppSheet 앱 사용 (추천!)**
```
1. App Store / Google Play
2. "AppSheet" 검색 및 설치
3. Google 계정 로그인
4. 내 앱 목록에 자동으로 표시됨!
```

**방법 2: 웹링크로 접근**
```
1. AppSheet 에디터 상단 "Share" 클릭
2. "Browser link" 복사
3. 모바일 브라우저에서 열기
4. "홈 화면에 추가" 선택
```

---

## 🎨 앱 커스터마이징

### 기본 UI는 이미 완성!

AppSheet가 자동으로 만들어준 것:
- ✅ 각 시트별 화면
- ✅ 입력 폼
- ✅ 데이터 목록
- ✅ 검색 기능
- ✅ 필터

**추가 설정 없이 바로 사용 가능!**

---

### 간단한 개선 (선택)

#### 1. Daily_Usage를 메인 화면으로

```
1. 왼쪽 "UX" 탭 클릭
2. "Primary Views" 설정
3. Daily_Usage를 최상단으로 드래그
```

#### 2. 드롭다운 설정

**account_id 필드:**
```
1. 왼쪽 "Data" 탭 → Daily_Usage 테이블
2. account_id 컬럼 클릭
3. Type: "Ref" 선택
4. Source table: "Accounts" 선택
→ 자동으로 드롭다운 생성됨!
```

**service_id 필드:**
```
1. service_id 컬럼 클릭
2. Type: "Ref" 선택
3. Source table: "Services"
→ 드롭다운 완성!
```

#### 3. 남은량 자동 계산 (고급)

**Google Sheets에서 수식 추가:**

Daily_Usage 시트에 컬럼 추가:

**E열 (total_quota):**
```
=VLOOKUP(C2, Services!A:D, 4, FALSE)
```

**F열 (remaining):**
```
=E2-D2
```

**G열 (status):**
```
=IF(F2<=10, "🔴 위험", IF(F2<=30, "🟡 주의", "🟢 안정"))
```

**AppSheet 새로고침:**
```
에디터 상단 "Regenerate structure" 클릭
→ 새 컬럼 자동 인식!
```

---

## 💡 실전 사용법

### 매일 사용량 입력 (30초!)

#### 모바일에서:

```
1. AppSheet 앱 열기
2. "Daily_Usage" 탭
3. "+" 버튼 클릭
4. 입력:
   - date: 오늘 (자동)
   - account_id: 드롭다운 선택
   - service_id: 드롭다운 선택
   - usage: 숫자 입력
5. 저장
```

**자동으로:**
- ✅ Google Sheets에 기록됨
- ✅ 남은량 계산됨
- ✅ 상태 표시됨

---

### View (화면) 커스터마이징

#### 오늘 데이터만 보기

```
1. UX 탭 → Views
2. Daily_Usage 뷰 선택
3. "View Options" → "Filter"
4. 조건 추가:
   [date] = TODAY()
5. Save
```

#### 위험 항목만 보기

```
1. 새 View 생성: "위험항목"
2. Source: Daily_Usage
3. Filter:
   [status] = "🔴 위험"
```

---

## 🔄 자동화 (Automation)

AppSheet 무료 플랜: **월 500회 자동화!**

### 남은량 위험 시 이메일 알림

```
1. 왼쪽 "Automation" 탭
2. "Create a new bot" 클릭
3. Bot name: "위험알림"
4. Event:
   - Table: Daily_Usage
   - Adds or Updates
5. Condition:
   [remaining] <= 10
6. Task:
   - Action: "Send email"
   - To: 내 이메일
   - Subject: "위험: {account_id} - {service_id}"
   - Body: "남은량: {remaining}개"
7. Save
```

### 매일 요약 리포트

```
1. 새 Bot: "일일요약"
2. Event: Schedule
   - Daily at 9:00 AM
3. Process:
   - 오늘 날짜 Daily_Usage 조회
   - 위험 항목 필터링
4. Task:
   - Send email with summary
```

---

## 📊 데이터 관리

### Google Sheets에서 직접 수정

**AppSheet의 장점:**
- Google Sheets 수정 → 앱 즉시 반영
- 앱에서 입력 → Sheets 즉시 업데이트

**활용:**
```
1. 대량 데이터는 Sheets에서 편집
2. 일상 입력은 앱에서
3. 분석은 Sheets에서 (차트, 피벗)
```

---

## 💰 무료 플랜 제한

### 무료로 가능한 것:

- ✅ 무제한 앱 개발
- ✅ 무제한 테스트
- ✅ 10명 사용자
- ✅ 월 500회 자동화
- ✅ Google Sheets/Excel 연동
- ✅ 모바일 앱
- ✅ 오프라인 모드

**개인 사용엔 완벽!**

### 유료 필요한 경우:

- 10명 이상 사용자
- 500회 이상 자동화/월
- Premium 데이터 소스 (SQL 등)

**하지만 개인은 무료로 충분!**

---

## 🆚 다른 도구 비교

| 항목 | Glide | Clappia | Airtable | **AppSheet** |
|------|-------|---------|----------|--------------|
| **Google 통합** | 보통 | 낮음 | 낮음 | **완벽** |
| **무료 플랜** | 제한적 | 제한적 | 좋음 | **최고** |
| **설정 시간** | 30분 | 1시간 | 5분 | **3분** |
| **모바일 앱** | PWA | PWA | 네이티브 | **네이티브** |
| **자동화** | 유료 | 복잡 | 월100회 | **월500회** |
| **데이터 소스** | Sheets 전환 | Excel 업로드 | 자체 DB | **Sheets 직접** |

**결론: Google 사용자라면 AppSheet 최고!** 🏆

---

## 🎯 실제 시나리오

### 아침 출근길 (30초)

```
📱 AppSheet 앱 열기
➕ Daily_Usage에서 "+" 클릭
📅 날짜: 오늘 (자동)
👤 아이디: A01 (드롭다운)
🌐 사이트: ChatGPT (드롭다운)
🔢 사용량: 15
💾 저장

→ Google Sheets 즉시 업데이트!
→ 남은량 자동 계산!
→ 위험하면 이메일 발송!
```

### 주간 분석 (5분)

```
💻 Google Sheets 열기
📊 피벗 테이블 생성
📈 아이디별 사용량 추이 확인
💭 다음 주 전략 수립
```

---

## 🔧 문제 해결

### Q1: 앱이 데이터 못 읽어요

**A:** Regenerate structure
```
에디터 상단 "Regenerate structure" 클릭
→ 시트 구조 재인식
```

### Q2: 드롭다운이 안 보여요

**A:** Ref 타입 설정
```
Data 탭 → 컬럼 → Type을 "Ref"로 변경
```

### Q3: 모바일에서 느려요

**A:** Sync 설정 확인
```
Settings → Offline/Sync
→ Delayed sync 활성화
```

---

## 🎓 학습 리소스

### 공식 문서
- [AppSheet 시작하기](https://support.google.com/appsheet/answer/11581986)
- [앱 만들기 가이드](https://about.appsheet.com/how-to-create-an-app/)
- [Google Skills Lab](https://www.skills.google/focuses/19041)

### 비디오 튜토리얼
- YouTube: "AppSheet tutorial 2025"
- [Udemy 무료 코스](https://www.udemy.com/course/create-business-applications-with-appsheet/)

### 커뮤니티
- [AppSheet Community](https://community.appsheet.com/)

---

## 🚀 다음 단계

### 오늘:
1. ✅ Google Sheets 생성
2. ✅ AppSheet 앱 생성
3. ✅ 모바일 앱 설치
4. ✅ 첫 데이터 입력

### 이번 주:
1. 드롭다운 설정
2. View 커스터마이징
3. 첫 자동화 만들기

### 다음 주:
1. 남은량 자동 계산
2. 이메일 알림 설정
3. 대시보드 만들기

---

## 🏁 결론

**Google AppSheet = 최고의 선택!**

✅ **가장 쉬움** - 3분 시작
✅ **완전 무료** - 개인 사용 충분
✅ **Google 완벽 통합** - Sheets 직접 연동
✅ **강력한 자동화** - 월 500회
✅ **네이티브 앱** - iOS/Android

**Google 사용자라면 AppSheet가 답입니다!** 🎯

---

## Sources

- [How to create an app | Google AppSheet](https://about.appsheet.com/how-to-create-an-app/)
- [Get started with AppSheet](https://support.google.com/appsheet/answer/11581986)
- [AppSheet Tutorial | Pretius](https://pretius.com/blog/google-appsheet-tutorial)
- [Google AppSheet Skills Lab](https://www.skills.google/focuses/19041)
- [Create Business Applications with AppSheet | Udemy](https://www.udemy.com/course/create-business-applications-with-appsheet/)

---

**지금 바로 시작하세요!** 🚀
