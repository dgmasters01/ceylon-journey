# CEYLON JOURNEY — 변경 이력 (CHANGELOG.md)

---

## 2026-05-01 (4순위: 회사 소개 페이지)

### [about.html 신규 생성 — 회사 소개 + 사업자 정보 #legal]
- **변경:** 럭셔리 톤 풀 페이지 신규 작성. 7개 섹션 구성 (hero / story / value / promise / metric / legal / cta).
- **HERO:** 풀스크린 다크 + 골드 라디얼 그라디언트 + 그레인 텍스처. 4개 핵심 지표(8년+ / 5★ Hotels Only / Max 20인 / 100% Korean Guide) 메타 표기.
- **OUR STORY:** 4:5 이미지 + 스토리 텍스트 2단 그리드. 첫 단락 드롭캡(첫 글자 64px 골드) + 이탤릭 강조. "We craft Sri Lanka, slowly" 영문 카피.
- **WHY (차별점 6카드):** 3×2 그리드. 5성급 / 20인 소수정예 / 한국어 가이드 / 3식 풀보드 / 직항 / 8년 노하우. hover 시 골드 라인 애니메이션.
- **OUR PROMISE:** 큰 인용구 + 4단계 약속(I~IV 로마자, 출발 전 / 현지 / 호텔 / 귀국 후).
- **METRICS:** 4분할 숫자 카드 (2018 Founded / 6개국 / 5★ / 100%).
- **#legal 섹션:** 사업자 정보 11행 표. 상호·대표자·등록번호·소재지·연락처·개인정보책임자·호스팅 등. **본문 placeholder 7개는 추후 실제 값으로 1:1 교체 가능한 구조** (이지형 대표·카카오 채널·Vercel 호스팅 등 확정 항목은 즉시 표시).
- **CTA:** "이제, 당신의 차례입니다" 골드 primary 버튼 + 카카오 secondary 버튼.
- **톤:** "We/우리" 강조 (우리 23회), 팀 기반 프리미엄 여행 스튜디오 인상. 1인 사업 표시 없음.
- **디자인:** terms / privacy / consumer_site와 100% 동일한 디자인 토큰 (#0E1410 다크 + #C9A84C 골드, Cormorant Garamond + Noto Sans KR), nav/footer 완전 일치.
- **반응형:** 980px / 768px 2단계 미디어 쿼리. 모바일에서 사업자정보 표는 th/td 세로 적층.
- **앵커:** `#legal` 스크롤 마진 80px (nav 가림 방지).
- **관련 파일:** about.html (신규, 약 410줄)

### [vercel.json — /about 라우팅 추가]
- **변경:** routes 배열에 `{ "src": "/about", "dest": "/about.html" }` 추가.
- **이유:** terms·privacy·consumer_site 푸터에 이미 걸린 `/about` 및 `/about#legal` 링크 정상 작동을 위해.
- **관련 파일:** vercel.json

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
