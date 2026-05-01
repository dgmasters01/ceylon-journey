# CEYLON JOURNEY — 변경 이력 (CHANGELOG.md)

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
