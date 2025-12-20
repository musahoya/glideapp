# 🚀 Clappia로 구글 아이디 무료할당량 관리 앱 만들기

## 📋 목차

1. [Clappia vs Glide 비교](#clappia-vs-glide-비교)
2. [앱 만들기 3단계](#앱-만들기-3단계)
3. [앱 설정 및 커스터마이징](#앱-설정-및-커스터마이징)
4. [워크플로우 자동화](#워크플로우-자동화)
5. [실전 사용법](#실전-사용법)

---

## 🆚 Clappia vs Glide 비교

| 항목 | Clappia ✅ | Glide ❌ |
|------|-----------|---------|
| **Excel 연동** | 직접 업로드 | Google Sheets 변환 필요 |
| **무료 플랜** | 무제한 앱 + 100명 | 매우 제한적 |
| **가격** | $0 (무료로 충분) | $199/월 (Business) |
| **워크플로우 자동화** | 무료 플랜 포함 | 유료만 가능 |
| **데이터 소유권** | Excel 파일로 완전 소유 | Google Sheets 의존 |
| **오프라인 작업** | Excel 수정 후 재업로드 | 불가능 |
| **학습 곡선** | 매우 쉬움 (드래그앤드롭) | 중간 (Relation/Computed Column) |

**결론**: Clappia가 압도적으로 유리! 🎯

---

## 📱 앱 만들기 3단계

### 1️⃣ Clappia 가입 (2분)

1. https://www.clappia.com 접속
2. **Sign Up Free** 클릭
3. Google 계정으로 로그인
4. Workplace 이름 입력 (예: "내 관리 앱")

✅ 가입 완료!

---

### 2️⃣ Excel 파일 업로드 (1분)

**방법 A: AI Assistant 사용 (추천)**

1. 왼쪽 메뉴에서 **AI Assistant** 클릭
2. 채팅창에서 **+ 아이콘** 클릭
3. `구글아이디_무료할당량_관리_Clappia템플릿.xlsx` 업로드
4. "Create app from this Excel file" 입력
5. **자동으로 앱 생성됨!** 🎉

**방법 B: 수동 업로드**

1. 왼쪽 메뉴 **More** → **Create App from Excel**
2. Excel 파일 업로드
3. 각 시트별로 앱이 자동 생성됨

---

### 3️⃣ 앱 확인 및 테스트 (3분)

생성된 앱 목록:
- ✅ **Daily_Usage** (메인 앱)
- ✅ **Accounts** (구글 아이디 관리)
- ✅ **Services** (사이트 관리)
- ✅ **Account_Service** (가입 매핑)

각 앱을 클릭하면 자동으로 생성된 화면이 보입니다!

---

## ⚙️ 앱 설정 및 커스터마이징

### 🎯 Daily_Usage 앱 설정 (가장 중요!)

이 앱이 **매일 사용할 메인 화면**입니다.

#### Step 1: 필드 타입 최적화

1. **Daily_Usage** 앱 열기
2. 오른쪽 **App Design** 패널에서 각 필드 클릭
3. 필드 타입 변경:

| 필드명 | 변경 전 | 변경 후 | 설정 방법 |
|--------|---------|---------|-----------|
| 날짜 | Text | **Date Selector** | Field Type → Date |
| account_id | Text | **Dropdown** | Field Type → Dropdown → Data from App: Accounts |
| service_id | Text | **Dropdown** | Field Type → Dropdown → Data from App: Services |
| 사용량 | Text | **Number** | Field Type → Number |
| 남은량 | Text | **Calculated Field** | Formula: 총할당량 - 사용량 |

#### Step 2: Dropdown 설정 (중요!)

**account_id Dropdown 설정:**
```
1. Field Type: Dropdown
2. Options Source: Data from App
3. Select App: Accounts
4. Display Field: google_id
5. Value Field: account_id
```

**service_id Dropdown 설정:**
```
1. Field Type: Dropdown
2. Options Source: Data from App
3. Select App: Services
4. Display Field: 사이트명
5. Value Field: service_id
```

#### Step 3: 자동 계산 필드 추가

**총할당량 자동 조회:**
```
1. 필드명: 총할당량
2. Field Type: Calculated Field
3. Formula: LOOKUP(service_id, Services, 일일무료한도)
```

**남은량 자동 계산:**
```
1. 필드명: 남은량
2. Field Type: Calculated Field
3. Formula: 총할당량 - 사용량
```

**상태 자동 판정:**
```
1. 필드명: 상태
2. Field Type: Calculated Field
3. Formula:
   IF(남은량 / 총할당량 <= 0.2, "위험",
      IF(남은량 / 총할당량 <= 0.5, "주의", "안정"))
```

#### Step 4: 조건부 서식 (색상 표시)

**남은량 필드 색상:**
1. 남은량 필드 클릭
2. **Conditional Formatting** 활성화
3. 조건 추가:

```
조건 1: 남은량 / 총할당량 <= 0.2
색상: 빨강 (#FF0000)

조건 2: 남은량 / 총할당량 <= 0.5
색상: 노랑 (#FFC000)

조건 3: 남은량 / 총할당량 > 0.5
색상: 초록 (#70AD47)
```

---

### 📧 Accounts 앱 설정

이 앱은 **구글 아이디를 추가/수정**할 때만 사용합니다.

#### 필드 설정:

| 필드명 | 타입 | 설명 |
|--------|------|------|
| account_id | Text (Auto-generated) | A01, A02, ... 자동 생성 |
| google_id | Email | 이메일 형식 검증 |
| 메모 | Text | 계정 용도 설명 |
| 활성 | Switch | TRUE/FALSE 토글 |

#### Auto-generated ID 설정:
```
1. account_id 필드 클릭
2. Field Type: Auto Number
3. Prefix: A
4. Start From: 01
5. Format: A{00}
```

---

### 🌐 Services 앱 설정

**사이트 추가/수정**용 앱입니다.

| 필드명 | 타입 | 설정 |
|--------|------|------|
| service_id | Auto Number | Prefix: S, Format: S{00} |
| 사이트명 | Text | - |
| URL | URL | 자동 링크 생성 |
| 일일무료한도 | Number | - |
| 리셋주기 | Dropdown | Options: DAILY, WEEKLY, MONTHLY |

---

## 🔄 워크플로우 자동화

Clappia의 **무료 플랜에서 가능한** 자동화입니다!

### 1️⃣ 매일 자동 알림 (남은량 위험 시)

**시나리오**: 남은량이 20% 이하인 항목이 있으면 알림

```
Trigger: Daily at 9:00 AM
Condition: 남은량 / 총할당량 <= 0.2
Action: Send Email / WhatsApp
Message: "⚠️ {google_id}의 {사이트명} 남은량 {남은량}개 (위험)"
```

**설정 방법:**
1. Daily_Usage 앱 → **Workflows** 탭
2. **Add Workflow** 클릭
3. Trigger: **Scheduled** → Daily 9:00 AM
4. Condition: 위 조건 입력
5. Action: **Send Notification**

---

### 2️⃣ 사용량 입력 시 자동 요약

**시나리오**: 사용량 입력 후 오늘 전체 요약 자동 생성

```
Trigger: On Submit (Daily_Usage)
Action: Update Dashboard
Data: 오늘 날짜 기준 모든 아이디의 남은량 합계
```

---

### 3️⃣ 남은량 0 이하 시 자동 차단

```
Trigger: On Submit
Condition: 남은량 < 0
Action: Show Error Message
Message: "❌ 무료 한도를 초과했습니다. 다른 아이디를 사용하세요."
```

---

## 📲 실전 사용법

### 매일 아침 루틴 (30초)

1. **Daily_Usage 앱** 열기
2. **+ Add New** 클릭
3. 입력:
   - 날짜: 오늘 (자동 선택됨)
   - account_id: 드롭다운에서 선택
   - service_id: 드롭다운에서 선택
   - 사용량: 숫자 입력
4. **Submit** 클릭
5. 자동으로 남은량/상태 계산됨! 🎉

---

### 새 구글 아이디 추가 (1분)

1. **Accounts 앱** 열기
2. **+ Add New** 클릭
3. 입력:
   - account_id: 자동 생성 (A04, A05...)
   - google_id: 이메일 입력
   - 메모: "신규 계정" 등
   - 활성: ON
4. **Submit** → 즉시 Daily_Usage에서 선택 가능!

---

### 새 사이트 추가 (1분)

1. **Services 앱** 열기
2. **+ Add New** 클릭
3. 입력:
   - service_id: 자동 생성 (S05, S06...)
   - 사이트명: "NotebookLM" 등
   - URL: https://...
   - 일일무료한도: 30
   - 리셋주기: DAILY
4. **Submit**
5. **Account_Service 앱**에서 어떤 아이디가 가입했는지 매핑

---

## 📊 대시보드 보기

### 내장 대시보드 사용

Clappia는 자동으로 대시보드를 생성합니다:

1. 왼쪽 메뉴 **Reports** 클릭
2. **Add Report** 클릭
3. Data Source: **Daily_Usage**
4. Chart Type: 선택
   - **Bar Chart**: 아이디별 남은량
   - **Pie Chart**: 상태별 분포 (위험/주의/안정)
   - **Table**: 전체 상세 내역

5. Filter: **날짜 = Today**
6. **Save** 클릭

---

## 📱 모바일 앱으로 사용하기

### 안드로이드

1. Clappia 앱 다운로드:
   - Google Play Store → "Clappia" 검색
   - 또는: https://play.google.com/store/apps/details?id=com.clappia

2. 로그인 → 내 앱 자동 동기화
3. **Daily_Usage** 앱을 즐겨찾기에 추가
4. 홈 화면에 바로가기 추가

**장점:**
- ✅ 네이티브 앱처럼 빠름
- ✅ 오프라인에서도 작동 (나중에 동기화)
- ✅ 푸시 알림 받기

### iOS

1. App Store → "Clappia" 검색 및 설치
2. 동일한 방식으로 사용

---

## 🎯 고급 기능 (선택)

### 1️⃣ REST API 연동

Clappia 무료 플랜에서 **REST API** 제공!

```bash
# 오늘 사용량 조회 API
curl -X GET "https://api.clappia.com/v1/apps/{app_id}/submissions" \
  -H "Authorization: Bearer {your_token}" \
  -H "Content-Type: application/json"
```

**활용 예시:**
- Python 스크립트로 자동 데이터 분석
- 다른 앱과 연동
- 자동 백업

---

### 2️⃣ Google Sheets 양방향 동기화

1. **Integrations** → **Google Sheets** 연결
2. Daily_Usage 데이터를 Google Sheets에 자동 백업
3. Sheets에서 수정해도 Clappia에 반영

---

### 3️⃣ WhatsApp 알림

```
Workflow:
Trigger: 남은량 < 10
Action: Send WhatsApp Message
To: {내 전화번호}
Message: "🚨 긴급: {사이트명} 남은량 {남은량}개"
```

---

## 💡 실전 팁

### ✅ DO (권장)

1. **매일 아침** Daily_Usage에 기록 (습관화)
2. **주말에** 한 주간 사용 패턴 확인
3. **월초에** 새 아이디 추가 고려
4. **Bulk Upload** 기능으로 과거 데이터 일괄 입력

### ❌ DON'T (비추천)

1. account_id, service_id 직접 입력 (드롭다운 사용)
2. Excel 파일 삭제 (백업용으로 보관)
3. 무료 한도 초과 후 입력 (미리 확인)

---

## 🆚 Glide 대비 개선점 요약

| 개선 항목 | Glide 방식 | Clappia 방식 |
|----------|-----------|--------------|
| **데이터 입력** | Google Sheets 열고 수동 입력 | 앱에서 드롭다운 선택만 |
| **계산 필드** | Computed Column 수동 설정 | 자동 인식 + 수식 입력 |
| **알림** | 유료 플랜만 가능 | 무료로 WhatsApp/Email |
| **오프라인** | 불가능 | 모바일 앱으로 가능 |
| **데이터 소유** | Google 의존 | Excel 파일로 완전 소유 |
| **확장성** | Relation 복잡 | Lookup 간단 |

---

## 🔗 참고 자료

- [Clappia 공식 문서](https://www.clappia.com/help/create-apps-using-excel)
- [Excel to App 가이드](https://www.clappia.com/blog/convert-excel-spreadsheet-into-an-app)
- [Clappia 비디오 튜토리얼](https://www.clappia.com/videos/create-apps-using-excel)

---

## 📞 다음 단계

이제 다음 중 선택하세요:

1. **바로 시작**: Excel 파일 다운로드 → Clappia 가입 → 앱 생성
2. **더 알아보기**: 워크플로우 자동화 심화 학습
3. **커스터마이징**: UI 디자인 변경, 차트 추가

궁금한 점 있으면 언제든 물어보세요! 🚀
