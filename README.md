# 📱 구글 아이디 무료할당량 관리 앱

> **Glide → Clappia 마이그레이션 완료!** 🎉
> Excel 직접 업로드, 무료 플랜 무제한, 워크플로우 자동화 지원

---

## 🆚 왜 Clappia인가?

| 기능 | Glide ❌ | **Clappia ✅** |
|------|---------|---------------|
| Excel 연동 | Google Sheets 변환 필요 | **직접 업로드** |
| 무료 플랜 | 매우 제한적 | **무제한 앱 + 100명** |
| 가격 | $199/월 (Business) | **$0** |
| 자동화 | 유료만 | **무료 포함** |
| 학습 난이도 | 중 (Relation 복잡) | **쉬움** |

**결론: Clappia가 압도적으로 유리!** 🎯

---

## 📦 프로젝트 구성

```
glideapp/
├── 구글아이디_무료할당량_관리_Clappia템플릿.xlsx  ← 메인 템플릿
├── QUICKSTART.md                              ← 5분 빠른 시작
├── CLAPPIA_GUIDE.md                           ← 상세 가이드
├── create_excel_template.py                   ← 템플릿 생성 스크립트
├── readme,txt                                 ← 기존 Glide 방식
└── readme1.txt                                ← 기존 Glide 상세
```

---

## ⚡ 5분 빠른 시작

### 1️⃣ Clappia 가입
```
https://www.clappia.com
→ Sign Up Free
→ Google 계정 로그인
```

### 2️⃣ Excel 업로드
```
AI Assistant 클릭
→ + 버튼
→ 구글아이디_무료할당량_관리_Clappia템플릿.xlsx 업로드
→ "Create apps from this Excel file" 입력
```

### 3️⃣ 앱 사용 시작
```
Daily_Usage 앱 열기
→ + Add New
→ 드롭다운 선택 + 사용량 입력
→ Submit
```

**끝!** 🎉

---

## 📊 Excel 템플릿 구조

### 시트 구성 (5개)

#### 1. **Accounts** (구글 아이디 관리)
```
account_id | google_id          | 메모   | 활성
A01        | user1@gmail.com    | 주력   | TRUE
A02        | user2@gmail.com    | 서브   | TRUE
```

#### 2. **Services** (사이트 정보)
```
service_id | 사이트명   | URL                    | 일일무료한도 | 리셋주기
S01        | ChatGPT   | chat.openai.com        | 50          | DAILY
S02        | Gemini    | gemini.google.com      | 60          | DAILY
```

#### 3. **Account_Service** (가입 매핑)
```
account_id | service_id | 가입여부
A01        | S01        | TRUE
A01        | S02        | TRUE
```

#### 4. **Daily_Usage** ⭐ (메인 - 매일 입력)
```
날짜       | account_id | service_id | 총할당량 | 사용량 | 남은량 | 상태
2025-01-15 | A01        | S01        | 50       | 12     | 38     | 안정
```

#### 5. **사용가이드** (도움말)

---

## 🎯 주요 기능

### ✅ 구현된 기능

- [x] 구글 아이디 무제한 추가
- [x] 사이트 무제한 추가
- [x] 매일 사용량 기록
- [x] 남은량 자동 계산
- [x] 상태 자동 판정 (위험/주의/안정)
- [x] 드롭다운 선택 (오타 방지)
- [x] 색상 표시 (🔴🟡🟢)
- [x] 모바일 앱 지원
- [x] 워크플로우 자동화
- [x] REST API 제공

### 🔄 자동화 예시

**남은량 위험 시 알림:**
```
Trigger: Daily 9:00 AM
Condition: 남은량 / 총할당량 <= 0.2
Action: Send WhatsApp/Email
```

---

## 📱 사용 방법

### 매일 아침 루틴 (30초)

1. Daily_Usage 앱 열기
2. + Add New 클릭
3. 드롭다운 선택:
   - account_id: 사용할 구글 아이디
   - service_id: 사용할 사이트
4. 사용량 입력
5. Submit → 자동 계산!

### 새 아이디 추가 (1분)

1. Accounts 앱 열기
2. + Add New 클릭
3. 이메일 입력
4. Submit → Daily_Usage에서 바로 선택 가능!

---

## 📖 문서

| 파일 | 내용 | 대상 |
|------|------|------|
| **QUICKSTART.md** | 5분 빠른 시작 | 초보자 |
| **CLAPPIA_GUIDE.md** | 상세 가이드 + 커스터마이징 | 전체 |
| **Excel 템플릿** | 바로 사용 가능한 파일 | 전체 |

---

## 🔧 고급 기능

### REST API 사용
```bash
curl -X GET "https://api.clappia.com/v1/apps/{app_id}/submissions" \
  -H "Authorization: Bearer {token}"
```

### Google Sheets 동기화
```
Integrations → Google Sheets
→ 양방향 자동 동기화
```

### 대시보드 생성
```
Reports → Add Report
→ Chart Type: Bar/Pie/Table
→ Filter: 날짜 = Today
```

---

## 💡 핵심 팁

### ✅ DO (권장)

1. **드롭다운만 사용** (직접 입력 금지)
2. **매일 아침 습관화** (30초면 충분)
3. **Excel 파일 백업** (주 1회)
4. **Bulk Upload 활용** (과거 데이터 일괄 입력)

### ❌ DON'T (비추천)

1. account_id/service_id 직접 타이핑
2. Excel 원본 파일 삭제
3. 무료 한도 초과 후 입력

---

## 🎓 학습 리소스

### 공식 문서
- [Clappia Excel Import](https://www.clappia.com/help/create-apps-using-excel)
- [Convert Excel to App](https://www.clappia.com/blog/convert-excel-spreadsheet-into-an-app)
- [Video Tutorial](https://www.clappia.com/videos/create-apps-using-excel)

### 이 프로젝트 문서
- `QUICKSTART.md` - 5분 시작 가이드
- `CLAPPIA_GUIDE.md` - 완전 가이드

---

## 🔄 Glide에서 마이그레이션

### 기존 Glide 사용자라면?

**기존 방식 (복잡):**
```
Excel → Google Sheets 변환
→ Glide 연결
→ Relation 수동 설정
→ Computed Column 추가
→ $199/월 결제
```

**Clappia 방식 (간단):**
```
Excel 업로드
→ 자동 앱 생성
→ 끝! (무료)
```

**마이그레이션 시간: 5분**

---

## 🆓 무료 플랜 제한

| 항목 | 제한 |
|------|------|
| 앱 개수 | **무제한** ✅ |
| 사용자 | 100명 |
| 월 제출 | 400건 |
| 워크플로우 | **포함** ✅ |
| 모바일 앱 | **포함** ✅ |
| REST API | **포함** ✅ |

**일반 사용자에게 완전 충분!** 🎯

---

## 🐛 문제 해결

### Q1: 앱이 생성되지 않아요
**A**: 수동 업로드 시도
```
More → Create App from Excel → 파일 선택
```

### Q2: 드롭다운이 비어있어요
**A**: 원본 데이터 확인
```
Accounts 앱 → 아이디 있는지 확인
Services 앱 → 사이트 있는지 확인
```

### Q3: 남은량 자동 계산 안 돼요
**A**: Calculated Field 설정
```
CLAPPIA_GUIDE.md → "앱 설정" 섹션 참고
```

---

## 📞 지원

- 📧 이슈: GitHub Issues
- 📖 Wiki: 프로젝트 Wiki
- 💬 질문: Discussions

---

## 📄 라이선스

MIT License - 자유롭게 사용하세요!

---

## 🙏 기여

개선 아이디어 환영합니다!

1. Fork
2. Feature Branch 생성
3. Commit
4. Pull Request

---

## 🎉 마치며

**Glide의 복잡함에서 벗어나 Clappia의 간편함을 즐기세요!**

- ✅ 설정 시간: 5분
- ✅ 일일 사용: 30초
- ✅ 비용: $0

**지금 바로 시작하세요!** 🚀

---

**Made with ❤️ for better productivity**
