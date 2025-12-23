# 📊 Google Sheets 템플릿 만들기

> **1분이면 완성!**

---

## ⚡ 빠른 시작

### 1️⃣ Google Sheets 열기

```
https://sheets.google.com
→ 새 스프레드시트 만들기
```

---

### 2️⃣ 시트 3개 만들기

#### 시트 1: Accounts

**헤더 (A1:D1):**
```
account_id | email | memo | active
```

**샘플 데이터:**
```
A01 | user1@gmail.com | 주력 계정 | TRUE
A02 | user2@gmail.com | 서브 계정 | TRUE
A03 | user3@gmail.com | 테스트 계정 | TRUE
```

---

#### 시트 2: Services

**헤더 (A1:E1):**
```
service_id | site_name | url | daily_limit | reset_cycle
```

**샘플 데이터:**
```
S01 | ChatGPT | https://chat.openai.com | 50 | DAILY
S02 | Gemini | https://gemini.google.com | 60 | DAILY
S03 | Claude | https://claude.ai | 45 | DAILY
S04 | Perplexity | https://perplexity.ai | 5 | DAILY
```

---

#### 시트 3: Daily_Usage (메인!)

**헤더 (A1:D1):**
```
date | account_id | service_id | usage
```

**샘플 데이터:**
```
2025-01-15 | A01 | S01 | 10
2025-01-15 | A01 | S02 | 20
2025-01-15 | A02 | S01 | 15
```

---

### 3️⃣ 완료!

Google Sheets 파일 이름: `구글아이디_무료할당량_관리`

**이제 AppSheet로 연결하세요!**

---

## 💡 팁

### CSV 파일로 빠르게 가져오기

프로젝트에 포함된 CSV 파일들:
- `accounts.csv`
- `services.csv`
- `daily_usage.csv`

**사용법:**
1. Google Sheets에서 `파일 → 가져오기`
2. `업로드` 탭 선택
3. CSV 파일 드래그
4. `데이터 가져오기` 클릭

**3개 파일 모두 가져오면 끝!**

---

## 🔗 다음 단계

**APPSHEET_GUIDE.md** 파일을 열어서 앱 만들기!
