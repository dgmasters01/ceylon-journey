# CEYLON JOURNEY — 변경 이력 (CHANGELOG.md)

---

## 2026-05-01 (3순위: 개인정보처리방침 + 예약폼 제3자 동의)

### [privacy.html 신규 생성 — 개인정보처리방침 전문]
- **변경:** 「개인정보 보호법」 제30조 표준양식 기반 개인정보처리방침 전문 신규 작성.
- **구성:** 12개 조항. 제1조 처리 목적 / 제2조 수집 항목·방법 / 제3조 보유·이용 기간 / **제4조 제3자 제공 (5개 표 — 항공사·현지 지상수배사·호텔·보험사·PG)** / 제5조 처리 위탁 (Vercel·Supabase·Resend·카카오·PG) / 제6조 국외 이전 (스리랑카·미국 등) / 제7조 정보주체 권리 / 제8조 안전성 확보 조치 / 제9조 쿠키 / 제10조 보호책임자 / 제11조 권익침해 구제 / 제12조 방침 변경.
- **회사명 표기:** 본문 "회사"로 통일, terms.html과 동일한 정의 패턴 사용. 사업자 정보(상호·등록번호 등)는 `/about#legal`로 링크.
- **디자인:** terms.html과 100% 동일한 디자인 토큰(#0E1410 다크 + #C9A84C 골드, Cormorant Garamond + Noto Sans KR), nav/footer 일관성 유지.
- **목차(TOC):** 12개 조항 앵커 링크 (`#a1`~`#a12`). 모바일 반응형 지원.
- **법적 표:** 보유기간 표(8행), 제3자 제공 표(5행), 위탁 표(5행), 국외이전 표(4행), 권익침해 구제기관 표(4행) 등 5개 표 포함.
- **관련 파일:** privacy.html (신규)

### [vercel.json — /privacy 라우팅 추가]
- **변경:** routes 배열에 `{ "src": "/privacy", "dest": "/privacy.html" }` 추가.
- **이유:** consumer_site / terms 푸터 "개인정보처리방침" 링크 정상 작동을 위해.
- **관련 파일:** vercel.json

### [consumer_site.html 예약폼 — 제3자 제공 동의(필수) 추가]
- **변경:** 약관 동의 블록 3항목 → 4항목으로 확장.
  - [필수] 이용약관 동의 (`rf-agree`)
  - [필수] 개인정보 수집·이용 동의 (`rf-agree2`)
  - **[필수] 개인정보 제3자 제공 동의 (`rf-agree3`) — 신규**
  - [선택] 마케팅 수신 동의 (기존 `rf-agree3` → `rf-agree4`로 변경)
- **변경:** 약관 보기 링크 `<span onclick="event.preventDefault()">` → 실제 페이지 링크 `<a href="/terms" target="_blank">` / `<a href="/privacy" target="_blank">` / `<a href="/privacy#a4" target="_blank">`로 교체.
- **변경:** `submitReserve()` 검증 로직에 `agree3` 필수 체크 추가. 미동의 시 "필수 약관 3개에 모두 동의해주세요." 알림.
- **이유:** 패키지 여행 특성상 항공사·현지 지상수배사·호텔에 개인정보 제공이 필수적이므로 사전 동의 확보 필요. 「개인정보 보호법」 제17조 제3자 제공 별도 동의 의무 준수.
- **백업:** `consumer_site_backup_before_privacy.html` (BEFORE 시점, git ac814d9 기준)
- **관련 파일:** consumer_site.html

---

## 2026-05-01

### [푸터 미니멀 글로벌 스타일 재설계 — consumer_site.html]
- **변경:** 푸터 ft-bottom 영역에서 사업자정보 텍스트("CEYLON JOURNEY · 사업자등록번호 · 여행업 등록번호 — 설정 후 자동 반영") 제거. © 2026 + "회사 소개" 링크로 미니멀화.
- **변경:** "법적 고지" 컬럼에 4개 링크 정상 연결 — 이용약관(`/terms`), 개인정보처리방침(`/privacy`), 취소·환불 규정(`/terms#cancel`), 사업자 정보(`/about#legal` — 신규 추가).
- **변경:** "고객 지원" 컬럼 카카오 상담 링크 → `https://pf.kakao.com/PLACEHOLDER` (target="_blank") 임시 적용.
- **변경:** 카카오 플로팅 버튼(.kk-float) `<button onclick="alert(...)">` → `<a href="https://pf.kakao.com/PLACEHOLDER">`로 교체. alert 팝업 제거.
- **이유:** Booking.com / Airbnb / Klook 등 글로벌 톱티어와 동일한 Progressive Disclosure 원칙 적용. 푸터는 브랜드 노출, 법적 정보는 별도 페이지 링크. [대괄호] 임시값의 외부 노출 0건 확보.
- **백업:** `consumer_site_backup_20260501.html`
- **관련 파일:** consumer_site.html

### [terms.html 신규 생성 — 이용약관 전문]
- **변경:** 국외여행 표준약관(공정거래위원회 표준약관 제10021호) 기반 이용약관 전문 신규 작성.
- **구성:** 6개 장 / 21개 조항. 제1장 총칙(목적·정의·약관 명시) / 제2장 계약체결(거절·특약·계약서 교부) / 제3장 여행 요금(포함·미포함·요금변경·결제) / 제4장 계약의 해제 및 해지(회사 해제·이용자 해제 #cancel·출발 후 해지) / 제5장 회사의 책임(손해배상·계약변경·보험) / 제6장 기타(여권비자·개인정보·관할법원·약관효력).
- **제12조 취소·환불 규정:** 소비자분쟁해결기준 기반 6단계 환불표(30일 전 전액 → 당일 50%) + 항공권/현지호텔 환불불가 항목 별도 처리 안내.
- **회사명 표기:** 본문은 "회사"로 통일, 제2조에서 "CEYLON JOURNEY 브랜드로 국외여행 상품을 기획·판매하는 사업자"로 정의 → 추후 법인 정보 확정 시 1조만 교체하면 끝.
- **디자인:** consumer_site.html 동일 디자인 토큰(#0E1410 다크 + #C9A84C 골드, Cormorant Garamond + Noto Sans KR). 네비/푸터 일관성 유지.
- **목차(TOC):** 6개 장 + 취소·환불 규정 앵커 링크. 모바일 반응형 지원.
- **관련 파일:** terms.html (신규, 421줄)

### [vercel.json — /terms 라우팅 추가]
- **변경:** routes 배열에 `{ "src": "/terms", "dest": "/terms.html" }` 추가.
- **이유:** consumer_site 푸터의 "이용약관", "취소·환불 규정"(`/terms#cancel`) 링크 정상 작동을 위해.
- **관련 파일:** vercel.json

---

## 2026-04-29

### [TW Standard System v1 적용]
- **변경:** Business Docs / Page Gallery / 작업 기록 / 검증 워크플로 / 자율 작업 큐 5개 모듈을 admin_final.html에 통합
- **이유:** TW B2B에서 검증된 프로젝트 표준 시스템을 CEYLON JOURNEY에도 적용하여 작업 방식 통일
- **관련 파일:** admin_final.html, BUSINESS.md, DECISIONS.md, USER_JOURNEY.md, BACKLOG.md, CHANGELOG.md, SOLO_WORK_QUEUE.md

### [브랜드 변경 — 여행능력자들 → CEYLON JOURNEY]
- **변경:** 소비자 상품 페이지를 '여행능력자들' 브랜딩에서 CEYLON JOURNEY 독립 브랜드로 전면 재설계
- **이유:** 프리미엄 스리랑카 패키지에 맞는 독자적 브랜드 정체성 확립
- **관련 파일:** consumer_site.html (sri-lanka-tour.html로 재작성)

### [상품 페이지 재설계]
- **변경:** 블로그 형태 → 프리미엄 여행사 수준 상품 상세 페이지로 완전 재구축
- **이유:** 기존 페이지가 구매 전환에 부적합. 시기리아/나인아치/갈레 등 장소별 이미지+매력 설명 추가, 7일 전일정 상세화
- **관련 파일:** consumer_site.html
