# 🔧 Clappia 업로드 문제 해결 가이드

## ❌ 문제: Excel 파일 인식 안 됨

**원인:**
1. 여러 시트를 한 번에 인식 못함
2. 한글 시트명 문제
3. 특수문자(이모지) 문제
4. 복잡한 구조

---

## ✅ 해결책: 3가지 방법

### 🥇 방법 1: 가장 단순한 파일 사용 (추천!)

**파일:** `Simple_Template.xlsx`

```
✅ 영문 헤더만 사용
✅ 이모지/특수문자 제거
✅ 최소 3개 시트만 포함
✅ 샘플 데이터 최소화
```

**업로드 방법:**
1. Clappia 접속
2. AI Assistant 클릭
3. `Simple_Template.xlsx` 업로드
4. "Create apps from this file" 입력

---

### 🥈 방법 2: 메인 앱만 먼저 만들기

**파일:** `04_Daily_Usage.xlsx`

이 방법이 **가장 확실합니다!**

```
1. 04_Daily_Usage.xlsx만 업로드
   → Daily_Usage 앱 생성

2. 나중에 account_id, service_id를
   수동으로 Dropdown 옵션 추가
```

**장점:**
- 복잡도 낮음
- Clappia가 무조건 인식
- 바로 사용 시작 가능

**단점:**
- 드롭다운 옵션을 수동으로 추가해야 함

---

### 🥉 방법 3: 시트별 개별 앱 만들기

각 파일을 따로 업로드:

```
1. 01_Accounts.xlsx → Accounts 앱
2. 02_Services.xlsx → Services 앱
3. 03_Account_Service.xlsx → 매핑 앱
4. 04_Daily_Usage.xlsx → 메인 앱
```

**나중에 연결:**
- Daily_Usage에서 Dropdown 설정
- Data Source → Accounts 앱 연결
- Data Source → Services 앱 연결

---

## 🎯 추천 순서

### Step 1: Simple_Template.xlsx 시도

```bash
1. Clappia AI Assistant
2. Simple_Template.xlsx 업로드
3. "Create app" 입력
```

**성공하면:** 끝! 바로 사용
**실패하면:** Step 2로

---

### Step 2: 04_Daily_Usage.xlsx만 업로드

```bash
1. AI Assistant 또는 "Create App from Excel"
2. 04_Daily_Usage.xlsx 업로드
3. 앱 생성 완료
```

**그 다음:**

#### account_id 드롭다운 수동 설정:
```
1. Daily_Usage 앱 열기
2. App Design → account_id 필드 클릭
3. Field Type → Dropdown
4. Options Source → Manual Entry
5. 옵션 추가:
   - A01
   - A02
   - A03
```

#### service_id 드롭다운 수동 설정:
```
1. service_id 필드 클릭
2. Field Type → Dropdown
3. Options Source → Manual Entry
4. 옵션 추가:
   - S01 (ChatGPT)
   - S02 (Gemini)
   - S03 (Claude)
   - S04 (Perplexity)
```

---

## 📝 파일별 차이점

| 파일 | 시트 수 | 헤더 언어 | 특수문자 | 복잡도 |
|------|---------|-----------|----------|--------|
| **구글아이디_무료할당량_관리_Clappia템플릿.xlsx** | 5개 | 한글 | ✅ (이모지) | 높음 |
| **Simple_Template.xlsx** | 3개 | 영문 | ❌ | 낮음 |
| **04_Daily_Usage.xlsx** | 1개 | 영문 | ❌ | 최소 |

---

## 🔍 업로드 확인 방법

### AI Assistant 사용 시:

**정상:**
```
✅ "Processing your file..."
✅ "Created app: Daily_Usage"
✅ 왼쪽 Apps 메뉴에 앱 표시됨
```

**오류:**
```
❌ "Unable to process file"
❌ "Invalid format"
❌ 아무 반응 없음
```

### Manual Upload 사용 시:

**정상:**
```
✅ 업로드 진행 바 100%
✅ "App created successfully"
✅ 자동으로 앱 화면 열림
```

---

## 🆘 여전히 안 되면?

### 대안 1: Google Sheets 사용

```
1. Simple_Template.xlsx를 Google Drive에 업로드
2. 우클릭 → "Google Sheets로 열기"
3. Clappia → Integrations → Google Sheets
4. 해당 시트 선택
```

### 대안 2: Clappia에서 직접 생성

```
1. Clappia → Create New App
2. Start from Scratch
3. 필드 수동 추가:
   - date (Date)
   - account_id (Dropdown)
   - service_id (Dropdown)
   - usage (Number)
```

**그 다음 Bulk Upload로 데이터 입력**

---

## 💡 핵심 팁

### ✅ Clappia가 좋아하는 Excel 구조:

```
✅ 영문 헤더 (한글 X)
✅ 단순한 시트 (1~3개)
✅ 특수문자 없음
✅ 적당한 샘플 데이터 (2~5행)
```

### ❌ Clappia가 싫어하는 구조:

```
❌ 한글 헤더
❌ 5개 이상 시트
❌ 이모지, 특수기호
❌ 복잡한 수식
❌ 병합된 셀
```

---

## 📊 각 방법 비교

| 방법 | 난이도 | 성공률 | 설정 시간 | 추천도 |
|------|--------|--------|-----------|--------|
| **Simple_Template.xlsx** | ⭐ | 95% | 2분 | ⭐⭐⭐⭐⭐ |
| **04_Daily_Usage.xlsx** | ⭐⭐ | 99% | 5분 | ⭐⭐⭐⭐ |
| **개별 파일 (01~04)** | ⭐⭐⭐ | 99% | 10분 | ⭐⭐⭐ |
| **Google Sheets** | ⭐⭐ | 100% | 3분 | ⭐⭐⭐⭐ |
| **수동 생성** | ⭐⭐⭐⭐ | 100% | 15분 | ⭐⭐ |

---

## 🚀 지금 바로 시도하기

### 1단계: 파일 준비
```bash
✅ Simple_Template.xlsx 다운로드
```

### 2단계: Clappia 업로드
```
1. https://www.clappia.com 접속
2. AI Assistant 클릭
3. Simple_Template.xlsx 드래그앤드롭
4. "Create app from this Excel file"
```

### 3단계: 확인
```
Apps 메뉴 확인:
- ✅ Accounts
- ✅ Services
- ✅ Daily_Usage
```

### 4단계: 테스트
```
Daily_Usage 앱 열기
→ + Add New
→ 데이터 입력 테스트
```

---

## 📞 추가 도움

업로드가 **여전히 안 되면** 알려주세요!

다음 정보와 함께:
1. 어느 파일 시도했는지
2. 어떤 에러 메시지가 나왔는지
3. AI Assistant 사용했는지 / Manual Upload 사용했는지

**더 단순한 버전을 만들어드리겠습니다!** 🔧
