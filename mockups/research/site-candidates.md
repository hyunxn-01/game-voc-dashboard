# 참고 사이트 후보

게임 유저 VOC · 동향 대시보드(로스트아크)를 다시 구성할 때 참고할 실제 대시보드 · 사이트 후보다. 2026-11-01 조사. 전체 데이터는 `site-candidates.json`.

## 요약

- 찾은 곳 **324곳**(중복 1건 합침) · 열람 **37** · 검색 결과만 **287**
- 등급: 강력 추천 20 · 참고 116 · 부분 참고 126 · 제외 62
- **열람 범위**: 이 환경은 네트워크 정책으로 외부 사이트 대부분이 막혀 있다. 열 수 있었던 곳은 GitHub 저장소 파일(raw.githubusercontent.com)과 PyPI뿐이라, '열람'은 오픈소스 도구의 README 같은 문서를 읽은 것이다. **라이브 대시보드 화면을 직접 본 곳은 없다.** 나머지는 검색 결과 문장만으로 판정했고, 실제 화면과 다를 수 있다.
- 막힌 주소와 오류는 맨 아래 '열람 시도 기록'에 있다.

구성요소 ID: C01 이번 주 결론(AI 해석) · C02 이슈 후보와 AI 판단 · C03 이슈 근거 · C04 AI 정독 요약 · C05 운영 대응 전후 비교 · C06 급상승 키워드 · C07 글 수 지수(평시 = 100) · C08 감성 추이 · C09 VOC 주제 지도 · C10 주간 보고 · C11 AI 분류 정확도와 비용 · G 게임 지표

## 강력 추천 상위 20곳

### 1. RedditWatch — Aditya1001001 (오픈소스, MIT)

- URL: <https://github.com/Aditya1001001/RedditWatch> · 열어 본 문서: <https://raw.githubusercontent.com/Aditya1001001/RedditWatch/main/README.md> (GitHub README (스크린샷 이미지는 보지 않음))
- 열람 여부: **열람** · 접근 조건: 오픈소스 · 종류: 게임 커뮤니티 분석
- 맞는 구성요소: C04 AI 정독 요약, C09 VOC 주제 지도, C03 이슈 근거, C10 주간 보고, C11 AI 분류 정확도와 비용
- 무엇이 왜 맞나: README 기준: Signals 화면(테마별 묶음, 빈도 × 신호 강도 순위, 의미 검색, 내보내기), Analytics 화면(차트 · 추세 · 신호 강도), 서브레딧 카탈로그(283개 · 50분류), LLM 제공자 관리, Ask(선택한 대상에 자연어 질문, 근거 카드 첨부), 근거 인용 + 레딧 링크 리포트 내보내기
- AI 해석을 지표 · 근거에 묶는 방식: LLM이 글과 댓글을 읽어 통증 · 수요 신호(강도 0~100), 제품 언급(감성), 기회를 추출. 인용문은 원문에서 그대로 가져와야 하고 원문과 대조해 확인 못 한 인용은 제거. 신호 · Ask 답변 · 리포트에 서브레딧 맥락 · 인용 · 레딧 링크가 붙음. 자기 홍보 글은 가중치를 낮추고 댓글 적은 글은 LLM 호출 전에 건너뜀
- 참고할 점:
  - RedditWatch의 '인용문을 원문과 대조해 확인 못 하면 제거' → C04 정독 요약 인용문마다 원문 대조 결과를 표시하고 C11 신뢰도에 반영
  - RedditWatch의 'Ask 답변 아래 근거 카드' → C01 결론 · C02 AI 판단 문장마다 근거 글 카드(커뮤니티 · 추천 수 · 링크) 붙이기
  - RedditWatch의 '빈도 × 신호 강도로 테마 순위' → C09 주제 지도의 정렬 기준에 글 수뿐 아니라 부정 강도를 곱한 점수 추가

### 2. Guidance for Agentic Live Ops on AWS — Amazon Web Services

- URL: <https://docs.aws.amazon.com/solutions/agentic-live-ops-on-aws/> · 열어 본 문서: <https://raw.githubusercontent.com/aws-solutions-library-samples/guidance-for-agentic-live-ops-on-aws/main/README.md (+ docs/agent-response-formats.md)> (GitHub README와 docs/agent-response-formats.md)
- 열람 여부: **열람** · 접근 조건: 오픈소스 · 종류: 게임 라이브 운영
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C02 이슈 후보와 AI 판단, C03 이슈 근거, C11 AI 분류 정확도와 비용
- 무엇이 왜 맞나: README: 자연어 질문에 차트 · 표 · 출처 인용이 있는 답을 실시간 스트리밍. 채팅 왼쪽 에이전트 활동 피드에 어느 하위 에이전트 · 데이터 계층을 썼는지와 추론 단계. Monitor 페이지(/monitor)에 KPI 카드 · 이벤트 타임라인 · 실시간 지표 게이지, 이벤트 비율이 임계 규칙을 넘으면 Analysis Runner가 자동 실행되어 심각도 · 근본 원인 · 조치 권고가 담긴 AI 사고 보고서가 Reports에 표시, 보고서의 'Investigate in Chat'으로 채팅에 넘겨 심층 분석. 비용표(기본 설정 월 약 $370, AI 질의 1,500건). 응답 형식 문서: 에이전트가 TABLE_DATA · CHART_DATA 블록을 넣으면 정렬 · CSV 내보내기 표와 Chart.js 차트로 렌더.
- AI 해석을 지표 · 근거에 묶는 방식: 임계값 초과 → AI 보고서(심각도 · 근본 원인 · 조치)로 지표와 판단을 묶음. 채팅 답에는 출처 인용, 에이전트 활동 피드로 어느 데이터 계층을 썼는지 공개.
- 참고할 점:
  - Monitor의 '임계 초과 → AI 사고 보고서(심각도 · 근본 원인 · 조치 권고)' → C02 이슈 후보마다 AI 판단 초안(수준 · 이유 · 다음 행동) 카드
  - 'Investigate in Chat' 버튼 → C02 이슈 카드에서 C03 · C04 근거 · 정독 요약으로 넘기는 버튼
  - 에이전트 활동 피드(하위 에이전트 · 데이터 계층 · 추론 단계) + README 비용표 → C11 방법 · 비용 공개

### 3. Reddit Sentiment Analyzer — saagpatel (오픈소스, MIT)

- URL: <https://github.com/saagpatel/RedditSentimentAnalyzer> · 열어 본 문서: <https://raw.githubusercontent.com/saagpatel/RedditSentimentAnalyzer/main/README.md> (GitHub README)
- 열람 여부: **열람** · 접근 조건: 오픈소스 · 종류: 게임 커뮤니티 분석
- 맞는 구성요소: C08 감성 추이, C02 이슈 후보와 AI 판단, C06 급상승 키워드, C03 이슈 근거
- 무엇이 왜 맞나: README 기준: React 대시보드(시계열 차트, 여러 서브레딧 비교, 워드클라우드, 급변 상세 패널), 6시간 감성 버킷을 12시간 · 1일로 합산, 급변 탐지(직전 버킷 대비 compound 점수 변화가 임계값 이상), 15분 주기 수집
- AI 해석을 지표 · 근거에 묶는 방식: 점수는 VADER 규칙 기반. 애매한 글만 Claude로 넘겨 이유와 함께 재분류하는 선택 기능(기본 꺼짐)
- 참고할 점:
  - Reddit Sentiment Analyzer의 '급변 버킷 + 급변 상세 패널' → C02 이슈 후보를 누르면 그 주 감성 변화와 해당 글 목록이 열리는 상세 패널
  - '여러 서브레딧 비교' 화면 → C03 다른 커뮤니티의 같은 지표(인벤 · 아카라이브 · 공식 · 레딧 순감성 겹쳐 그리기)
  - '애매한 글만 LLM에 넘기고 이유 저장' → C11 비용 절감 방식(규칙/저가 모델 1차 + 애매한 것만 상위 모델) 검토

### 4. Analyze Topics by AI Assist + Spike Alerts — Sprout Social

- URL: <https://support.sproutsocial.com/hc/en-us/articles/20104813531533>
- 열람 여부: **검색 결과만** · 접근 조건: 확인 불가 · 종류: 소셜 리스닝
- 맞는 구성요소: C02 이슈 후보와 AI 판단, C03 이슈 근거, C04 AI 정독 요약, C09 VOC 주제 지도
- 무엇이 왜 맞나: Topics by AI Assist 위젯: 주제의 기간 · 필터 안 참여도 상위 메시지 최대 1,000건으로 대화 패턴 상위 3개와 요약, 요약마다 근거 메시지 최대 50건을 Message Explorer로 열기. 필터를 바꾸면 '오래됨' 배너와 Regenerate. Spike Alerts(사용자 임계값, 비 AI)는 언급량 · 노출 · 긍/부정 감성 증감을 이메일로.
- AI 해석을 지표 · 근거에 묶는 방식: AI 테마 요약마다 근거 원문(최대 50건) 링크, 요약 입력 범위(상위 1,000건)를 밝힘, 필터 변경 시 신선도 배너.
- 참고할 점:
  - Sprout 테마 요약 카드의 '근거 메시지 50개 펼치기' → C04 정독 요약의 하위 문제마다 원문 인용 펼치기
  - '필터 바뀌면 오래됨 배너 + Regenerate' → C04 · C01 요약 생성 시점과 현재 필터가 다르면 배너
  - Spike Alerts(언급량 · 긍/부정 감성 임계값) → C02 이슈 후보 기준(글 수 · 부정 비율)

### 5. Impact Analysis + AI data-point summaries (Lyra) — Chattermill

- URL: <https://chattermill.com/platform/impact-analysis>
- 열람 여부: **검색 결과만** · 접근 조건: 확인 불가 · 종류: VOC 분석
- 맞는 구성요소: C03 이슈 근거, C04 AI 정독 요약, C08 감성 추이, C09 VOC 주제 지도
- 무엇이 왜 맞나: Impact Analysis: 어떤 테마가 NPS(또는 순감성 · 평균 점수)를 올리고 내리는지. 아무 데이터 지점이나 누르면 무엇이 · 왜 일어나는지 AI 요약과 발견마다 뒤에 있는 원문 인용. Lyra = 측면 기반 감성 + LLM.
- AI 해석을 지표 · 근거에 묶는 방식: 차트 지점 → AI 요약(무엇 · 왜) → 근거 원문 인용. 지표(순감성) ↔ 주제 ↔ 원문이 한 흐름.
- 참고할 점:
  - Chattermill Impact Analysis의 '테마별 순감성 기여(올림/내림)' → C09 주제 지도에 주제별 순감성 기여 막대
  - '데이터 지점 클릭 → 무엇 · 왜 요약 + 원문 인용' → C04 정독 요약 패널을 C08 감성 추이의 해당 주 점에서 열기
  - 발견마다 원문 인용 → C03 대표 글

### 6. Steam user review histogram — Valve Steam

- URL: <https://www.engadget.com/2017-09-20-valve-steam-chart-graph-review-bombing.html>
- 열람 여부: **검색 결과만** · 접근 조건: 확인 불가 · 종류: 게임 커뮤니티 분석
- 맞는 구성요소: C03 이슈 근거, C05 운영 대응 전후 비교, C08 감성 추이, C10 주간 보고
- 무엇이 왜 맞나: Steam 상점 페이지 사용자 리뷰 히스토그램(2017.9~): 시간별 긍정(파랑) · 부정(빨강) 막대, 기간을 누르면 그 기간 리뷰 표본, 최근 30일 · 전체 점수 대비, 그래프 표시 토글. 리뷰 폭탄 같은 급등을 그 시점 사건과 맞춰 보게 하려고 도입.
- AI 해석을 지표 · 근거에 묶는 방식: 해당 없음(AI 기능 없음). 다만 지표 막대 → 그 기간 원문 표본으로 바로 이어지는 근거 연결.
- 참고할 점:
  - Steam 히스토그램의 '긍/부정 쌓은 막대 + 막대 클릭 시 그 기간 리뷰 표본' → C08 감성 추이 주별 막대를 누르면 C03 그 주 대표 글
  - '최근 30일 vs 전체' 두 점수 → C10 이번 주 vs 평시(8주) 비교 기준 표기
  - 급등을 사건과 맞춰 보는 용도 → C05 공지 · 업데이트 시점을 감성 막대 위에 표시

### 7. Iris AI / Signals (spike alerts + AI summaries) — Brandwatch

- URL: <https://www.brandwatch.com/wp-content/uploads/2025/11/AI-in-Brandwatch-1-Pager.pdf>
- 열람 여부: **검색 결과만** · 접근 조건: 확인 불가 · 종류: 소셜 리스닝
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C02 이슈 후보와 AI 판단, C04 AI 정독 요약, C06 급상승 키워드
- 무엇이 왜 맞나: Signals: 유의한 변화를 감지해 알림, 각 Signals 이메일은 감지된 변화의 AI 요약(테마 · 어조 · 가능한 원인)으로 시작. Iris가 대시보드 결과를 쉬운 말로 요약하고, 차트의 아무 데이터 지점이나 눌러 급등을 이끈 것을 AI 요약.
- AI 해석을 지표 · 근거에 묶는 방식: 급등 신호 → 테마 · 어조 · 원인 요약으로 묶고, 차트 데이터 지점 클릭 → 그 지점 설명. 대시보드 탭 요약도 있음.
- 참고할 점:
  - Brandwatch Signals 이메일의 '변화 + 테마 · 어조 · 가능 원인' 3칸 → C02 이슈 후보 AI 판단 초안(무엇이 · 어떤 분위기 · 이유)
  - Iris '차트 데이터 지점 클릭 → 그 지점의 급등 요인 요약' → C07 · C08 차트에서 튄 주를 누르면 C04 정독 요약
  - 대시보드 요약 → C01 이번 주 결론

### 8. Mira AI in Analyze dashboards (Add AI Insight, Spike Summary) — Meltwater

- URL: <https://community.meltwater.com/new-to-meltwater-125/5-easy-ways-to-impress-your-boss-this-week-11886>
- 열람 여부: **검색 결과만** · 접근 조건: 확인 불가 · 종류: 소셜 리스닝
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C02 이슈 후보와 AI 판단, C03 이슈 근거, C06 급상승 키워드
- 무엇이 왜 맞나: Analyze 대시보드의 Mira: 무엇이 뜨는지, 무엇이 급등을 이끌었는지, 채널 비교를 쉬운 말로 요약. 'Add AI Insight to the Dashboard'로 설명을 차트 옆에 고정. AI Spike Summary는 원인 · 핵심 테마 · 상위 콘텐츠.
- AI 해석을 지표 · 근거에 묶는 방식: AI 설명을 설명 대상 차트 바로 옆에 고정. 급등 요약에 상위 콘텐츠(근거 글)를 함께.
- 참고할 점:
  - Meltwater 'AI Insight를 차트 옆에 고정' → C01 이슈별 인사이트를 C07 · C08 차트 옆 카드로
  - AI Spike Summary의 '원인 · 핵심 테마 · 상위 콘텐츠' → C02 · C06 급상승 키워드마다 원인 한 줄 + 대표 글
  - '채널 비교' 요약 → C03 다른 커뮤니티의 같은 지표 비교 문장

### 9. FirstLook Player Sentiment

- URL: <https://docs.firstlook.gg/player/sentiment/>
- 열람 여부: **검색 결과만** · 접근 조건: 확인 불가 · 종류: 게임 커뮤니티 분석
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C06 급상승 키워드, C08 감성 추이, C09 VOC 주제 지도
- 무엇이 왜 맞나: Player Sentiment: Discord와 Steam 리뷰 · 토론을 모니터링해 감성 분류와 떠오르는 주제 발견. 개요에 뜨는 태그 · 주제, 기본 태그(Gameplay · Combat · Balance), 화제가 커지면 새 태그 자동 생성. Topics 페이지와 주별 감성 변화 · 뜨는 주제 · 참여를 보는 Weekly Summaries.
- AI 해석을 지표 · 근거에 묶는 방식: AI가 태그를 자동 생성하고 주별 요약을 씀. 요약 ↔ 원문 연결은 이 문서 근거로는 확인 불가(같은 회사 Agent는 인용 제공).
- 참고할 점:
  - FirstLook 개요의 '뜨는 태그 + 새 태그 자동 생성' → C06 급상승 키워드와 '새로 생긴 주제' 배지
  - Weekly Summaries(감성 변화 · 뜨는 주제 · 참여) → C01 이번 주 결론 + C10 주간 보고 구성
  - 기본 태그 Gameplay · Combat · Balance → C09 게임 VOC 주제 분류 체계 초안

### 10. FirstLook Agent

- URL: <https://firstlook.gg/agent/>
- 열람 여부: **검색 결과만** · 접근 조건: 확인 불가 · 종류: 게임 커뮤니티 분석
- 맞는 구성요소: C03 이슈 근거, C04 AI 정독 요약, C08 감성 추이
- 무엇이 왜 맞나: FirstLook Agent: 사용자가 입력한 주제에 대해 요약, 감성 점수, 그 뒤의 플레이어 원문 인용을 돌려줌. FirstLook Labs 안에서 무료로 표기(로그인 조건은 확인 불가).
- AI 해석을 지표 · 근거에 묶는 방식: 주제 요약 = 요약 + 감성 점수 + 근거 원문 인용 세트.
- 참고할 점:
  - FirstLook Agent의 '요약 + 감성 점수 + 원문 인용' 3단 카드 → C04 정독 요약의 하위 문제마다 감성 점수와 인용 2~3개
  - 원문 인용 → C03 대표 글

### 11. AI Anomaly Detector (멘션 탭 이상 급증 표시) — Brand24

- URL: <https://help.brand24.com/en/articles/8822129-ai-anomaly-detector>
- 열람 여부: **검색 결과만** · 접근 조건: 유료 · 종류: 소셜 리스닝
- 맞는 구성요소: C02 이슈 후보와 AI 판단, C07 글 수 지수(평시 = 100), C08 감성 추이, C03 이슈 근거
- 무엇이 왜 맞나: 멘션 탭의 언급량 · 도달 차트 위에 AI가 찾은 비정상 급증 지점을 느낌표 아이콘으로 표시하고, 아이콘을 누르면 급증에 대한 인사이트가 열린다. 같은 탭에 시간에 따른 감성(긍정 · 중립 · 부정) 차트가 있다.
- AI 해석을 지표 · 근거에 묶는 방식: AI가 언급량 · 도달의 급증을 감지해 차트의 해당 시점에 느낌표로 고정하고, 그 아래에 급증 인사이트를 붙인다. 급증을 실시간 사건과 연결한다고 설명한다(검색 결과 문장 기준). 인사이트에 원문 링크가 붙는지는 확인 불가.
- 참고할 점:
  - 멘션 차트 위 느낌표(이상 지점) → C07 글 수 지수 차트에서 평시 대비 이상 주간에 표식을 찍고, 누르면 C02 이슈 후보 카드(AI 판단 초안)가 열리게
  - '급증을 실시간 사건과 연결' → C03 이슈 근거에 같은 주 운영 공지 · 업데이트를 자동으로 붙여 급증 원인 후보로 보여 주기

### 12. AI Anomaly Detection Alerts · SIA(Social Intelligence Advisor) — Mentionlytics

- URL: <https://intercom.help/mentionlytics/en/articles/11028840-anomaly-detection>
- 열람 여부: **검색 결과만** · 접근 조건: 유료 · 종류: AI 인사이트
- 맞는 구성요소: C02 이슈 후보와 AI 판단, C04 AI 정독 요약, C08 감성 추이, C07 글 수 지수(평시 = 100)
- 무엇이 왜 맞나: 브랜드의 '평소 한 주'를 학습해 언급량 급증 · 급감과 갑작스러운 감성 변화(특히 부정 급증)를 감지하는 이상 알림. 알림에 평소 대비 편차, 부정 감성, 그럴듯한 원인(예: Ryanair 지연 항공편)을 함께 적는다. 트래커 · 키워드 · 채널 · 부정 멘션만으로 범위를 좁히고, 수신자와 AI 요약 언어를 지정. 별도로 SIA가 게시 시간 · 해시태그 등 제안.
- AI 해석을 지표 · 근거에 묶는 방식: AI가 평시 패턴을 기준선으로 삼아 이탈을 감지하고, 알림 본문에 '편차(지표) + 부정 감성 + 원인 가설'을 한 묶음으로 쓴다(검색 결과의 Ryanair 예시). 원문 인용 첨부 여부는 확인 불가.
- 참고할 점:
  - '평소 한 주를 학습해 이탈 감지' → C02 이슈 후보 기준선(직전 8주 평균)과 같은 설계 — 알림 카드에 '평시 대비 몇 배'를 맨 앞에
  - 알림 = 편차 + 부정 감성 + 그럴듯한 원인(지연 항공편) → C02 AI 판단 초안을 '무엇이 · 얼마나 · 왜(가설)' 3줄 고정 형식으로
  - 부정 멘션만 · 채널별 범위 지정 → C02 이슈 후보를 커뮤니티별로 켜고 끄는 필터

### 13. Emplifi Listening — Spike Alerts · AI Query Highlights

- URL: <https://docs.emplifi.io/platform/latest/home/crisis-management-and-spike-alerts-in-listening>
- 열람 여부: **검색 결과만** · 접근 조건: 유료 · 종류: 소셜 리스닝
- 맞는 구성요소: C02 이슈 후보와 AI 판단, C06 급상승 키워드, C08 감성 추이, C05 운영 대응 전후 비교
- 무엇이 왜 맞나: 키워드 + 감성 필터를 조합한 Spike alert 규칙(설정 → Listening → Spike alerts), AI가 대화량 기준선을 잡고 일상 변동을 걸러 내는 스마트 감지, 각 급증 뒤의 핵심 주제와 감성 변화를 보여 주는 AI Query Highlights, 이메일 · 플랫폼 알림, 부정 감성 급증 시 예약 캠페인 일시 중지 · 케어팀 에스컬레이션.
- AI 해석을 지표 · 근거에 묶는 방식: AI가 기준선을 학습해 급증을 감지하고, 급증마다 '그 뒤의 핵심 주제 · 감성 변화'를 AI Query Highlights로 붙인다(벤더 설명). 급증 → 대응 행동(캠페인 중지 · 에스컬레이션)까지 연결.
- 참고할 점:
  - '기준선 + 일상 변동 걸러 내기' → C02 이슈 후보 기준(직전 8주 평균 대비)에 '평시 변동폭 이내면 후보 제외' 규칙
  - 급증마다 핵심 주제 · 감성 변화 하이라이트 → C02 후보 카드에 C06 급상승 키워드 상위 3개와 C08 순감성 변화를 같이
  - 부정 급증 → 캠페인 중지 · 케어팀 에스컬레이션 → C02 '다음 행동' 칸에 운영 대응 선택지(공지 · 소통 · 확인 요청)

### 14. Rill Explore 대시보드 (시간 비교 · 리더보드 · AI Chat) — Rill Data

- URL: <https://docs.rilldata.com/explore/ai-chat> · 열어 본 문서: <https://raw.githubusercontent.com/rilldata/rill/main/README.md> (GitHub README(+ 검색 결과의 Rill 문서 요약))
- 열람 여부: **열람** · 접근 조건: 오픈소스 · 종류: 오픈소스 대시보드 도구
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C02 이슈 후보와 AI 판단, C06 급상승 키워드, C07 글 수 지수(평시 = 100)
- 무엇이 왜 맞나: Explore 대시보드: 큰 숫자 · 리더보드 · 차원 표에 비교 기간 대비 변화량과 변화율 표시, 리더보드에서 여러 차원 값을 골라 추이 비교, 대시보드 안에서 여는 AI Chat, 임계값 알림 · 보고서(Alerts & Reports).
- AI 해석을 지표 · 근거에 묶는 방식: 검색 결과(Rill 문서): 대시보드에서 AI Chat을 열면 AI가 현재 metrics view, 적용된 필터, 선택한 기간, 켜진 비교 설정을 안다. 릴리스 노트에 AI 생성 차트의 비교 지원 언급. README: 자연어 Conversational BI, MCP 서버로 AI 에이전트를 시맨틱 레이어에 연결.
- 참고할 점:
  - Rill 리더보드의 '비교 기간 대비 변화 · 변화율' 열 → C06 급상승 키워드 표에서 키워드별 '평시 8주 평균 대비 배수'를 같은 방식으로 정렬 · 표시
  - Rill AI Chat이 현재 필터 · 기간 · 비교 설정을 그대로 넘겨받는 구조 → C02 이슈 후보 행에서 'AI에게 묻기'를 누르면 그 커뮤니티 · 지표 · 주차 · 평시 기준이 문맥으로 붙도록
  - Rill 큰 숫자(big number) + 비교 기간 변화율 → C07 글 수 지수 카드(평시 = 100)의 기준 표시

### 15. VaporLens (LLM 스팀 리뷰 분석 · 리뷰 통계)

- URL: <https://vaporlens.app/changelog/review-stats>
- 열람 여부: **검색 결과만** · 접근 조건: 무료 공개 · 종류: 리뷰 분석
- 맞는 구성요소: C04 AI 정독 요약, C08 감성 추이, C05 운영 대응 전후 비교, C11 AI 분류 정확도와 비용
- 무엇이 왜 맞나: 수천 건의 스팀 리뷰를 LLM으로 분석해 장점 · 단점 · 성능 인사이트 · 게임 비교를 보여 줌. 'Statistical Analysis' 블록에 월별 감성 추이 막대(패치 · DLC 뒤 변화 확인용) 추가.
- AI 해석을 지표 · 근거에 묶는 방식: LLM이 리뷰에서 장점 · 단점을 뽑아 요약하고, 같은 페이지에 월별 감성 추이 통계 블록을 함께 둔다. 요약과 원문 리뷰의 연결(인용 · 근거 링크) 방식은 확인 불가이며, 커뮤니티에서 '요약이 리뷰와 맞는지 어떻게 아느냐'는 지적이 있었다.
- 참고할 점:
  - VaporLens의 'LLM 장점 · 단점 요약 + 같은 화면의 월별 감성 막대' → C04 정독 요약 카드 아래에 그 이슈의 주별 순감성 미니 막대를 붙여 요약과 지표를 한눈에
  - VaporLens 리뷰 통계의 '패치 · DLC 뒤 변화를 보는 단순 막대' → C05 운영 대응 전후 비교에 공지 시점 표시선이 있는 주별 부정 비율 막대
  - Augmented Steam 사용자들의 '요약이 리뷰와 맞는지 어떻게 아나' 반발 → C04 하위 문제마다 원문 인용과 C11 표본 검증 결과를 반드시 함께 노출

### 16. Outlier (Outlier.ai) Daily Stories — Outlier AI

- URL: <https://technologyadvice.com/products/outlier-ai-reviews/>
- 열람 여부: **검색 결과만** · 접근 조건: 유료 · 종류: AI 인사이트
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C02 이슈 후보와 AI 판단, C03 이슈 근거, C04 AI 정독 요약
- 무엇이 왜 맞나: 매일 '예상 밖 변화'를 Story로 알림(이메일 · 큐레이션 피드 · Explore), Story마다 변화 · 관련 데이터 · 비즈니스 영향 · 가능한 원인, 매일 '물어야 할 질문 4~5개', Rank Stories(세그먼트 순위 변화), Data Quality Stories(누락 · 손상 데이터).
- AI 해석을 지표 · 근거에 묶는 방식: 검색 결과: 하나의 Story 안에 변화한 지표, 관련 데이터, 잠재 영향, 가능한 원인을 같이 묶어 제시하고 일일 이메일 미리보기에 원인 분석이 들어감.
- 참고할 점:
  - Outlier Story의 '변화 + 관련 데이터 + 영향 + 가능한 원인' 4칸 → C02 이슈 후보 카드 한 장에 지표 변화 · 다른 커뮤니티 같은 지표(C03) · 원인 가설(C04)을 같이
  - '매일 물어야 할 질문 4~5개'로 상한을 둔 큐레이션 → C01 이번 주 결론을 이슈 3~5개로 제한
  - Data Quality Stories → C11에 수집 누락 · 이상 데이터 알림을 이슈와 같은 형식으로

### 17. SurveySparrow Social Listening — 감성별 급증일 AI 요약

- URL: <https://support.surveysparrow.com/hc/en/articles/25993111325853-Social-Listening/>
- 열람 여부: **검색 결과만** · 접근 조건: 유료 · 종류: 소셜 리스닝
- 맞는 구성요소: C04 AI 정독 요약, C06 급상승 키워드, C08 감성 추이
- 무엇이 왜 맞나: 소셜 리스닝 대시보드에서 특정 날짜에 급증한 언급을 감성별로 골라 AI에게 요약을 요청.
- AI 해석을 지표 · 근거에 묶는 방식: 검색 결과: 감성 추이에서 언급이 튄 날짜 · 감성을 선택하면 그 언급 묶음을 AI가 요약(차트 점 → 해당 원문 묶음 → AI 요약).
- 참고할 점:
  - '급증한 날 × 감성'을 골라 AI 요약 → C08 감성 추이에서 부정 급증 주차를 누르면 그 주 부정 글 묶음의 C04 정독 요약이 열리게
  - 같은 방식을 C06 급상승 키워드에 적용: 키워드 클릭 → 그 키워드 글 묶음 AI 요약

### 18. Zoho CRM — Zia Dashboard Insights

- URL: <https://help.zoho.com/portal/en/kb/crm-v2/analytics-and-dashboards/analytics-or-dashboards/overview/articles/crm-v2-zia-dashboard-insights>
- 열람 여부: **검색 결과만** · 접근 조건: 유료 · 종류: AI 인사이트
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C02 이슈 후보와 AI 판단, C03 이슈 근거
- 무엇이 왜 맞나: 대시보드 컴포넌트 옆 Zia 아이콘 → 그 컴포넌트 데이터를 분석해 패턴 · 주목할 변화를 전용 패널에 표시, Text View(짧은 평이한 발견) + Chart View(뒷받침 시각), 인사이트가 없으면 아이콘 회색 처리.
- AI 해석을 지표 · 근거에 묶는 방식: 검색 결과(Zoho 도움말): 컴포넌트 단위로 AI 분석을 호출하고, 같은 패널 안에 설명(Text View)과 근거 차트(Chart View)를 나란히 둠. 인사이트가 없으면 진입점을 비활성화.
- 참고할 점:
  - Zia 패널의 'Text View + Chart View' 쌍 → C02 이슈 후보마다 AI 판단 문장과 그 근거 차트(평시 대비 막대)를 한 패널에
  - '인사이트 없으면 아이콘 회색' → C04 정독 요약 대상이 아닌 지표는 AI 버튼을 비활성 처리해 과잉 해석 방지
  - 컴포넌트별 진입점 → C07 · C08 · C09 각 차트 모서리에 'AI 해석' 아이콘

### 19. Strategy (MicroStrategy) Auto Narratives · Auto Summary · Insights — Strategy (구 MicroStrategy)

- URL: <https://www.strategysoftware.com/strategyone/whats-new/auto-narratives-ai-powered-dashboard-summaries>
- 열람 여부: **검색 결과만** · 접근 조건: 유료 · 종류: AI 인사이트
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C02 이슈 후보와 AI 판단, C10 주간 보고
- 무엇이 왜 맞나: Auto Narratives(작성자가 조정, 필터 · 선택 변경에 맞춰 요약 갱신, 사용자 언어 적응), 대시보드 툴바 Auto Summary 버튼(페이지 전체 요약, 요약 지시문 편집, 자동 새로고침 끄면 수동 Refresh), Insights(KPI를 한곳에 모아 추세 · 이상치를 감시하고 알림), Auto Answers(대시보드 데이터 범위 안에서만 답).
- AI 해석을 지표 · 근거에 묶는 방식: 검색 결과: 요약에 상위 항목 · 총합 · KPI 비교 같은 지표가 들어가고, 필터 변경에 맞춰 다시 생성되며, 답변은 대시보드 뒤 데이터셋 범위로 제한.
- 참고할 점:
  - Auto Summary의 '편집 가능한 요약 지시문 + 자동 갱신 on/off + Refresh' → C01 결론 생성 프롬프트를 운영자가 고치고, 데이터 갱신 시 재생성 여부를 고르게
  - Insights의 'KPI 모아 두고 추세 · 이상치 감시 → 알림' → C02 이슈 후보 목록의 자동 탐지
  - '답변을 대시보드 데이터 범위로 제한' → C04 정독 요약이 수집한 6건 밖 내용을 말하지 않도록 범위 고정

### 20. 조이시티 AI 기반 VOC 시스템 (일별 요약 · 5단계 감정 점수) — 조이시티 (브런치 글 소개)

- URL: <https://brunch.co.kr/@@hYwI/22>
- 열람 여부: **검색 결과만** · 접근 조건: 확인 불가 · 종류: VOC 분석
- 맞는 구성요소: C01 이번 주 결론(AI 해석), C08 감성 추이, C10 주간 보고, C02 이슈 후보와 AI 판단
- 무엇이 왜 맞나: 라이브 운영팀 · 데이터팀이 만든 VOC 시스템: 생성형 AI로 갱신된 VOC의 일별 요약, 자체 학습 LLM의 5단계 감정 점수 시각화, AI 생성 트렌드 리포트로 내부 공유. 화면 자체는 확인 불가(2차 자료).
- AI 해석을 지표 · 근거에 묶는 방식: 생성형 AI가 VOC 데이터를 매일 요약하고, LLM 감정 점수(5단계)를 시각화해 라이브 운영 · 서비스팀이 수작업 분류 없이 시급한 이슈에 집중하게 했다고 함. 요약과 원문 · 지표의 연결 방식은 확인 불가.
- 참고할 점:
  - 조이시티의 '일별 AI 요약 + 5단계 감정 점수 시각화' → C01 이번 주 결론과 C08 감성 추이를 같은 데이터에서 뽑고, 감성을 3단계가 아닌 5단계(매우 부정~매우 긍정)로 나눌지 검토
  - 조이시티의 'AI 트렌드 리포트로 내부 공유 가속' → C10 주간 보고를 AI 초안 + 숫자 표로 만들어 복사 · 인쇄
  - 조이시티의 '수작업 분류 없이 시급한 이슈에 집중' 목표 → C02 이슈 후보 목록을 시급도 순으로 정렬

## 나머지 후보 전체

등급 순서(강력 추천 → 참고 → 부분 참고). 상위 20곳은 위에 있어 빼고 적었다.

### 참고 (116곳)

| ID | 이름 | 종류 | 구성요소 | 참고할 점 | 열람 | 접근 |
|---|---|---|---|---|---|---|
| S002 | [Power BI Narrative visual with Copilot](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-create-narrative) | AI 인사이트 | C01 C11 | Copilot 내러티브의 '보고서에 저장된 프롬프트 + 요약 범위 선택' → C11 방법 공개에 주간 결론을 만든 프롬프트와 입력 범위(어느 지표 · 커뮤니티)를 함께 공개 / Auto refresh 토글 → C01 결론이 어느 데이터 시점 기준인지 표시하고 데이터 갱신 때만 다시 생성 | 검색 결과만 | 확인 불가 |
| S005 | [Tableau Pulse insight summary & digest](https://help.tableau.com/current/online/en-us/pulse_explore_metrics.htm) | AI 인사이트 | C01 C02 C10 | Pulse 다이제스트의 '상위 인사이트 글 + 지표 상세로 가는 링크' → C10 주간 보고의 각 문장에 해당 이슈 카드(C02)로 가는 링크 / Pulse의 '인사이트 유용성 순위'와 '지표 음소거' → C02 이슈 후보 정렬 기준과, 상시 노이즈 지표(예: 특정 게시판)를 요약에서 빼되 표에는 남기기 | 검색 결과만 | 확인 불가 |
| S008 | [Looker Studio Gemini chart summaries (Slides export)](https://docs.cloud.google.com/looker/docs/studio/add-looker-studio-slides-gemini) | AI 인사이트 | C01 C10 | Gemini Slides 내보내기의 '차트 + 그 차트만의 요약 문장' → C10 주간 보고 복사본에서 차트마다 한두 문장 캡션 / '4행 미만이면 요약 안 함' → C04 신뢰도: 정독 표본이 부족한 커뮤니티는 AI 요약 대신 '표본 부족' 표시 | 검색 결과만 | 유료 |
| S011 | [Amazon Q in QuickSight - Executive summaries & Data stories](https://community.aws/content/2bdXbPBGkcEYF9IvK6kN87pjY8G/amazon-q-in-amazon-quicksight--generative-bi-capabilities-for-dashboard-authoring-executive-summary-data-stories) | AI 인사이트 | C01 C10 | QuickSight Executive summary의 '문장 클릭 → 그 문장이 나온 비주얼 강조' → C01 이번 주 결론의 각 인사이트 문장을 누르면 C07 · C08의 해당 차트 구간으로 이동 / Data stories 이메일 공유 → C10 주간 보고를 문장 + 차트 묶음으로 복사 · 발송 | 검색 결과만 | 확인 불가 |
| S014 | [ThoughtSpot Liveboard AI Highlights](https://docs.thoughtspot.com/cloud/latest/liveboard-ai-highlights) | AI 인사이트 | C01 C02 | AI Highlights의 '예상/예상 밖 변화 라벨' → C02 이슈 후보마다 평시 범위 안/밖 라벨을 달아 AI 판단 초안의 '수준' 근거로 / '변화 기여 속성' 목록 → C02 이유 칸에 어느 게시판 · 주제가 변화를 끌었는지 | 검색 결과만 | 확인 불가 |
| S021 | [Domo AI summary card](https://domo-webflow.domo.com/blog/build-ai-summary-card-dashboard) | AI 인사이트 | C01 C02 | Domo AI 요약 카드의 '중요 지표 표시 + 다음 할 일 추천' → C02 AI 판단 초안의 '다음 행동' 칸 / '데이터 갱신 때만 재생성' 원칙 → C01 · C11 주 1회 생성본을 고정하고 생성 시각 · 모델을 표시 | 검색 결과만 | 확인 불가 |
| S024 | [Amplitude Dashboard Agent](https://amplitude.com/docs/amplitude-ai/dashboard-agent) | AI 인사이트 | C01 C02 | Dashboard Agent의 '차트별 WoW 변화 발견 + 원인 세그먼트' → C02 이슈 후보 행마다 평시 대비 변화와 이를 끈 게시판 · 주제 | 검색 결과만 | 확인 불가 |
| S025 | [Amplitude Root Cause Analysis + Anomaly & Forecast](https://amplitude.com/docs/en/analytics/root-cause-analysis) | AI 인사이트 | C02 C04 | Amplitude Microscope의 '휴일에 걸린 이상은 경고' → C02 AI 판단 초안에 업데이트 · 점검 · 이벤트 주차 경고를 붙여 오탐 줄이기 / 차트 점 → RCA 목록 → C04 원인 가설을 차트 점에서 바로 열기 | 검색 결과만 | 확인 불가 |
| S028 | [Yellowfin Signals + Assisted Insights + Stories](https://www.yellowfinbi.com/blog/industrys-first-automated-analysis-and-cross-vendor-storytelling) | AI 인사이트 | C02 C04 | Yellowfin 신호 상세의 '성격 · 크기 · 기간' 3요소 서술 → C02 이슈 후보 한 줄 형식(무엇이 · 몇 배 · 언제) / Analysis 탭의 원인 후보 → C04 원인 가설 칸 | 검색 결과만 | 확인 불가 |
| S029 | [Arria Intelligent Narratives for BI (Power BI / Tableau add-in)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/wa200002323) | AI 인사이트 | C01 C02 | Arria의 '요약 ↔ 무엇 · 왜 · 다음' 길이 선택 → C01 한 줄 결론과 이슈별 인사이트(왜 · 다음 행동)를 같은 카드의 접기/펼치기로 | 검색 결과만 | 확인 불가 |
| S031 | [Datadog Watchdog stories](https://datadoghq.com/blog/watchdog) | AI 인사이트 | C02 C03 | Watchdog 스토리 카드의 '시계열에 해당 구간 강조 + 요약' → C02 이슈 후보 카드에 13주 미니 차트와 이번 주 구간 강조 / '관련 이상을 한 스토리로 합침 + 같은 시각 급등 대시보드 링크' → C03 다른 커뮤니티의 같은 지표 급등을 한 이슈로 묶어 보여주기 | 검색 결과만 | 확인 불가 |
| S032 | [Datadog dashboard anomaly investigation (Graph Insights)](https://docs.datadoghq.com/dashboards/graph_insights/investigate_anomalies/) | AI 인사이트 | C02 C03 | Graph Insights의 '동시에 발생한 이상을 하나의 이슈로 묶기' → C02 같은 주 여러 지표(글 수 · 부정 비율 · 키워드)가 함께 튄 경우 이슈 하나로 통합 / '기여 태그' → C03 · C06 이슈를 끈 키워드 · 게시판 태그 칩 | 검색 결과만 | 확인 불가 |
| S033 | [Status pages (component status + 90-day uptime bars)](https://www.checklyhq.com/communicate/status-pages/overview) | 공개 대시보드 | C05 C07 | 상태 페이지의 '구성요소 행 + 90일 일별 등급 막대' → C07 커뮤니티 행마다 13주 주별 등급 막대(평시 대비 수준 색) / '사고 타임라인 + 계획된 점검' → C05 공지(문제 안내 · 제재 · 변경 예고)를 같은 막대 아래 시간순으로 | 검색 결과만 | 확인 불가 |
| S035 | [Databox AI-powered Performance Summaries](https://help.databox.com/overview-using-ai-powered-performance-summaries-on-performance-screen) | AI 인사이트 | C01 C10 | Databox의 '상단 접힌 AI 요약 + 펼치기' → C01 결론을 한 줄로 접어 두고 펼치면 이슈별 인사이트 / 이메일 · Slack 스냅샷 → C10 주간 보고 발송본 | 검색 결과만 | 확인 불가 |
| S039 | [ServiceNow Dashboard Summarization (citations per highlight)](https://www.servicenow.com/docs/r/J7UfGStUvhlVOcoqiM3zlQ/mauybB1QJ_ZrM86hDhiG6Q) | AI 인사이트 | C01 C03 | ServiceNow 요약의 '하이라이트별 인용 칩 → 근거 위젯 강조' → C01 인사이트 문장마다 [C08 감성] [대표 글 3] 같은 근거 칩, 누르면 C03 근거 패널 열기 | 검색 결과만 | 확인 불가 |
| S046 | [Text iQ in CX Dashboards (table / bubble chart widgets)](https://www.qualtrics.com/support/vocalize/dashboard-settings-cx/text-analysis-cx/) | VOC 분석 | C08 C09 | Text iQ 표 위젯의 '주제 계층 드릴다운' → C09 VOC 주제 지도에서 상위 주제 → 하위 주제로 펼치며 부정 비율 / 주제별 감성 버블 차트 → C09 주제 × 감성 분포를 크기(글 수)와 색(부정 비율)으로 | 검색 결과만 | 확인 불가 |
| S047 | [Comment Summaries widget (EX)](https://qualtrics.com/support/employee-experience/creating-ee-project/dashboards-tab/widgets-ee/analysis-widgets-ee/comment-summaries-widget-ex) | VOC 분석 | C04 C09 | Comment Summaries의 'AI 요약 + 상위 5개 주제 차트 한 위젯' → C04 정독 요약 옆에 그 6건이 속한 주제 분포 막대를 함께 / '정확성 검토 권고' 문구 → C04 하단 검토 안내 | 검색 결과만 | 확인 불가 |
| S049 | [Generative AI reporting: GenAI Themes, Intelligent Summaries, Root Cause Assist](https://docs.medallia.com/medallia-experience-cloud/analysis/generative-ai-reporting) | VOC 분석 | C04 C09 | Intelligent Summaries의 '테마를 고르면 그 부분집합만 요약' → C09 주제 지도에서 주제를 누르면 그 주제 글만의 AI 요약(C04) 패널 / Root Cause Assist → C04 원인 가설을 주제 · 지표 단위로 | 검색 결과만 | 확인 불가 |
| S051 | [Smart Insights / Intuition Smart Alerts](https://www.sprinklr.com/products/consumer-intelligence/smart-insights/) | 소셜 리스닝 | C02 C08 | Sprinklr Smart Alerts의 '감성 · 언급량에 과거 기반 동적 임계값' → C02 평시 8주 기준 이상 판정을 감성(C08)과 글 수(C07) 둘 다에 | 검색 결과만 | 확인 불가 |
| S054 | [Blue Silk GPT / AI summaries & peak detection](https://talkwalker.com/products/bluesilkgpt) | 소셜 리스닝 | C02 C06 | Talkwalker '급등 원인 요약' → C06 급상승 키워드 행마다 '왜 올랐나' 한 줄과 대표 글 | 검색 결과만 | 확인 불가 |
| S058 | [Business Impact Analysis (impact view / NPS waterfall)](https://getthematic.com/insights/cx-dashboards-that-earn-executive-trust) | VOC 분석 | C03 C09 | Thematic NPS 폭포 → C09 순감성 지수가 평시에서 이번 주로 움직인 것을 주제별 기여로 분해한 폭포 차트 / 'Impact vs Volume' 토글 → C09 주제 정렬을 글 수 순 / 감성 영향 순으로 전환 | 검색 결과만 | 확인 불가 |
| S059 | [Anomaly alerts + Wisdom (dashboards)](https://helpcenter.enterpret.com/en/articles/6446366-anomaly) | VOC 분석 | C02 C09 C11 | Enterpret 'z-score 1.5 기본 + 민감도 조절' → C02 평시 대비 이상 기준을 숫자로 공개하고 조절 가능하게 / '인라인 재분류' → C11 분류 정확도 표본에 사람 교정 건수를 반영 | 검색 결과만 | 확인 불가 |
| S062 | [Siena Insights (formerly Idiomatic)](https://siena.cx/insights/customer-feedback-analytics-software) | VOC 분석 | C02 C09 | Siena '일 평균 대비 급증 Slack 알림 + 예시 카테고리' → C02 이슈 후보 문장('○○ 주제 글이 평시 대비 3배') / 카테고리별 비중 → C09 주제 비중 | 검색 결과만 | 확인 불가 |
| S063 | [Intelligent triage dashboard (analyst copilot)](https://support.zendesk.com/hc/en-us/articles/10782829928986-Understanding-the-intelligent-triage-dashboard-in-analyst-copilot-EAP) | VOC 분석 | C08 C09 C11 | Zendesk 'enriched(분류된) 티켓 수' KPI → C11 분류 커버리지(전체 글 중 AI 분류 완료 비율)를 카드로 / 탭 구성 Overview → Intent → Sentiment → C09(주제 · 의견 유형) / C08(감성)을 같은 순서의 탭으로 | 검색 결과만 | 확인 불가 |
| S064 | [Fin Insights (Topics Explorer, Optimize dashboard)](https://fin.ai/insights) | VOC 분석 | C02 C09 | Fin Topics → Subtopics 탐색기 → C09 주제 → 하위 주제 행마다 부정 비율 · 글 수 / Optimize 제안 목록 → C02 AI 판단 초안의 '다음 행동'을 목록화 | 검색 결과만 | 확인 불가 |
| S066 | [AI Dashboards / Channels](https://www.dovetail.com/product/ai-dashboards) | VOC 분석 | C06 C09 | Dovetail Channels의 '새 테마 주기 감지' → C06 급상승 키워드와 별도로 '새로 생긴 주제' 표시 / 테마 분리 · 병합 · 이름 바꾸기 → C09 키워드 그룹을 운영자가 편집 | 검색 결과만 | 확인 불가 |
| S068 | [AppFollow AI review analytics](https://appfollow.io/ai-info) | 리뷰 분석 | C08 C09 C10 | AppFollow '기능(feature)별 감성 추세' → C09 주제별 부정 비율 13주 추이 / 예약 이메일 보고 → C10 주간 보고 발송 | 검색 결과만 | 확인 불가 |
| S069 | [Appbot dashboards (sentiment, topics, Ask Appbot)](https://appbot.co/features/) | 리뷰 분석 | C03 C08 C09 | Appbot 주제 표의 '감성 · 언급 수 · % · 행별 추세선' → C09 주제 지도 표의 열 구성(부정 비율 · 글 수 · 비중 · 13주 스파크라인) / 긴 기간 감성 추세 → C08 순감성 지수에 업데이트 시점 표시 | 검색 결과만 | 유료 |
| S070 | [AppTweak topic analysis](https://help.apptweak.com/en/articles/9428575-how-to-use-the-topics-analysis) | 리뷰 분석 | C09 C11 | AppTweak 주제 행의 'AI 정의 + 사용한 키워드' → C11 방법 공개 · C09 주제 지도에서 주제마다 정의와 판단 키워드 툴팁 / '최소 5회' 노출 조건 → C06 급상승 키워드 최소 등장 수 기준 명시 | 검색 결과만 | 확인 불가 |
| S071 | [Birdeye Insights AI](https://birdeye.com/insights/) | 리뷰 분석 | C02 C05 | Birdeye '우선순위 수정 목록 → 개선 추적' → C05 운영 대응 전후 비교에서 대응한 이슈의 다음 주 부정 비율 변화를 추적 / 우선순위 목록 → C02 이슈 후보 정렬 | 검색 결과만 | 확인 불가 |
| S076 | [Lens (AI social sentiment for community managers)](https://www.keywordsstudios.com/en/lens/) | 게임 커뮤니티 분석 | C06 C08 C10 | Lens의 '커뮤니티 포럼 포함 감성 변화 · 떠오르는 추세' → C08 · C06 게임 커뮤니티 기준 지표 구성의 직접 비교 대상(화면 세부는 별도 확인 필요) / 보고 시간 단축 사례 → C10 주간 보고 자동 작성 범위 설정 참고 | 검색 결과만 | 확인 불가 |
| S082 | [VOC 스튜디오](https://byline.network/2023/07/%ec%b1%84%eb%84%90%ed%86%a1-%eb%b3%b4%ec%9d%b4%ec%a0%80%ec%97%91%ec%8a%a4-ai-%ea%b3%a0%ea%b0%9d-%ec%83%81%eb%8b%b4-%eb%b6%84%ec%84%9d%ed%88%b4-voc-%ec%8a%a4%ed%8a%9c%eb%94%94%ec%98%a4%ec%b6%9c/) | VOC 분석 | C02 C04 C10 | VOC 스튜디오 '첫 화면에 추세 이탈 특이점' → C02 이슈 후보를 대시보드 첫 화면 최상단에 / '불만 · 이슈 · 칭찬' 3분류 → C09 의견 유형 분류 | 검색 결과만 | 확인 불가 |
| S083 | [오픈서베이 데이터스페이스 VOC 분석](https://blog.opensurvey.co.kr/research-tips/cx-action-guide-4/) | VOC 분석 | C04 C09 | 오픈서베이 '주제 → 분류 → 대표 VOC → 요약' 순서 → C04 정독 요약 화면을 하위 문제 → 대표 인용 → 요약 순으로 배치 / '사람 검토' 단계 → C02 AI 판단 초안에 검토 상태 표시 | 검색 결과만 | 확인 불가 |
| S092 | [SteamDB Charts](https://steamdb.com/charts) | 게임 시장 지표 | G C06 | SteamDB 게임별 과거 동시 접속 추세 → G 스팀 동시 접속 13주 차트(일 최고치 기준) / 'Trending(가장 큰 변화)' 목록 형식 → C06 급상승 키워드 표를 '변화 폭 순' 목록으로 | 검색 결과만 | 확인 불가 |
| S095 | [Live Events Tracker](https://gamerefinery.com/live-events-tracker) | 게임 라이브 운영 | C03 C05 | GameRefinery '캘린더에서 이벤트 클릭 → 옆 패널 상세' → C03 같은 주 운영 대응을 타임라인에서 눌러 공지 원문 요약 보기 / '이벤트의 매출 · 다운로드 영향' → C05 공지 · 업데이트 전후 부정 비율 · 글 수 변화 | 검색 결과만 | 확인 불가 |
| S096 | [Levellr Discord insights](https://tech.eu/2026/01/29/levellr-raises-2-5m-to-turn-discord-and-gaming-user-voice-data-into-brand-intelligence/) | 게임 커뮤니티 분석 | C08 C09 | Levellr Social Listening 대시보드의 '커뮤니티 대화 주제 군집 + 주제별 감성' → C09 주제 지도와 C08 감성을 같은 주제 축으로 | 검색 결과만 | 확인 불가 |
| S099 | [Affogata player feedback analytics](https://www.affogata.com/helpshift-users/) | 게임 커뮤니티 분석 | C02 C03 C08 | Affogata '여러 소스(Discord · Steam · Reddit · 포럼) 한데 + 급증 · 감성 변화 알림' → C03 같은 지표를 다른 커뮤니티와 나란히, C02 감성 변화도 이슈 후보 신호로 | 검색 결과만 | 확인 불가 |
| S114 | [Nexon Stats (넥슨스탯)](https://www.invenglobal.com/articles/24544/nexon-introduces-internal-data-analysis-tool-nexon-stats-from-reactive-to-proactive) | 게임 라이브 운영 | C03 C05 | 넥슨스탯 '운영 이슈 + 지표 한 타임라인' → C05 공지와 부정 비율 · 글 수를 같은 시간 축에 겹치기 / User Voice(공지 · 커뮤니티 반응 수집) → C03 같은 주 운영 대응과 커뮤니티 반응을 한 근거 패널에 | 검색 결과만 | 확인 불가 |
| S121 | [Neo Theme Analysis dashboards](https://clootrack.com/solutions/customer-experience/ai-customer-feedback-analytics-voc-solutions) | VOC 분석 | C09 C08 C04 | Clootrack 테마 대시보드의 '인사이트 → 원문 코멘트 연결' → C09 주제 지도에서 주제 셀을 누르면 해당 글 목록(C03 대표 글)으로 바로 이동 / Clootrack의 다단계 동인 드릴다운 → C09 주제 → 하위 주제 → 키워드 그룹 3단 드릴다운 | 검색 결과만 | 유료 |
| S122 | [High-impact themes (Dashboard Impact sort / Quadrant chart)](https://help.kapiche.com/en/articles/6509843-how-to-find-high-impact-themes-using-your-dashboard) | VOC 분석 | C09 C08 | Kapiche Quadrant Chart의 '전체 평균선 + 테마별 위치' → C09 주제 지도에서 x=글 수 지수, y=부정 비율로 놓고 평시 평균선을 그어 '많고 부정적인 주제'를 사분면으로 표시 / Kapiche Display 드롭다운(빈도/감성/영향 정렬 전환) → C09 주제 표의 정렬 기준 전환 토글 | 검색 결과만 | 유료 |
| S125 | [Zonka AI Feedback Intelligence](https://www.zonkafeedback.com/blog/launching-zonka-ai-feedback-intelligence) | VOC 분석 | C09 C08 C02 | Zonka의 '긴급도(urgency)' 태그 → C02 이슈 후보의 AI 판단 수준(관찰/주의/대응)을 글 단위 긴급도 비율로 보강 / Zonka의 테마 · 하위 테마 2단 태깅 → C09 주제 지도의 주제/하위 주제 구조 | 검색 결과만 | 확인 불가 |
| S127 | [Viable 주간 자연어 피드백 리포트](https://venturebeat.com/ai/viable-is-quantifying-qualitative-customer-feedback-with-ai) | AI 인사이트 | C01 C04 C10 | Viable 주간 리포트의 '테마별 요약 + 긴급도 순위 + 추천 + 고객 인용' → C01 이번 주 결론의 이슈별 인사이트 카드(요약 · 수준 · 다음 행동 · 인용 2개) / Viable의 '상위 불만 · 칭찬 · 질문 · 요청' 4칸 주간 메일 → C10 주간 보고의 의견 유형별 상위 항목 블록 | 검색 결과만 | 유료 |
| S128 | [Monterey AI Weekly Report + Slack 알림](https://docs.monterey.ai/weekly-report) | AI 인사이트 | C10 C01 | Monterey의 '알림 단위 선택(개별 / 주간 요약 / 테마)'과 '피드백이 많으면 알림이 시끄럽다'는 경고 → C10 주간 보고 발송을 '주간 요약'만 기본으로 두고 개별 글 알림은 끄기 / Monterey 주간 리포트의 대화형 요약 → C01 결론 카드에서 이슈를 누르면 C02로 내려가는 구조 | 검색 결과만 | 유료 |
| S130 | [Keatext 대시보드 (칭찬 · 문제 · 질문 · 제안 분류, 토픽 × 의견 히트맵)](https://www.keatext.ai/wp-content/uploads/2021/09/Keatext-User-Guide.pdf) | VOC 분석 | C09 C10 | Keatext의 '토픽 × 의견(칭찬/문제/질문/제안) 히트맵' → C09 주제 × 의견 유형 표를 같은 히트맵으로 구성(칸 = 글 수, 색 = 평시 대비 배수) / Keatext의 '필터를 담은 대시보드 링크 공유' → C10 주간 보고에서 현재 필터 상태를 URL로 복사 | 검색 결과만 | 유료 |
| S132 | [Freddy AI Insights (Proactive insights)](https://support.freshdesk.com/support/solutions/articles/50000011660-proactive-insights-in-freshdesk) | AI 인사이트 | C02 C04 | Freddy의 '가장 많이 오른/내린 지표' 자동 목록 → C02 이슈 후보 목록을 평시 대비 변화 폭 순으로 정렬 / Freddy의 '티켓 급증 인사이트 → 원인 분해' → C02에서 이상 지표를 누르면 게시판 · 주제별 기여도 분해(C04 원인 가설 앞 단계) | 검색 결과만 | 유료 |
| S134 | [CXone Mpower Interaction Analytics workspace widgets](https://help.nicecxone.com/Content/interactionanalyticspro/dataanalysis/workspacewidgets.htm) | VOC 분석 | C09 C08 C06 | NiCE Topic AI의 '카테고리 → 주제 → 하위 주제' 3단 → C09 주제 지도의 계층 구조 / NiCE AutoDiscovery의 '모르는 주제 군집' → C06 급상승 키워드 옆에 '기존 분류에 없는 새 군집' 칸 | 검색 결과만 | 유료 |
| S136 | [Similarweb App Reviews 리포트](https://support.similarweb.com/hc/en-us/articles/28538732013725-App-Reviews) | 리뷰 분석 | C09 C03 | Similarweb의 '앱 간 비교를 위해 주제를 고정' → C03 다른 커뮤니티의 같은 지표 비교가 성립하도록 커뮤니티 공통 주제 분류를 고정 / Similarweb 주제 행의 '리뷰 수 · 평균 별점 · 감성 분포 · 답변율' 열 → C09 주제 표에 '공식 대응 여부' 열 추가 | 검색 결과만 | 유료 |
| S138 | [MobileAction Reviews (Review Analysis / Keyword Plot)](https://helpcenter.mobileaction.co/reviews) | 리뷰 분석 | C06 C08 | MobileAction Keyword Plot의 '세로 위치 = 감성, 크기 = 언급 빈도, 화살표 = 추세' → C06 급상승 키워드를 산점도로 그려 배수(x)와 부정 비율(y)을 같이 보여주기 | 검색 결과만 | 유료 |
| S140 | [ReviewTrackers Dashboard](https://support.reviewtrackers.com/hc/en-us/articles/360007938133-ReviewTrackers-Dashboard) | 리뷰 분석 | C06 C08 C03 | ReviewTrackers가 '워드 버블 → 긍정/부정 키워드 순위 목록'으로 바꾼 사례 → C06 급상승 키워드를 워드클라우드 대신 순위 목록(배수 · 대표 글)으로 / ReviewTrackers의 '지점별 점수 추이' → C03/C08 커뮤니티별 순감성 지수 나란히 비교 | 검색 결과만 | 유료 |
| S143 | [Revinate 감성 분석 · Corporate Dashboard](https://www.revinate.com/hotel-software/reputation-management/) | 리뷰 분석 | C09 C03 C08 | Revinate의 '주제 언급 드릴다운(무엇이 어떤 맥락에서 말해졌나)' → C09 주제 셀 클릭 시 해당 문장 단위 언급 목록 / Revinate Corporate Dashboard의 '여러 호텔 순위 · 감성 추세' → C03/C08 커뮤니티 4곳 순감성 순위와 추세를 한 장에 | 검색 결과만 | 유료 |
| S144 | [Trustpilot Review Spotlight / Review Insights](https://uk.business.trustpilot.com/blog/learn-from-customers/unlock-key-insights-with-your-new-spotlight-report) | 리뷰 분석 | C10 C01 C09 | Trustpilot Spotlight의 '주간 · 월간 간결 리포트' → C10 주간 보고를 결론 3줄 + 테마 3개 형식의 짧은 판으로 별도 제공 / Review Insights의 '주제별 감성 시간 추적' → C09 키워드 그룹 비중과 추이 | 검색 결과만 | 유료 |
| S145 | [Revuze Explorer (SWOT · Best/Worst · Topics)](https://revuze.it) | 리뷰 분석 | C09 C10 | Revuze의 'SWOT 대시보드' → C01 이번 주 결론을 강점(칭찬 증가) · 약점(불만 증가) · 기회(개선 요청) · 위협(이탈 언급)으로 정리하는 변형안 / Revuze의 'PowerPoint 내보내기' → C10 주간 보고의 복사 · 인쇄 외 슬라이드 내보내기 | 검색 결과만 | 유료 |
| S146 | [Pendo Listen feedback insights + Listen Explore](https://support.pendo.io/hc/en-us/articles/18906566175131) | AI 인사이트 | C01 C07 C09 | Pendo의 '항목 5개 이상일 때만 AI 요약 생성' → C04 정독 요약에 최소 표본 기준과 표본 수를 같이 표기(신뢰도) / Pendo의 'AI 요약 카드를 대시보드에 차트와 함께 추가' → C01 결론 카드와 C07 글 수 차트를 같은 필터로 묶기 | 검색 결과만 | 유료 |
| S149 | [Hotjar AI 설문 요약 리포트 · 감성 분석](https://www.cmswire.com/the-wire/hotjar-introduces-hotjar-ai-the-ai-powered-research-assistant-for-marketers-and-product-teams/) | AI 인사이트 | C04 C08 | Hotjar AI 리포트의 '발견 → 뒷받침 인용 → 추천 다음 행동' 3단 → C04 정독 요약의 하위 문제마다 인용 · 원인 가설 · 다음 행동을 같은 순서로 / Hotjar의 '부정 응답으로 바로 이동' → C08 감성 비율 막대를 누르면 부정 글 목록으로 | 검색 결과만 | 유료 |
| S150 | [BuildBetter Signals · Clustering insights](https://docs.buildbetter.ai/pages/Analytics/clustering-insights) | AI 인사이트 | C04 C09 C07 | BuildBetter 군집 리포트의 '추세 · 근본 원인 · 추천' → C04 정독 요약의 원인 가설과 다음 행동 칸 구성 / BuildBetter의 '군집은 최소 3개 신호부터' → C04 하위 문제는 인용 3건 이상일 때만 별도 항목으로 표시 | 검색 결과만 | 유료 |
| S152 | [채널톡 VOC 스튜디오 'VoC 리포트 구독하기'](https://docs.channel.io/voc-studio/ko/articles/ed2ea434-%EB%B8%8C%EA%BE%B8%EA%B8%B0-VoC-%EB%A6%AC%ED%8F%AC%ED%8A%B8-%EA%B5%AC%EB%8F%85%ED%95%98%EA%B8%B0) | VOC 분석 | C10 C04 | 채널톡 리포트의 '수집 기준(인입/종료 시간) 선택' → C10 주간 보고에 집계 기준(작성 시각 기준, 주 시작 요일)을 명시 / 채널톡 리포트의 'AI 추출 문제 상황 + 태그' → C04 하위 문제 목록을 주제 태그와 함께 주간 보고에 붙이기 | 검색 결과만 | 유료 |
| S155 | [싱클리 (국내 한국어 VOC 분석)](https://yozm.wishket.com/magazine/product-valley/products/syncly/) | VOC 분석 | C08 C09 C10 | 싱클리의 '한 VOC를 의미 단위로 쪼개 단위별 감정' → C09 주제별 부정 비율을 글 단위가 아니라 '글 속 주제 언급 단위'로 계산하는 방식 검토(제목 하나에 칭찬 + 불만 공존 대응) | 검색 결과만 | 확인 불가 |
| S164 | [Forum Scraper (Decodo Reddit-scraper)](https://github.com/Decodo/Reddit-scraper) | 게임 커뮤니티 분석 | C01 C04 C08 | Forum Scraper의 '요약 + 테마 + 대표 인용 + 상위 글 순위' 한 장 리포트 → C04 정독 요약 레이아웃(하위 문제 · 인용 · 추천 상위 글 비교) / '수집 계획(서브레딧 · 검색어)을 실행 전 검토' → C11 방법 공개에 커뮤니티 · 게시판 수집 범위를 명시 | 열람 | 오픈소스 |
| S165 | [Play Store Review Trend Analysis AI Agent (Pulsegen)](https://github.com/Keerthan410/Pulsegen) | 리뷰 분석 | C09 C07 C11 | Pulsegen의 '비슷한 표현을 한 주제로 통합(예: 배달원 불친절 3표현 → 1주제)' → C06 급상승 키워드를 표현 묶음(키워드 그룹) 단위로 계산 / Pulsegen의 평가 지표 '주제 중복률 · 통합 정확도' → C11 분류 정확도 패널에 주제 중복률 항목 추가 | 열람 | 오픈소스 |
| S167 | [Kura (대화 데이터 군집 분석, Clio 재현)](https://gittrend.io/repo/jxnl/kura) | 오픈소스 대시보드 도구 | C09 C04 | Kura의 '군집 → 메타 군집' 계층 → C09 주제 지도에서 AI가 이름 붙인 하위 군집을 상위 주제로 접고 펼치기 / Kura의 '수천 건 → 20개 패턴' 요약 → C01 결론에 '이번 주 새로 생긴 군집' 목록 | 열람 | 오픈소스 |
| S168 | [OpenClio](https://github.com/Phylliida/OpenClio) | 오픈소스 대시보드 도구 | C09 C03 | OpenClio의 '트리 상태를 URL 해시로 공유' → C03/C10 이슈 근거 화면의 현재 상태(커뮤니티 · 주제 · 글)를 링크로 복사 / OpenClio의 '패싯 정의(질문 + 군집 이름 기준)' → C11 방법 공개에 분류 축(감성 · 주제 · 의견 유형)별 질문 문장을 그대로 공개 | 열람 | 오픈소스 |
| S169 | [BERTopic (topics over time / per class / LLM representation)](https://github.com/MaartenGr/BERTopic) | 오픈소스 대시보드 도구 | C06 C09 C03 | BERTopic topics_per_class → C03/C09 같은 주제를 커뮤니티별(클래스 = 인벤 · 아카라이브 · 공식 · 레딧) 비중으로 비교 / BERTopic topics_over_time → C06 키워드 그룹(주제)별 주간 추이와 평시 대비 배수 계산의 기반 | 열람 | 오픈소스 |
| S172 | [AI Brand Assistant · Summarize with AI · AI Topic Analysis](https://help.brand24.com/en/articles/11461070-discover-the-value-of-ai-features) | AI 인사이트 | C01 C04 C09 C10 | 'Why did mentions increase last week?' 질의 → C01 이번 주 결론 아래 '왜 늘었나' 질문 버튼을 두고 답에 C07 · C08 차트를 같이 그려 주기 / Topic Analysis 탭의 주제 클러스터 + 무관 주제 차단 → C09 VOC 주제 지도에서 잡음 주제(거래 · 홍보 글) 제외 토글 | 검색 결과만 | 유료 |
| S173 | [Insights Copilot (대화형 인사이트) · Visual Insights](https://youscan.io/insight-platforms) | AI 인사이트 | C01 C04 C03 | Copilot 요약 + 실제 멘션 예시 연결 → C04 정독 요약의 하위 문제마다 원문 인용 2~3건을 붙이기 / 리뷰의 '예시가 요약에 맞지 않음 · 중복' 불만 → C04 신뢰도 표시에 '인용이 요약을 뒷받침하는지' 점검 항목 추가(중복 인용 제거, 커뮤니티 분산) | 검색 결과만 | 유료 |
| S174 | [Awario 대시보드 · Alert Comparison 리포트](https://awario.com/help/dashboard/dashboard-overview) | 소셜 리스닝 | C03 C07 C08 | '통계 뒤의 멘션을 바로 보기' → C07 · C08 차트의 막대 · 점을 누르면 그 주 · 그 커뮤니티 원문 목록이 열리는 드릴다운 / Alert Comparison(최대 15개 알림 비교) → C03 '다른 커뮤니티의 같은 지표'를 한 표로 나란히 | 검색 결과만 | 유료 |
| S178 | [Ipsos Synthesio — Topic Modeling · Signals GenAI · Listen/Discover 탭](https://www.ipsos.com/en/social-listening-tools-synthesio) | 소셜 리스닝 | C02 C09 C06 | Topic Modeling(상향식 주제 발견) → C09 주제 지도에 '사전 정의 주제' 외 '새로 발견된 주제' 칸을 따로 / Listen(원문 스트림)과 Discover(분석 모델) 탭 분리 → 대시보드를 '읽기(원문)'와 '분석(C02 · C09)' 영역으로 나누는 정보 구조 | 검색 결과만 | 유료 |
| S179 | [Radarly Discovery (AI Insight Assistant)](https://community.meltwater.com/product-updates/radarly-general-availability-of-discovery-and-video-analysis-927) | AI 인사이트 | C02 C04 | '감지하고 설명하고 노출' 3단계 → C02 이슈 후보 카드에 감지(지표) · 설명(AI 판단) · 노출(대표 글) 순서를 고정 | 검색 결과만 | 유료 |
| S180 | [Radarly 인사이트 페이지 AI 분석 카드 · 템플릿](https://help.meltwater.com/en/articles/10003275-radarly-ai-analysis-in-insight-pages) | AI 인사이트 | C03 C04 C08 | '부정 게시물' AI 카드 → C04 정독 요약 옆에 '부정 대표 글' 카드를 고정 배치 / '가장 참여 높은 게시물' 카드 → C04 '추천 상위 글 vs 일반 글' 비교의 추천 상위 쪽 묶음 | 검색 결과만 | 유료 |
| S189 | [GummySearch — 레딧 오디언스 리서치(Pain Points 등 테마)](https://gummysearch.com/product/) | 게임 커뮤니티 분석 | C09 C04 C03 | Pain Points / Solution Requests / Seeking Alternatives 필터 → C09 '주제 × 의견 유형'의 의견 유형 축(불만 · 개선 요청 · 이탈 언급) 설계 참고 / 테마를 빈도순으로 정렬 + 원글 읽기 안내 → C04 정독 요약의 하위 문제를 빈도순으로 나열하고 각각 원글 링크 | 검색 결과만 | 확인 불가 |
| S195 | [YouTube Comment Insights (Apify 액터)](https://apify.com/seemuapps/youtube-comment-insights?fpr=ewv9tm) | 리뷰 분석 | C08 C09 C06 | '요청 주제 · 질문 · 불만' 분해 → C09 의견 유형(개선 요청 · 질문 · 불만)을 게임 공식 유튜브 댓글에도 같은 분류로 적용 / 건당 비용 공개(1,000건당 80달러) → C11 비용 표에 '1,000건당 비용' 단위로 비교 | 검색 결과만 | 유료 |
| S197 | [Ground News Bias Bar · Blindspot 리포트](https://help.ground.news/en/articles/245249) | 공개 대시보드 | C03 C10 | 이벤트별 '누가 다뤘나' 분포 막대 + 출처 목록 → C03 이슈 근거에 '커뮤니티별 이 이슈 글 비중' 막대(인벤 · 아카라이브 · 공식 · 레딧)와 각 커뮤니티 대표 글 / 주간 Blindspot(한쪽만 크게 다룬 사건) → C10 주간 보고에 '한 커뮤니티에서만 커진 이슈' 섹션 | 검색 결과만 | 확인 불가 |
| S199 | [GDELT Summary · GKG Tone Timeline Visualizer](https://blog.gdeltproject.org/announcing-gdelt-summary/) | 공개 대시보드 | C07 C08 C10 | 볼륨 타임라인 + 평균 톤 타임라인 분리 → C07 글 수와 C08 순감성을 같은 시간축 두 줄 차트로 / 공유 URL · CSV/JSON · 임베드 HTML → C10 주간 보고의 차트마다 '데이터 받기 · 퍼가기' 버튼 | 검색 결과만 | 무료 공개 |
| S200 | [Media Cloud Search (Attention Over Time · Top Words)](https://www.mediacloud.org/media-cloud-search) | 오픈소스 대시보드 도구 | C07 C06 C03 | 추세 그래프 지점 클릭 → 그 기간 워드클라우드 → C07 글 수 지수의 주를 누르면 그 주 C06 급상승 키워드로 바뀌는 연동 / 그래프 구간 드래그 → 재검색 → C03 이슈 근거의 기간을 차트에서 바로 좁히기 | 열람 | 오픈소스 |
| S202 | [Determ (구 Mediatoolkit) — Synthia AI 요약 · Spike alerts](https://determ.com/?p=13645) | 소셜 리스닝 | C01 C02 C08 | '주제 요약 + 다음 단계' 원클릭 → C02 AI 판단 초안의 '다음 행동' 칸을 주제 요약과 한 카드로 / 급증 · 감성 변화 두 종류 Spike alert → C02 이슈 후보를 '글 수 이상'과 '감성 이상'으로 유형 구분 | 검색 결과만 | 유료 |
| S203 | [Agorapulse Inbox 감성 분석 리포트](https://support.agorapulse.com/en/articles/10148423-how-to-view-the-inbox-sentiment-analysis-report) | 소셜 리스닝 | C08 C11 | 'Undefined'(너무 짧아 분류 불가) 범주를 지표에 따로 → C08 감성 비율에 '판단 불가' 칸을 숨기지 않고 표시, C11에 그 비율 공개 / 감성 점수 + 일별 감성 2단 리포트 → C08 상단 순감성 지수, 하단 일별 감성 비율 막대 | 검색 결과만 | 유료 |
| S204 | [YouGov Ratings · BrandIndex Buzz 순위](https://yougov.com/en-us/business/products/brandrankings) | 공개 대시보드 | C08 C03 C10 | Buzz = 긍정 - 부정(-100~100) → C08 순감성 지수의 정의 · 범위 표기를 같은 방식으로 명시 / 업종 내 순위 · 비교(Lite) → C03 · C10에 '다른 게임 · 다른 커뮤니티 대비' 순위 표 | 검색 결과만 | 무료 공개 |
| S207 | [WHO COVID-19 Epidemiological Update (Key highlights) + 대시보드](https://www.who.int/publications/m/item/weekly-epidemiological-update-on-covid-19---1-september-2023) | 공개 대시보드 | C01 C10 C07 | Key highlights → Global overview → Special focus → Regional overviews 순서 → C10 주간 보고를 '한 줄 결론 → 전체 지표 → 이번 주 이슈 → 커뮤니티별' 순서로 / 보고서(서술)와 대시보드(세부 데이터)를 분리하고 서로 연결 → C01 결론 문장에서 해당 C07 · C08 차트로 가는 링크 | 검색 결과만 | 무료 공개 |
| S208 | [OCHA Humanitarian Dashboard 가이드 (상황 개요 · 다이얼 · 근거)](https://humanitarian.atlassian.net/wiki/download/attachments/230457426/Humanitarian+Dashboard+Guidance.pdf?version=1) | 공개 대시보드 | C01 C02 C03 C10 | '다이얼 범주와 근거' 층 → C02 AI 판단 초안의 수준(관찰 · 주의 · 대응)을 다이얼로, 바로 아래 근거 지표와 출처 글 / 대시보드 그래픽 → 상황 개요 → 부문 개요 → 출처의 층 → 첫 화면 C01, 펼치면 C02 → C03 → 원문 순서의 점진 공개 | 검색 결과만 | 무료 공개 |
| S209 | [빅카인즈(BIG KINDS) 이슈 분석 — 관계도 · 키워드 트렌드 · 연관어](https://wikidocs.net/331431) | 국내 여론 · 트렌드 | C06 C07 C10 | 키워드 트렌드(일 · 주 · 월 · 연 전환) + 급증 시점 → C07 일별 · 주별 전환과 급증 주 강조 / 관계도 · 트렌드 · 연관어 3종을 한 보고서로 → C10 주간 보고의 키워드 섹션을 '추이 · 연관어 · 관계'로 고정 | 검색 결과만 | 로그인 필요 |
| S213 | [썸트렌드 비교분석 · 채널별 언급량 · 긍부정 연관어](https://inside.ampm.co.kr/insight/2831) | 국내 여론 · 트렌드 | C07 C08 C06 C03 | 채널별 언급량 추이 + 증감률 → C07 커뮤니티별 글 수 지수 표에 '전주 대비 증감률' 열 / 긍정어 · 부정어 연관어 목록 → C08 감성 추이 아래 '이번 주 부정 연관어 상위'로 감성 변화 이유 보조 | 검색 결과만 | 무료 공개 |
| S215 | [문화체육관광부 정책여론수렴시스템 (키워드 기간별 감성 언급량)](https://www.data.go.kr/biz/dcat/metadata/15152794.do) | 국내 여론 · 트렌드 | C08 C09 C05 | 키워드 × 기간 × 긍정 · 부정 · 중립 언급량 → C09 '키워드 그룹별 부정 비율과 추이' 표의 데이터 구조 / '정책 여론 파악 → 대국민 소통 활용' 목적 → C05 운영 대응 전후 비교(공지 전후 키워드 감성 변화)를 공공 사례로 설명할 근거 | 검색 결과만 | 확인 불가 |
| S217 | [한국갤럽 데일리 오피니언 — 직무 긍정 · 부정률과 부정 평가 이유](https://weekly.khan.co.kr/article/202609111016001) | 국내 여론 · 트렌드 | C01 C09 C10 | 긍정 · 부정률 + 부정 이유 비율 + 분석가 해설 → C01 이번 주 결론을 '순감성 변화 → 부정 주제 상위 3 → 같은 주 사건(공지 · 업데이트) 해석' 3단으로 / 부정 평가 이유를 비율로 순위화 → C09 주제별 부정 비율 상위 목록 | 검색 결과만 | 확인 불가 |
| S220 | [Steambase Lost Ark 게임 페이지 (월별 평균 · 증감 · 리뷰 표)](https://steambase.io/apps/1599340) | 게임 시장 지표 | G C10 C08 | Steambase 월별 표의 '평균 · 증감(절대) · 증감(%) · 최고' 4열 → G 스팀 동시 접속 카드와 C10 주간 보고 13주 표에 '평시 대비 증감' 열을 같은 형식으로 / Steambase 월별 긍정 · 부정 리뷰 표 → C08 감성 추이 표에 커뮤니티별 긍정 · 부정 글 수와 순감성 변화를 월 · 주 단위로 나란히 | 검색 결과만 | 무료 공개 |
| S223 | [PlayTracker Insight (추정치 + 신뢰 구간 표기)](https://playtracker.net/info/how_insight_works/) | 게임 시장 지표 | C11 C04 G | PlayTracker 게임 페이지의 '추정치 옆 90% 신뢰 구간 문장' → C11 분류 정확도 카드와 C04 정독 요약 신뢰도에 '95% 구간 ±x%p'를 숫자 바로 옆에 문장으로 / PlayTracker 가이드의 '실제 변화가 며칠 늦게 반영' 안내 → C07 · C08 추이 차트에 수집 지연 · 집계 기준 시각 주석 | 검색 결과만 | 무료 공개 |
| S240 | [크래프톤 하이브리드 분석 (AI 가설 + Tableau 검증)](https://www.tableau.com/ko-kr/solutions/customer/how-krafton-enhances-reliability-of-game-meta-analysis) | BI 갤러리 | C04 C02 C11 | 크래프톤의 'AI 가설 → 분석가 데이터 검증' 흐름 → C04 원인 가설마다 '검증 상태(미검증 · 지표 확인됨 · 반박됨)'와 확인에 쓴 지표 링크 / 같은 흐름 → C02 AI 판단 초안을 사람이 확정 · 수정하는 단계로 명시 | 검색 결과만 | 확인 불가 |
| S243 | [Currents AI (게임 커뮤니티 감성 추적 · 기능 요청 · 경쟁 커뮤니티)](https://www.currents.one/en/blog/how-gaming-studios-use-ai-to-keep-players-hooked) | 게임 커뮤니티 분석 | C08 C09 C02 | Currents의 '기능 요청 자동 식별' → C09 의견 유형에 '개선 요청'을 따로 두고 주제별 요청 목록 / Currents의 '참여 하락 시작 시 알림' → C02 이슈 후보에 글 수 급감도 이상 신호로 포함(급증만이 아니라) | 검색 결과만 | 유료 |
| S246 | [Unity Safe Text 모더레이션 대시보드 · 커뮤니티 상태](https://docs.unity.com/en-us/safe-text/overview-and-community-health) | 게임 라이브 운영 | C03 C08 C05 | Safe Text의 '사건 → 증거 검토 → 조치' 동선 → C03 이슈 근거에서 대표 글(증거) 확인 후 같은 주 운영 대응(제재 등)으로 이어지는 순서 / Safe Text의 '커뮤니티 상태 점수 7 · 15 · 30일 전환' → C08 순감성 지수의 기간 전환 버튼 | 검색 결과만 | 로그인 필요 |
| S247 | [GGWP Player Reports (신고 분류 · 커뮤니티 상태 분석)](https://ggwp.com/player-reports) | 게임 라이브 운영 | C02 C03 C08 | GGWP의 'AI 우선순위 → 사람 검토' 대시보드 → C02 이슈 후보 목록을 AI가 정렬하고 담당자가 확정하는 검토 큐로 / GGWP의 '사건을 맥락과 함께 검토' → C03 이슈 근거에 대표 글 앞뒤 맥락(같은 스레드 · 같은 시간대 글) | 검색 결과만 | 무료 공개 |
| S249 | [Heroic Labs Satori 분석 대시보드 (Status · Game Metrics · 위젯)](https://heroiclabs.com/blog/satori-analytics-dashboards/) | 게임 라이브 운영 | C05 C10 G | Satori의 'Live Events 위젯을 지표 위젯 옆에' → C05 운영 대응 전후 비교에 공지 · 업데이트를 이벤트 행으로 두고 같은 기간의 부정 비율 차트를 나란히 / Satori의 '게임 버전 필터' → C05 · C08에 업데이트(패치) 버전 경계로 기간을 자르는 필터 | 검색 결과만 | 유료 |
| S255 | [Newzoo × Reddit 커뮤니티 감성 · 토픽 데이터](https://www.pocketgamer.biz/newzoo-furthers-its-games-engamement-insights) | 게임 커뮤니티 분석 | C08 C07 C05 C03 | Newzoo의 'IP별 서브레딧 게시글 수 벤치마크' → C07 글 수 지수를 경쟁 게임 커뮤니티와 같은 축에 놓는 비교 / Newzoo의 '주요 이벤트가 감성에 준 영향' → C05 업데이트 효과에 이벤트 전후 긍정 · 중립 · 부정 비율 변화 | 검색 결과만 | 유료 |
| S256 | [Bruin 모바일 게임 사례: 디스코드 감성 하락이 이탈 급증보다 먼저 오나](https://getbruin.com/use-cases/mobile-gaming/gx2-discord-sentiment-trend-before-churn-spike/) | 게임 커뮤니티 분석 | C02 C05 C08 | Bruin의 '감성 15% 하락 · 5일 시차' 같은 명시적 임계 규칙 → C02 이슈 후보 기준(평시 대비 몇 % · 몇 주)을 화면에 문장으로 / Bruin의 '이벤트 출시 후 72시간 감성 변화' 질문 → C05 대응 전후 비교의 기본 창(공지 전 · 후 N일)을 명시 | 검색 결과만 | 무료 공개 |
| S257 | [Steam Review Miner — 평판 하락 진단 (Apify)](https://apify.com/muddy_snowshoe/steam-review-miner) | 리뷰 분석 | C02 C09 C08 | Review Miner의 '표본 수를 고려한 기준을 넘을 때만 표시' → C02 이슈 후보 판정에 글 수가 적은 게시판의 과민 반응을 막는 최소 표본 조건 / Review Miner의 '진행 중 하락 vs 이미 회복된 논란' 구분 → C02 AI 판단 초안의 수준에 '지속 · 회복 중 · 신규' 상태 | 검색 결과만 | 유료 |
| S258 | [Steam Game Reviews & Player Feedback Analyzer / Game Patch Impact (Apify)](https://apify.com/obliging_persimmon_cki/steam-game-feedback-analyzer.md) | 리뷰 분석 | C05 C04 C09 | Patch Impact의 '전후 창 길이 설정(기본 7일)' → C05 운영 대응 전후 비교에 공지 기준 전 · 후 7일 기본 창과 변경 옵션 / Feedback Analyzer의 '늘어난 주제 = 가능한 회귀, 인과 주장 안 함' → C04 원인 가설 문구를 '가능성'으로 쓰고 근거 지표를 붙이는 규칙 | 검색 결과만 | 유료 |
| S263 | [소규모 스튜디오용 무료 라이브옵스 잔존 대시보드 템플릿 16선 (2026 Q4)](https://gamineai.com/resources/16-free-live-ops-retention-dashboard-template-resources-small-studios-2026) | 대시보드 디자인 갤러리 | C10 C05 | GamineAI의 '지표 정의(DAU · WAU · 잔존 창)를 잠가 비교 가능하게' → C10 주간 보고 하단에 비교 기준 · 정의를 고정 문구로 / GamineAI의 '사고 기간 · 릴리스 체크포인트 대시보드' → C05에 업데이트 · 장애 기간을 음영 구간으로 | 검색 결과만 | 무료 공개 |
| S268 | [No Man's Sky 스팀 리뷰 토픽 진화와 패치 (DiGRA 논문)](https://dl.digra.org/index.php/dl/article/view/1303) | 기타 | C09 C05 | 논문의 '주제별 시간 추이를 패치 시점과 대조' → C09 키워드 그룹 비중 추이 차트에 업데이트 시점 세로선 / 같은 방법 → C05 업데이트 효과를 전체 감성 하나가 아니라 주제별로 나눠 보여 주기 | 검색 결과만 | 무료 공개 |
| S269 | [ServiceNow Now Assist for CSM 감성 분석 대시보드](https://www.servicenow.com/community/csm-articles/servicenow-otto-for-csm-sentiment-analysis-dashboard/ta-p/3447142) | AI 인사이트 | C08 C04 C02 | ServiceNow의 '감성 변화 배경 LLM 요약' → C08 감성 추이 차트에서 큰 변화가 있는 주를 누르면 AI가 쓴 변화 이유와 C04 정독 요약으로 연결 | 검색 결과만 | 유료 |
| S271 | [Lightdash AI 에이전트 · 예약 AI 요약 전송](https://docs.lightdash.com/guides/ai-agents) | 오픈소스 대시보드 도구 | C01 C10 | Lightdash 예약 전송의 '갱신된 차트 + AI 요약' 묶음 → C10 주간 보고를 매주 같은 질문으로 재실행해 숫자와 요약을 같이 갱신 / README의 '검사 가능한 쿼리(inspectable queries) · 검증된 답 재사용' → C11 방법 공개: AI 판단마다 근거 쿼리 · 집계 조건 펼치기 | 열람 | 오픈소스 |
| S272 | [Evidence (SQL + Markdown 보고서, BigValue 비교 · 스파크라인)](https://docs.evidence.dev/components/big-value) | 오픈소스 대시보드 도구 | C07 C10 | Evidence BigValue의 '비교 제목(vs. Last Month) + 퍼센트 비교 + 스파크라인' → C10 주간 보고 숫자 카드에 '평시 대비' 비교 기준을 글자로 명시 / Markdown 안에 숫자와 문장을 섞는 보고서 방식 → C01 이번 주 결론 문장 안에 실제 지표 값을 변수로 끼워 넣기 | 열람 | 오픈소스 |
| S278 | [Lumen (HoloViz, 데이터 대화 · 요약 에이전트)](https://raw.githubusercontent.com/holoviz/lumen/main/README.md) | 오픈소스 대시보드 도구 | C01 C11 | Lumen의 'LLM 출력 검사 · 검증 · 수정' → C11 방법 공개: AI 요약마다 사용한 쿼리 · 변환 단계를 펼쳐 보게 / Lumen의 '결과 요약 + 핵심 인사이트 추출' → C01 이번 주 결론을 실제 집계 파이프라인 결과에서만 생성 | 열람 | 오픈소스 |
| S283 | [Cube AI summary 위젯](https://docs.cube.dev/docs/explore-analyze/dashboards/widgets/ai-summary) | AI 인사이트 | C01 C11 | Cube의 '요약도 차트와 같은 위젯 하나' 배치 → C01 결론 카드를 지표 카드 줄 바로 옆 위젯으로 두고 같은 필터를 공유 / 위젯별 프롬프트 · 모델 지정 → C11 비용: 결론 요약과 정독 요약에 다른 모델을 쓰고 위젯에 모델명을 표시 | 검색 결과만 | 유료 |
| S284 | [Twitter Analytics Dashboard (AUT, Streamlit)](https://github.com/AUT-Twitter-Analytics/Streamlit-Dashboard) | 오픈소스 대시보드 도구 | C08 C09 | 감성 + 토픽 탐지 + 개체명(NER) 탭 구성 → C09 VOC 주제 지도에 '언급된 직업 · 콘텐츠 · 아이템' 같은 개체 축을 더해 주제 × 개체 부정 비율 보기 | 열람 | 오픈소스 |
| S286 | [Dashboard Design Patterns (Bach et al., IEEE VIS 2022)](https://dashboarddesignpatterns.github.io/patterns.html) | 대시보드 디자인 갤러리 | C02 C03 C07 C11 | 'Thresholds — 좋음 · 나쁨 · 중립 판단을 명시' 패턴 → C02 이슈 후보의 AI 판단 수준(주의 · 경고 등)을 임계값 규칙과 같이 표시 / 'Stratified layout(위는 요약, 아래는 상세)' + 'Hierarchical(드릴다운)' → C01 결론 → C02 이슈 후보 → C03 근거 → C04 정독 요약 순서의 화면 구조 | 열람 | 무료 공개 |
| S291 | [UKHSA Data Dashboard](https://ukhsa-dashboard.data.gov.uk/about) | 공개 대시보드 | C07 C10 C11 | 지표별 '정의 + 왜 보여 주나' 문서 → C11 방법 공개에 각 지표(글 수 지수 · 순감성 등)의 정의와 사용 이유 카드 / 헤드라인 숫자 + 추세 화살표 + PDF 제공 → C10 주간 보고 인쇄본 | 검색 결과만 | 무료 공개 |
| S292 | [CDC COVID Data Tracker — Community Levels + Weekly Review(해설 요약)](https://stacks.cdc.gov/view/cdc/115111) | 공개 대시보드 | C01 C02 C11 | 주간 Interpretive Summary(숫자 뒤 해설 문서) → C01 이번 주 결론을 '등급 + 해설 문단' 형식으로 / 여러 지표를 묶은 Low/Medium/High 주간 등급 → C02 이슈 후보 수준 판단 규칙 공개 | 검색 결과만 | 무료 공개 |
| S302 | [British Airways Reviews Dashboard (포트폴리오)](https://mostaql.com/portfolio/2609033-british-airways-reviews-dashboard) | BI 갤러리 | C08 C09 | '불만 추적 + 경쟁사 비교' → C09 주제별 불만 비율을 커뮤니티 간(또는 경쟁 게임 지표 G와) 비교 | 검색 결과만 | 무료 공개 |
| S303 | [Carglass 리뷰 분석 (ChatGPT API + Tableau)](https://atlantic-technologies.eng.it/en/case-studies/carglass) | AI 인사이트 | C06 C08 C11 | 'LLM 감성 + 반복 키워드 추출 → BI 시각화' 파이프라인 → 우리 C06 · C08과 같은 구조라 분류 프롬프트 · 검증 방식(C11) 비교 사례로 | 검색 결과만 | 확인 불가 |
| S305 | [Porter — Google Business Profile Reviews 템플릿 (Looker Studio)](https://portermetrics.com/en/templates/google-looker-studio/google-business-profile-reviews-porter-reports/) | BI 갤러리 | C06 C08 C09 | '감성 3분류 + 공통 주제 · 키워드' 한 페이지 → C08 감성 비율과 C09 주제 · C06 키워드를 같은 필터로 묶은 요약 페이지 | 검색 결과만 | 확인 불가 |
| S311 | [Zoho Analytics — Zia Insights (Explain Data · 서술 수준)](https://help.zoho.com/portal/en/kb/analytics/user-guide/data-storytelling/zia-insights/articles/zia-insights-7-9-2022) | AI 인사이트 | C01 C04 | 서술 수준 Low/Medium/High → C01 결론을 '한 줄 / 문단 / 상세' 세 단계로 펼치기 / 데이터 점 'Explain Data' → C07 · C08 차트의 튀는 주차를 누르면 C04 정독 요약으로 연결 | 검색 결과만 | 유료 |
| S313 | [Pyramid Analytics — Smart Insights · Explain · Explain the difference](https://help.pyramidanalytics.com/Content/root/MainClient/apps/Discover/PRO/SmartInsights/SmartInsights.htm) | AI 인사이트 | C02 C04 C05 | 'Explain the difference(두 점 차이의 요인)' → C05 운영 대응 전후 부정 비율 차이를 누르면 어떤 주제 · 게시판이 차이를 만들었는지 분해 / 인사이트 수준 light/advanced 필터 → C02 AI 판단 초안을 요약/상세로 전환 | 검색 결과만 | 유료 |
| S314 | [Looker Conversational Analytics — 대시보드 에이전트](https://docs.cloud.google.com/looker/docs/studio/conversational-analytics?authuser=2) | AI 인사이트 | C01 C04 | '대시보드 타일 범위로 제한된 에이전트' → C04 원인 가설을 이번 주 대시보드 지표(C07~C09)와 정독 6건 안에서만 세우게 / 여러 타일을 엮어 하락 원인 제안 → C02 이슈의 '이유'에 다른 차트(운영 공지 C05, 키워드 C06) 근거를 인용 | 검색 결과만 | 유료 |
| S315 | [Narrative BI (데이터 내러티브 피드 · 이상 알림)](https://narrative.bi/platform/) | AI 인사이트 | C01 C02 | '무엇이 바뀌었나 · 왜 중요한가 · 어디를 볼까' 3문장 틀 → C02 AI 판단 초안(수준 · 이유 · 다음 행동) 문장 틀 | 검색 결과만 | 유료 |
| S316 | [Anodot 비즈니스 모니터링 (상관 이상 묶기 · Triage)](https://support.anodot.com/hc/en-us/articles/360013325240-What-is-Anodot) | AI 인사이트 | C02 C03 | '상관된 이상을 한 사건으로 묶기' → C02 이슈 후보에서 같은 주에 여러 커뮤니티 · 지표가 함께 튀면 하나의 이슈로 묶고 C03에 '다른 커뮤니티의 같은 지표'로 펼치기 | 검색 결과만 | 유료 |
| S317 | [Sisu Data — 핵심 동인 분석 · Smart Waterfall](https://bigdatawire.com/this-just-in/sisu-data-announces-smart-waterfall-charts) | AI 인사이트 | C02 C04 C09 | Smart Waterfall(동인별 기여 폭포) → C02 '부정 비율 상승'을 주제 · 게시판별 기여로 분해한 폭포 차트 / PoP 세그먼트 변화 순위 → C09 주제 지도에서 평시 대비 가장 많이 바뀐 주제를 위로 | 검색 결과만 | 확인 불가 |
| S318 | [Julius AI (차트 Explain · 원인 가설)](https://www.datacamp.com/tutorial/julius-ai-guide) | AI 인사이트 | C01 C04 | '요약 + 차트 + 원자료 표' 3종 세트 → C04 정독 요약의 각 하위 문제 아래에 인용 원문 표를 붙이기 / 생성 코드 내보내기 → C11 방법 공개(집계 코드 열람) | 검색 결과만 | 로그인 필요 |
| S323 | [Awario Social Listening Dashboards (차트 클릭 → 원문 언급)](https://awario.com/social-listening-dashboards/) | 소셜 리스닝 | C03 C07 C08 | '차트 어느 부분이든 클릭 → 그 조건의 원문' → C03 이슈 근거: C07 · C08 막대를 누르면 해당 커뮤니티 · 주차 · 감성 글 목록 / 언급 증가 · 감성 시간 변화 → C07 · C08 같은 시간축 정렬 | 검색 결과만 | 유료 |
| S324 | [Perspective AI — VoC 대시보드 가이드(2026)](https://getperspective.ai/blog/voice-of-customer-dashboard-2026-that-execs-actually-use/markdown) | VOC 분석 | C04 C09 C10 | '감성 점수 → 그 뒤 주제 → 원문 인용' 3단 → C09 주제 지도에서 주제를 누르면 C04의 인용 포함 하위 문제로 / '임원이 실제로 쓰는 지표만' 선별 → C10 주간 보고 지표 수 줄이기 | 검색 결과만 | 무료 공개 |

### 부분 참고 (126곳)

| ID | 이름 | 종류 | 구성요소 | 참고할 점 | 열람 | 접근 |
|---|---|---|---|---|---|---|
| S001 | [Power BI Smart Narrative visual](https://learn.microsoft.com/en-gb/power-BI/visuals/power-bi-visualization-smart-narrative) | AI 인사이트 | C01 | Smart Narrative의 '문장 속 동적 값(증가율)' → C01 이번 주 결론 문장 안의 배수 · 비율을 텍스트가 아니라 지표 값 바인딩으로 넣어 수치와 문장이 어긋나지 않게 | 검색 결과만 | 확인 불가 |
| S003 | [Power BI KPI visual](https://learn.microsoft.com/en-gb/power-BI/visuals/power-bi-visualization-kpi) | 대시보드 디자인 갤러리 | C08 | KPI 비주얼의 '낮을수록 좋은 지표는 색 방향 반전' → C08 · C09에서 부정 비율 상승을 빨강으로, 순감성 하락을 빨강으로 일관되게 색 방향 지정 | 검색 결과만 | 확인 불가 |
| S006 | [Tableau Public Viz of the Day - Amazon Sales Performance dashboard](https://thedataschool.co.uk/mila-kholodiy/my-first-viz-of-the-day/) | BI 갤러리 | C10 | Amazon Sales VOTD의 '상단 KPI 카드 5개 + 카드별 직전 기간 비교' → C10 주간 보고 머리의 숫자 줄(글 수 지수 · 순감성 · 부정 비율 등)에 전주 대비 비교를 붙이기 | 검색 결과만 | 무료 공개 |
| S009 | [Looker Studio scorecard (compact with trend)](https://www.databloo.com/blog/google-looker-studio-scorecards/) | 대시보드 디자인 갤러리 | C07 | 스코어카드의 '압축 숫자 + 떠 있는 추세선' → C07 글 수 지수 카드에 평시=100 숫자와 13주 미니 추세선 | 검색 결과만 | 확인 불가 |
| S012 | [Amazon QuickSight KPI visual (comparison, sparkline, progress bar)](https://docs.aws.amazon.com/quicksight/latest/user/KPI-options.html) | 대시보드 디자인 갤러리 | C07 | QuickSight KPI의 '비교 값 전용 조건부 서식(색 · 아이콘)' → C07 · C08 카드에서 평시 대비 차이만 따로 색칠하고 본 값은 중립색 | 검색 결과만 | 확인 불가 |
| S013 | [Qlik Insight Advisor natural-language insights / Qlik Answers](https://help.qlik.com/en-US/cloud-services/Insights/insight-advisor-natural-language.htm) | AI 인사이트 | C01 | 'Show additional insights' 펼치기 → C01 이슈별 인사이트를 차트 아래 접힌 상태로 두고 펼쳐 읽게 | 검색 결과만 | 확인 불가 |
| S015 | [ThoughtSpot SpotIQ change analysis](https://docs.thoughtspot.com/cloud/latest/spotiq-change) | AI 인사이트 | C02 | SpotIQ의 'KPI 변화 기여 속성 분해' → C02 부정 비율 상승을 주제(C09) · 게시판별 기여로 분해해 이유 칸에 표시 | 검색 결과만 | 확인 불가 |
| S016 | [Metabase X-rays](https://Metabase.com/docs/latest/exploration-and-organization/x-rays) | 오픈소스 대시보드 도구 | C03 | X-ray의 'Compare to the rest'(차트 한 점을 나머지와 비교) → C03 이슈 근거에서 이 커뮤니티의 같은 지표를 다른 커뮤니티 전체와 나란히 비교 / Zoom in / Zoom out 제안 → C07에서 커뮤니티 → 게시판 → 일별로 내려가고 올라오는 이동 버튼 | 열람 | 오픈소스 |
| S017 | [Apache Superset / Preset Big Number with Trendline](https://docs.preset.io/docs/big-number-chart) | 오픈소스 대시보드 도구 | C07 | Big Number with Trendline → C07 커뮤니티별 글 수 지수 카드(큰 숫자 + 13주 추세선, 시간 단위 주별 고정) | 검색 결과만 | 오픈소스 |
| S018 | [Grafana Stat panel](https://grafana.com/docs/grafana/v10.3/panels-visualizations/visualizations/stat) | 오픈소스 대시보드 도구 | C07 C08 | Stat의 'Percent change color mode = Inverted' → C08 부정 비율 카드에서 증가를 빨강으로 표시(증감 % 자동 표기) / 'All values'로 행마다 Stat 타일 → C07 커뮤니티별 글 수 지수 타일 줄을 같은 서식으로 반복 | 열람 | 오픈소스 |
| S019 | [Grafana Play (demo dashboard gallery)](https://grafana.com/blog/2025/11/17/grafana-play-updates-a-redesigned-homepage-to-celebrate-our-community) | 공개 대시보드 | C07 | Grafana Play의 Stat · 시계열 예제 대시보드 → C07 · C08 패널 배치와 임계값 색을 실제 화면으로 비교해 보는 용도 | 검색 결과만 | 무료 공개 |
| S020 | [Sisense Widget Narratives](https://docs.sisense.com/main/SisenseLinux/sisense-narratives.md) | AI 인사이트 | C01 | Sisense 위젯 단위 Narrative → C01 이슈별 인사이트를 해당 지표 카드에 붙이는 방식(페이지 요약과 분리) | 검색 결과만 | 확인 불가 |
| S023 | [Google Analytics 4 Insights (Analytics Intelligence)](https://support.google.com/analytics/answer/9443595) | AI 인사이트 | C02 | GA4 Insights의 '카드 피드 + 1년 보관 + Load more' → C02 지난 주차 이슈 후보 기록을 같은 카드 형식으로 거슬러 보기 | 검색 결과만 | 확인 불가 |
| S026 | [Amplitude Automated Insights](https://www.amplitude.com/blog/introducing-automated-insights) | AI 인사이트 | C02 | Automated Insights의 '발견 + 추천' 쌍 → C02 이슈별 AI 판단(이유 + 다음 행동) 묶음 | 검색 결과만 | 확인 불가 |
| S027 | [Mixpanel Spark (now Mixpanel Agent)](https://mixpanel.com/spark-ai) | AI 인사이트 | C11 | Spark의 'AI는 쿼리만, 계산은 시스템 + 쿼리 들여다보기' → C11 방법 공개: AI는 분류만 하고 지수 계산은 규칙 코드임을 밝히고 계산식을 펼쳐 보이기 | 검색 결과만 | 확인 불가 |
| S030 | [Einstein Discovery Stories (Tableau CRM / CRM Analytics)](https://www.thebricks.com/resources/guide-how-to-use-einstein-discovery-in-tableau) | AI 인사이트 | C04 | '데이터 부족 시 Why 보기 비활성' → C04 정독 표본이 적거나 글 수가 평시보다 너무 적은 주에는 원인 가설 칸을 '판단 보류'로 | 검색 결과만 | 확인 불가 |
| S034 | [Geckoboard Number visualization](https://support.geckoboard.com/en/articles/6055767-guide-to-the-number-visualization) | 대시보드 디자인 갤러리 | C10 | Geckoboard '모든 숫자에 비교(목표 · 직전 기간)' → C10 주간 보고의 각 숫자 옆에 비교 기준(평시 8주 평균)을 반드시 함께 | 검색 결과만 | 확인 불가 |
| S037 | [Microsoft Fabric Copilot-generated Real-Time Dashboard](https://learn.microsoft.com/en-us/fabric/fundamentals/copilot-generate-dashboard) | AI 인사이트 | C10 | Fabric의 '인사이트 개요 페이지 / 데이터 프로필 페이지' 분리 → C10 보고 첫 장(결론)과 부록(수집 건수 · 결측 · 분류 커버리지) 분리 | 검색 결과만 | 확인 불가 |
| S040 | [Cascade executive summary widget (hyperlinked citations)](https://www.cascade.app/academy/chapter/executive-summary-widget) | AI 인사이트 | C01 | Cascade의 '문장별 하이퍼링크 인용' → C01 결론 문장의 숫자를 원 지표 표로 링크 | 검색 결과만 | 확인 불가 |
| S041 | [Rapid7 InsightIDR AI Assistant Summary Card](https://docs.rapid7.com/insightidr/ai-assistant-summary-card/) | AI 인사이트 | C11 | Rapid7 요약 카드의 '위젯과 같은 데이터 + 사람 분석 대체 아님 문구' → C01 · C11 AI 결론 아래 'AI 초안, 운영자 검토 전' 표시 | 검색 결과만 | 확인 불가 |
| S042 | [AI dashboard design principles (confidence & uncertainty in UI)](https://www.lazarev.agency/articles/ai-dashboard-design) | 기타 | C04 | 'AI 결과 옆에 출처 범위 · 신선도 · 확신도' → C04 정독 요약 머리에 '읽은 글 6건(추천 3 · 무작위 3) · 수집 시각 · 신뢰도' 줄 | 검색 결과만 | 확인 불가 |
| S043 | [Stephen Few bullet graph & sparklines](https://www.fusioncharts.com/resources/chart-primers/bullet-graph) | 대시보드 디자인 갤러리 | C10 | 불릿 그래프 + 스파크라인 한 줄 → C10 주간 보고 표에서 지표별 '이번 주 vs 평시 범위' 막대와 13주 추이를 한 행에 | 검색 결과만 | 확인 불가 |
| S060 | [AI Customer Feedback Dashboards](https://www.unwrap.ai/dashboards-reporting) | VOC 분석 | C09 | 'Found by Unwrap'(미리 정하지 않은 그룹 발견) → C09 기존 주제 밖의 새 묶음을 따로 표시 | 검색 결과만 | 확인 불가 |
| S061 | [SentiSum insight dashboard](https://zendesk.fr/marketplace/partners/3324/sentisum) | VOC 분석 | C09 | SentiSum '문의 사유(reason for contact) 추세' → C09 의견 유형(불만 · 개선 요청)별 추세 | 검색 결과만 | 확인 불가 |
| S065 | [Productboard Spark (feedback synthesis)](https://www.productboard.com/spark/) | VOC 분석 | C03 | Productboard '모든 기회가 원 피드백으로 연결' → C03 이슈마다 근거 글 링크 목록 | 검색 결과만 | 확인 불가 |
| S074 | [Hootsuite Listening / crisis management (Talkwalker-powered)](https://hootsuite.com/platform/crisis-management) | 소셜 리스닝 | C02 | Hootsuite '언급량 · 도달 · 참여 급증 자동 식별' → C02 이슈 후보에 글 수뿐 아니라 추천 · 댓글 수 급증도 신호로 | 검색 결과만 | 확인 불가 |
| S079 | [리스닝마인드 클러스터파인더 리포트](https://docs.channel.io/lm-skills/ko/articles/clusterfinder-report-3b97d33b) | 국내 여론 · 트렌드 | C10 | 리스닝마인드 '대시보드 / A4 보기 전환' → C10 주간 보고를 같은 데이터로 화면형 · 인쇄형 전환 | 검색 결과만 | 확인 불가 |
| S080 | [퓰리처AI 평판·위기관리](https://view.asiae.co.kr/article/2026072208240029096) | 국내 여론 · 트렌드 | C10 | 퓰리처AI 보고서 순서 '이슈 → 언급량 변화 → 여론 → 키워드 → 리스크 · 시사점' → C10 주간 보고 목차 순서 | 검색 결과만 | 확인 불가 |
| S094 | [Live Ops Insights (ex-Playliner)](https://sensortower.com/ko/product/live-ops) | 게임 시장 지표 | C05 | Sensor Tower 라이브옵스 캘린더 → C05 로스트아크 공지 · 이벤트를 주차 축 타임라인으로(문제 안내 · 변경 예고 등 유형 색) | 검색 결과만 | 확인 불가 |
| S100 | [PlayerXP](https://www.g2.com/products/player-xp/discuss) | 게임 커뮤니티 분석 | C08 | PlayerXP '게임 피드백으로 학습한 감성 점수' → C11 · C08 일반 감성 모델이 아니라 게임 은어 기준 정확도를 따로 공개 | 검색 결과만 | 확인 불가 |
| S101 | [BetaHub Discord sentiment](https://betahub.io/resources/setup-discord-sentiment-analysis/) | 게임 커뮤니티 분석 | C11 | BetaHub의 '비꼼 · 밈은 오분류 가능' 경고 → C11 방법 공개와 C08 감성 추이 옆 한계 문구(커뮤니티 은어 · 반어) | 검색 결과만 | 유료 |
| S102 | [Community analytics practice (sentiment levels x topics)](https://www.keywordsstudios.com/en/about-us/news-events/news/how-community-managers-use-analytics-to-understand-and-serve-players-better/) | 게임 커뮤니티 분석 | C09 | 감성 4단계 × 주제 5개 행렬 → C09 주제 × 의견 유형 표의 행 · 열 초안 | 검색 결과만 | 확인 불가 |
| S110 | [Game Performance Monitor](https://xsolla.partnerpage.io/integrations/partner/newzoo) | 게임 시장 지표 | G | Newzoo '맞춤 경쟁작 그룹' 비교 → G 게임 지표에서 로스트아크를 같은 장르 몇 작품과 나란히(PC방 점유율 · 스팀 동시 접속) | 검색 결과만 | 확인 불가 |
| S112 | [Streams Charts game release stats](https://streamscharts.com/games/stream/release-stats) | 게임 시장 지표 | G | Streams Charts '출시 주간(사건 기준) 분해' → G · C05 업데이트 주를 기준으로 전후 주 지표를 나란히 | 검색 결과만 | 유료 |
| S116 | [더로그 주간 PC방 리포트](https://www.invenglobal.com/articles/27040/the-log-pc-cafe-playtime-increases-58-in-2nd-week-of-october) | 게임 시장 지표 | G | 더로그 리포트 '총량 + 전주 대비 → 순위 변동 서술' 순서 → G 게임 지표 블록의 문장 형식(점유율 · 순위 + 전주 대비 + 움직임 한 줄) | 검색 결과만 | 확인 불가 |
| S117 | [게임메카 주간 인기순위 (민심 신호 해석)](https://www.gamemeca.com/news.php?ca=O&p=155) | 게임 시장 지표 | G | 게임메카 '순위 변동을 민심 신호로 해석' → G 순위 변동을 C01 결론에 넣을 때 감성 지표(C08)와 함께 제시 | 검색 결과만 | 확인 불가 |
| S123 | [Caplena 텍스트 분석 대시보드 + AI 챗봇](https://www.ki-syndikat.de/tools/caplena/) | VOC 분석 | C09 | Caplena의 analyst-in-the-loop(사람이 AI 주제를 고쳐 가며 쓰는 흐름) → C11 분류 정확도 검수 화면에서 사람이 고친 라벨을 다음 주 분류 기준에 반영 | 검색 결과만 | 유료 |
| S124 | [Wonderboard / Wonder (리뷰 분석)](https://wonderflow.ai/product/customer-insights-platform) | 리뷰 분석 | C04 | Wonderflow의 '인사이트 출처를 리뷰 원문에 하이라이트' → C04 정독 요약의 인용문마다 원문 글에서 해당 문장을 하이라이트해 보여주기 | 검색 결과만 | 유료 |
| S126 | [Kraftful 피드백 자동 수집 · 분석](https://docs.kraftful.com/analyze-customer-feedback) | 리뷰 분석 | C09 | Kraftful의 '기능 요청 / 사랑받는 기능 / 불만 / 경쟁 언급' 4분류 → C09 의견 유형(불만 · 개선 요청 · 칭찬)에 '타 게임 비교 언급' 유형 추가 검토 | 검색 결과만 | 유료 |
| S129 | [Lumoa GPT 요약 · 토픽 영향](https://g2.com/products/lumoa/reviews) | VOC 분석 | C11 | Lumoa 사용자들이 지적한 'AI 요약 정확도 불신' → C11 정확도 패널을 결론 카드 옆에 붙여 AI 요약의 신뢰도를 같이 보여줄 근거 사례 / Lumoa 대시보드의 '터치포인트별 카드 비교' → C07/C08 커뮤니티별 카드 나란히 비교 | 검색 결과만 | 유료 |
| S131 | [Zendesk QA Spotlight (Sentiment insight) + AutoQA dashboard](https://support.zendesk.com/hc/en-us/articles/7043759586074-Understanding-spotlight-insights) | VOC 분석 | C03 | Zendesk QA Spotlight의 '감성이 강한 대화를 자동으로 골라 리뷰 대기열에 올리기' → C03 이슈 근거의 대표 글 후보를 '부정 강도 상위'로 자동 선별하는 보조 규칙 | 검색 결과만 | 유료 |
| S133 | [CallMiner Eureka 맞춤 AI 요약 · 시각화](https://www.businesswire.com/news/home/20260309968438/en) | VOC 분석 | C09 | CallMiner의 '요약 프롬프트 템플릿을 고쳐 쓰기' → C11 방법 공개에 정독 요약 프롬프트 템플릿과 버전을 공개 / CallMiner 트리맵 → C09 키워드 그룹 비중을 트리맵으로 표시 | 검색 결과만 | 유료 |
| S135 | [Appfigures Reviews & Ratings](https://appfigures.com/products/reviews-ratings) | 리뷰 분석 | C05 | Appfigures의 '버전별 리뷰 필터' → C05 업데이트 효과에서 업데이트 전후 구간으로 글을 나눠 부정 비율 비교 | 검색 결과만 | 유료 |
| S139 | [Alchemer Digital Fan Signals](https://help.alchemer.com/help/alchemer-mobile-fan-signals-overview) | VOC 분석 | C08 | Alchemer Fan Signals의 '연속 응답 사이의 상태 전환 버킷' → C08 감성 추이에서 '지난주 대비 긍정→부정으로 돌아선 주제' 같은 전환 표시 아이디어 | 검색 결과만 | 유료 |
| S141 | [Reputation Score 드릴다운 · Actions · Reputation IQ](https://reputation.com/platform/reputation-iq) | 리뷰 분석 | C05 | Reputation Actions 탭의 '리뷰가 끝까지 처리되는지 추적' → C05 운영 대응에서 이슈별 공지 · 대응 상태(미대응/안내/조치) 추적 칸 | 검색 결과만 | 유료 |
| S142 | [Chatmeter Pulse AI: Signals](https://www.chatmeter.com/resource/press-release/chatmeter-unveils-future-of-reputation-management/) | 리뷰 분석 | C03 | Chatmeter Signals의 '지역별 강점 · 약점' 인사이트 → C03 다른 커뮤니티의 같은 지표 비교를 '커뮤니티별 강점 · 약점 한 줄'로 요약 | 검색 결과만 | 유료 |
| S148 | [Survicate Insights Hub / Research Assistant (AI Chat)](https://help.survicate.com/en/articles/9515049-research-assistant) | AI 인사이트 | C04 | Survicate의 '응답 하나를 Hub에 저장(노트)' → C04 정독 요약 화면에서 분석가가 인용할 글을 직접 핀 고정 | 검색 결과만 | 유료 |
| S151 | [Zoho CRM VoC dashboards (Zia)](https://help.zoho.com/portal/en/kb/crm-v2-1/zia-artificial-intelligence/voice-of-the-customer/voc-dashboards/articles/crm-v2-summary-analysis-a-voc-chart-for-on-the-go-insights) | VOC 분석 | C08 | Zoho VoC의 '채널 통합 감성 + 채널별 분해' → C08 전체 순감성과 커뮤니티별 순감성을 한 차트에서 전환 | 검색 결과만 | 유료 |
| S153 | [채널톡 VOC 스튜디오 'AI 자동 채우기'](https://docs.channel.io/voc-studio/ko/articles/c3c553ac-AI-%EC%9E%90%EB%8F%99-%EC%B1%84%EC%9A%B0%EA%B8%B0) | VOC 분석 | C09 | 채널톡 'AI 자동 채우기'의 '사용자 정의 기준 → 표에 새 칼럼' → C09 의견 유형 · 주제 분류 결과를 원문 표의 칼럼으로 보여 줘 검수하기 쉽게 | 검색 결과만 | 유료 |
| S154 | [채널톡 커스텀 리포트 출시 · 상담 통계 집계 기준 개선 공지](https://docs.channel.io/updates/ko/articles/%EA%B3%B5%EC%A7%80-%EC%BB%A4%EC%8A%A4%ED%85%80-%EB%A6%AC%ED%8F%AC%ED%8A%B8-%EC%B6%9C%EC%8B%9C-%EB%B0%8F-%EC%83%81%EB%8B%B4-%ED%86%B5%EA%B3%84-%EC%A7%91%EA%B3%84-%EA%B8%B0%EC%A4%80-%EA%B0%9C%EC%84%A0260116-0eae7aa4) | VOC 분석 | C10 | 채널톡이 집계 기준 변경을 공지로 따로 알린 방식 → C10 주간 보고 · C11 방법 공개에 '집계 기준 변경 이력'을 남겨 13주 추이의 단절을 설명 | 검색 결과만 | 유료 |
| S156 | [Syncly VoC Reporting](https://syncly.app/product/voc-reporting) | VOC 분석 | C02 C10 | Syncly의 '새 트렌드 감지 시 알림' → C02 이슈 후보가 기준을 넘으면 알림을 보내는 선택 기능 | 검색 결과만 | 유료 |
| S157 | [크리마 인사이트 / AI 리뷰 분석](https://byline.network/2023/08/%ed%81%ac%eb%a6%ac%eb%a7%88-%ea%b2%bd%ec%9f%81%ec%82%ac-%eb%8f%99%ed%96%a5%eb%b6%80%ed%84%b0-%ec%9d%b8%ea%b8%b0%ec%83%81%ed%92%88%ea%b9%8c%ec%a7%80-%ed%8c%8c%ec%95%85%ed%95%98%eb%8a%94/) | 리뷰 분석 | C09 | 크리마의 '키워드별 긍정/부정 평가' → C09 키워드 그룹 비중 표에 그룹별 긍정/부정 막대를 함께 표시 | 검색 결과만 | 유료 |
| S158 | [솔트룩스 데이터믹시 (온라인 데이터 분석)](https://byline.network/2017/04/25-2/) | 국내 여론 · 트렌드 | C06 | 데이터믹시의 '이슈 감지 분석' → C06 급상승 키워드의 국내 선행 사례로 참고(현재 제공 여부 확인 필요) | 검색 결과만 | 확인 불가 |
| S160 | [오피니언 마이닝 기반 지능형 VOC 분석 시스템(학술)](https://www.koreascience.or.kr/article/JAKO201330251812553.page) | VOC 분석 | C11 | 논문의 '임계값 -0.50에서 정확도 77.8%'처럼 기준값과 정확도를 함께 공개 → C11 방법 공개에 분류 기준(프롬프트 · 임계값)과 정확도를 짝지어 표기 | 검색 결과만 | 무료 공개 |
| S161 | [GitHub CSE 고객 피드백 분석(BERTopic + GPT-4) 사례](https://www.zenml.io/llmops-database/ai-powered-customer-feedback-analysis-at-scale) | AI 인사이트 | C09 C04 | GitHub 사례의 '군집 먼저 → 군집별 LLM 요약' 순서 → C04 정독 요약 대상 6건 외에 같은 주제 군집 글 수를 함께 보여 요약의 대표성을 표시 | 검색 결과만 | 무료 공개 |
| S175 | [Mention 대시보드 · 분석(QuickChart 등)](https://en.support.mention.com/en/articles/8695163-mention-social-listening-analytics-explained) | 소셜 리스닝 | C07 | 기본 7일 + 1일/30일 전환 → C07 일별 · 주별 전환 토글의 기본값을 '이번 주'로 | 검색 결과만 | 유료 |
| S182 | [Keyhole 대시보드 · QuickTrends](https://www.g2.com/products/keyhole) | 소셜 리스닝 | C06 C08 | QuickTrends(여러 키워드 추세 · 점유율 비교) → C06 급상승 키워드 상위 몇 개를 한 차트에 겹쳐 비교 | 검색 결과만 | 유료 |
| S183 | [Exploding Topics 트렌드 카드 · 토픽 페이지 · 대시보드](https://explodingtopics.com/blog/dashboard-announcement) | 기타 | C06 | 성장 패턴 라벨(Regular · Peaked · Exploding) → C06 급상승 키워드에 '반짝 · 지속 · 폭발' 같은 상태 라벨을 배수 옆에 / 카드 = 검색량 + 성장률 + 미니 추세 + 한 줄 설명 → C06 키워드 행 구성(언급 수 · 평시 대비 배수 · 스파크라인 · 대표 글 한 줄) | 검색 결과만 | 유료 |
| S184 | [Glimpse — Google Trends 절대 검색량 · 성장률 확장](https://meetglimpse.com/insights/google-trends-search-volume/) | 기타 | C07 C06 | 상대 지수(0~100)와 절대 수치를 같은 축에 병기 → C07 글 수 지수(평시 = 100) 옆에 실제 글 수를 툴팁 · 보조 축으로 같이 보여 주기 | 검색 결과만 | 로그인 필요 |
| S185 | [Google Trends Explore (Gemini 사이드바 · 상승 검색어)](https://blog.google/products-and-platforms/products/search/google-trends-explore-with-ai/) | 기타 | C06 C01 | 타임라인마다 상승 검색어 목록(+550% 등) → C06 급상승 키워드를 C07 추세 차트의 해당 주 아래에 바로 붙이기 / AI 개편 화면 + '클래식으로 돌아가기' 토글 → 새 대시보드에 AI 해석 없는 원래 보기 전환 제공 | 검색 결과만 | 무료 공개 |
| S186 | [Google Year in Search (연간 급상승 검색어)](https://www.wsoctv.com/news/trending/google-wraps-up-2025-with-year-search/JGVLPEM3ZBAX3GF7ZR2EKXSUDY/) | 공개 대시보드 | C06 C10 | '절대량이 아니라 전년 대비 급증' 기준 → C06 급상승 키워드를 언급 수가 아닌 평시 대비 배수로 정렬하는 근거 / 카테고리별 순위 + 클릭 시 추이 · 관련어 → C10 주간 보고의 키워드 섹션(주제별 상위 + 펼쳐서 추이) | 검색 결과만 | 무료 공개 |
| S187 | [Feedly Emerging Trends 대시보드](https://docs.feedly.com/article/716-how-to-use-the-emerging-trends-tables) | AI 인사이트 | C06 | 성장률 임계값으로 단계 라벨(+1,000% 초과 = Exploding) → C06 급상승 키워드의 배수 구간별 라벨 기준을 화면에 명시 | 검색 결과만 | 확인 불가 |
| S188 | [BuzzSumo Trending 대시보드 · Content Analyzer](https://www.socialmediatoday.com/news/buzzsumo-adds-trending-content-feature/501918) | 기타 | C06 C03 | 트렌딩 점수 = 공유 속도 → C03 대표 글 선정에 '추천 수'만이 아니라 '짧은 시간 내 반응 속도'도 표시 | 검색 결과만 | 유료 |
| S190 | [Project Arctic Shift (레딧 데이터 덤프 · API · 웹 검색)](https://github.com/ArthurHeitmann/arctic_shift) | 오픈소스 대시보드 도구 | C07 | 서브레딧 과거 덤프 · API → 레딧 커뮤니티의 C07 평시(직전 8주) 기준선을 처음 만들 때 과거 글 수를 채우는 데이터원 | 열람 | 오픈소스 |
| S191 | [4CAT: Capture and Analysis Toolkit](https://github.com/digitalmethodsinitiative/4cat) | 오픈소스 대시보드 도구 | C07 C11 | 데이터셋 → 프로세서 연결(수집 조건과 처리 단계가 남는 구조) → C11 '방법 공개'에 수집 조건 · 처리 단계를 그대로 기록해 보여 주기 / CSV 업로드로 외부 수집 데이터 분석 → 커뮤니티별 수집기를 따로 두고 같은 분석 단계로 묶는 구조 | 열람 | 오픈소스 |
| S192 | [Statora (디스코드 서버 통계 봇 · 웹 대시보드)](https://top.gg/bot/1435801819078201494) | 게임 커뮤니티 분석 | C07 | 시간대 · 요일별 메시지 분해 → C07 글 수 지수에 요일 효과(주말 · 점검일) 보조 차트 | 검색 결과만 | 확인 불가 |
| S193 | [TGStat 채널 언급(Mentions) 모니터](https://databar.ai/explore/tgstat/telegram-channel-mentions) | 소셜 리스닝 | C03 | '다른 채널에서 인용된 횟수' → C03 이슈 근거에 '이 글 · 이슈가 다른 커뮤니티로 퍼졌는가'(교차 언급) 표시 | 검색 결과만 | 확인 불가 |
| S194 | [Tweet Binder — X 해시태그 · 키워드 리포트](https://home.tweetbinder.com/faqs) | 소셜 리스닝 | C10 C08 | 리포트 단위(기간 지정 → 총량 · 유형 · 감성 → PDF) → C10 주간 보고를 '기간 고정 스냅숏 + 내보내기'로 | 검색 결과만 | 유료 |
| S196 | [Meta Content Library 실시간 대시보드 (CrowdTangle 후속)](https://techcrunch.com/2024/08/15/meta-shut-down-crowdtangle-a-tool-for-tracking-disinformation-heres-how-its-replacement-compares) | 공개 대시보드 | C07 C03 | '게시물 피드 + 추세 차트'를 한 대시보드에 → C07 차트 옆에 같은 조건의 원문 피드를 나란히(차트만 보고 끝나지 않게) | 검색 결과만 | 로그인 필요 |
| S198 | [AllSides Headline Roundups (좌 · 중 · 우 헤드라인 나란히)](https://www.allsides.com/blog/how-allsides-creates-balanced-news-step-step-guide) | 공개 대시보드 | C03 | 같은 이슈를 진영별 헤드라인 3개로 나란히 + 순서 순환 → C03 '다른 커뮤니티의 같은 이슈' 대표 글을 커뮤니티별 1개씩 나란히, 특정 커뮤니티가 늘 첫 칸에 오지 않게 | 검색 결과만 | 확인 불가 |
| S201 | [pytrends (비공식 Google Trends API)](https://github.com/GeneralMills/pytrends) | 오픈소스 대시보드 도구 | C06 | related_queries(상승 검색어) 정기 수집 → C06 급상승 키워드 옆에 '외부 검색 관심도도 올랐는가' 보조 지표 | 열람 | 오픈소스 |
| S205 | [Silver Bulletin 지지율 · 폴링 평균 트래커](https://www.natesilver.net/p/silver-bulletin-polling-average-methodology) | 공개 대시보드 | C11 C07 | 조사기관별 정확도 등급으로 가중 평균 → C11 모델별 정확도를 근거로, 여러 분류 결과를 합칠 때 정확도 가중을 쓰고 그 규칙을 공개 / 단일 조사 대신 평균선 → C08 커뮤니티별 순감성 위에 '전체 가중 평균' 한 줄 | 검색 결과만 | 확인 불가 |
| S206 | [Gallup Presidential Job Approval Center](https://news.gallup.com/interactives/507569/presidential-job-approval-center.aspx) | 공개 대시보드 | C10 | '최대 4명 추이 겹쳐 비교' → C10 13주 추이에 '지난 대형 업데이트 시기' 같은 과거 구간을 최대 몇 개 겹쳐 비교 | 검색 결과만 | 확인 불가 |
| S210 | [네이버 데이터랩 (검색어 트렌드 · 쇼핑인사이트 · 댓글 통계)](https://inside.ampm.co.kr/insight/6773) | 국내 여론 · 트렌드 | C07 | 상대 추이(최대 = 100) 중심 표기 → C07 글 수 지수(평시 = 100) 표기 방식의 국내 사용자 친숙도 근거, 절대 글 수는 툴팁으로 | 검색 결과만 | 무료 공개 |
| S211 | [카카오 데이터트렌드](https://www.kakaocorp.com/page/detail/8806) | 국내 여론 · 트렌드 | C07 | 성별 · 연령 · 지역 분해를 한 화면에 → C07 글 수 지수를 커뮤니티 · 게시판별로 한 화면에 쪼개 보는 배치 | 검색 결과만 | 확인 불가 |
| S212 | [블랙키위 키워드 분석 (검색량 · 발행량 · 콘텐츠 포화 지수)](https://inside.ampm.co.kr/insight/9242) | 국내 여론 · 트렌드 | C06 | '검색량 대비 발행량'(콘텐츠 포화 지수) → C06 급상승 키워드에 '글 수 대비 추천 · 조회'처럼 관심 대비 글 공급 비율 보조 지표 | 검색 결과만 | 확인 불가 |
| S214 | [리스닝마인드 허블 — 패스파인더 · 인텐트파인더 · 저니파인더](https://docs.channel.io/lm-skills/ko/articles/pathfinder-report-c3423fef) | 국내 여론 · 트렌드 | C06 | '90일 동안 새로 생기거나 사라진 경로' → C06 급상승 키워드에 '새로 등장 · 사라짐' 표식(평시에 없던 키워드) | 검색 결과만 | 유료 |
| S216 | [국회도서관 AI 여론 분석 프로젝트 'M'AI Report'](https://aida.kisti.re.kr/data/7744e059-9e10-40b1-8ba9-85212a225f77/7cff2c22-2f6f-4d99-9a93-2029805b5f7a/01.발표자료.pdf) | 국내 여론 · 트렌드 | C08 C09 | '영상 내용 제외, 설명 데이터만 사용' 같은 데이터 범위 명시 → C11 방법 공개에 '제목만 분류, 본문은 6건만 정독' 같은 범위 한계를 같은 방식으로 적기 | 검색 결과만 | 확인 불가 |
| S221 | [SteamSpy 앱 페이지 (소유자 범위 · 태그 투표)](https://steamspy.com/app/453170) | 게임 시장 지표 | C06 | SteamSpy의 '추정치를 단일 숫자가 아닌 범위로' 표기 → C11 정확도 · C07 지수에서 표본이 적은 게시판은 값 대신 범위로 표시 / SteamSpy 'Tags over time'(태그별 시간 추이) 아이디어 → C06 급상승 키워드의 주별 추이 미니 차트 | 검색 결과만 | 무료 공개 |
| S222 | [Steam 250 랭킹 알고리즘 소개 (About)](https://steam250.com/about) | 게임 시장 지표 | C11 C02 | Steam 250의 '표 수와 비율을 함께 넣은 점수 + 가중치는 드물게만 바꾼다' 원칙 → C02 이슈 후보 점수에 글 수(규모)와 부정 비율(강도)을 함께 쓰고 가중치 변경 이력을 C11 방법 공개에 기록 | 검색 결과만 | 무료 공개 |
| S224 | [Gamalytic 추정 오차 연구 공개 (비교 글)](https://www.steampageanalyzer.com/blog/gamalytic-vs-vg-insights) | 게임 시장 지표 | C11 | Gamalytic의 '개별 추정 77%가 ±30%, 98%가 ±50%' 식 오차 분포 공개 → C11에 모델별 정확도를 한 숫자가 아니라 '주제 · 감성별로 몇 %가 맞았나' 분포로 | 검색 결과만 | 유료 |
| S227 | [Augmented Steam (VaporLens 통합 · 리뷰 정렬 · 필터)](https://github.com/IsThereAnyDeal/AugmentedSteam) | 오픈소스 대시보드 도구 | C11 | Augmented Steam의 'AI 기능 도입 후 사용자 반발' 사례 → C11 방법 공개에 AI가 쓰인 곳 · 안 쓰인 곳을 명시하고 C04 요약 블록에 'AI 생성' 표시와 원문 보기 경로를 고정 | 열람 | 오픈소스 |
| S228 | [TwitchTracker 게임 순위 · 게임별 통계](https://twitchtracker.com/games) | 게임 시장 지표 | G C07 | TwitchTracker 게임 페이지의 '주말은 평일 같은 시간대보다 200% 더 많다' 문장형 비교 → C07 글 수 지수에 요일 효과를 문장으로 덧붙여 평시 대비 상승이 요일 탓인지 구분 | 검색 결과만 | 무료 공개 |
| S229 | [SullyGnome (트위치 게임 통계 · 비교 · 월간 · 연간 리포트)](https://www.streamscheme.com/?p=15446) | 게임 시장 지표 | C10 G | SullyGnome의 '비교 도구 + 월간 · 연간 리포트' 구성 → C10 주간 보고에 직전 주 · 8주 평균 · 13주 전 비교 기준을 고를 수 있는 비교 표 | 검색 결과만 | 무료 공개 |
| S231 | [OpenCritic 게임 차트 페이지 (평균 · 추천 비율 · 백분위)](https://opencritic.com/game/13730/grounded/charts) | 게임 시장 지표 | C10 | OpenCritic의 '89th percentile' 백분위 표기 → C10 주간 보고에 이번 주 부정 비율이 지난 13주 중 몇 번째 백분위인지 함께 적어 평시 대비 위치를 직관적으로 | 검색 결과만 | 무료 공개 |
| S232 | [Metacritic 유저 점수 36시간 지연 (리뷰 폭격 대응)](https://videogameschronicle.com/news/metacritic-has-introduced-a-36-hour-delay-on-user-scores-following-review-bombing-campaigns) | 게임 커뮤니티 분석 | C02 | Metacritic의 '출시 직후 유저 점수 지연 · 플랫폼별 분리' → C02 이슈 후보에 '집단 행동(폭격) 가능성' 플래그를 두고, 소수 계정 · 짧은 시간 집중 여부를 AI 판단 이유에 표시 | 검색 결과만 | 무료 공개 |
| S233 | [로아와 (로스트아크 정보 · 통계 사이트)](https://www.breakflip.com/?p=67579) | 게임 커뮤니티 분석 | C09 | 로아와 직업군별 인구수 통계 → C09 VOC 주제 지도에서 '직업 밸런스' 주제의 부정 비율 옆에 해당 직업 인구 변화를 참고 지표로(인벤에서 인구 지표 신뢰성 논쟁이 있으므로 출처 · 기준 명시) | 검색 결과만 | 무료 공개 |
| S235 | [던담 (던파 딜 · 버프력 랭킹, 알고리즘 신뢰성 논쟁)](https://namu.moe/w/DUNDAM) | 게임 커뮤니티 분석 | C11 | 던담 '비공개 알고리즘 → 공신력 논쟁 → 유저 지적으로 수정' 사례 → C11 방법 공개에 분류 기준 · 프롬프트 요지 · 변경 이력(언제 무엇을 고쳤나)을 공개하고 오분류 제보 경로를 둠 | 검색 결과만 | 무료 공개 |
| S242 | [LLM 기반 VOC 자동 분류 및 Action Mapping 사례 연구](https://scholarworks.gnu.ac.kr/item/1ab26633-8b8e-42b3-9b2d-c21cfe1d845a) | 기타 | C02 | 'VOC 분류 → Action Mapping' 개념 → C02 AI 판단 초안의 '다음 행동'을 주제 × 의견 유형별 표준 조치 목록에서 고르게 해 판단을 일관되게 | 검색 결과만 | 무료 공개 |
| S244 | [Statbot (디스코드 서버 메시지 활동 대시보드)](https://peakbot.pro/blog/statbot-vs-serverstats-discord-analytics-bot-2026) | 게임 커뮤니티 분석 | C07 | Statbot의 '채널별 메시지 활동 일 · 주 · 월 전환 + 요일 × 시간 히트맵' → C07 글 수 지수의 게시판별 일별 · 주별 전환과 요일 × 시간대 히트맵(평시 패턴 대비) | 검색 결과만 | 무료 공개 |
| S245 | [Discord Server Insights](https://discord.com/community/understanding-server-insights) | 게임 커뮤니티 분석 | C07 | Server Insights의 '인기 텍스트 채널' 순위 → C07에 게시판별 글 수 지수를 순위 막대로 보여 이번 주 어느 게시판이 평시보다 붐볐는지 | 검색 결과만 | 로그인 필요 |
| S254 | [Solsten 핵심 지표 (플레이어 심리 대시보드 · 신뢰도 공개)](https://solsten.io/blog/understanding-solstens-core-metrics) | AI 인사이트 | C11 | Solsten의 '측정 신뢰도 범위(0.7~0.95, 평균 0.85)' 공개 → C11에 모델별 정확도의 범위와 평균을 함께, 주제별로 가장 낮은 값도 노출 | 검색 결과만 | 유료 |
| S259 | [Steam Reviews Scraper — Sentiment & Review-Bomb Detection (Apify)](https://apify.com/justfeel/steam-reviews-scraper) | 리뷰 분석 | C02 | 리뷰 폭격 탐지 기능 → C02 이슈 후보에 '짧은 시간 집중 · 신규 계정 비중' 같은 폭격 의심 표시 | 검색 결과만 | 유료 |
| S260 | [ClarityQ 게임 특화 AI 분석 (자연어 질의 · 게임 시맨틱 레이어)](https://www.pocketgamer.biz/clarityq-launches-game-native-ai-analytics-platform-for-mobile-game-studios/) | AI 인사이트 | C11 C10 | ClarityQ CEO의 '스튜디오마다 지표 정의가 흔들린다' 문제와 시맨틱 레이어 → C10 · C11에 '평시', '순감성', '이슈 후보' 정의를 한곳에 고정해 보고서마다 같은 정의를 쓰게 | 검색 결과만 | 유료 |
| S261 | [Helpshift Support Analytics (Power BI 앱)](https://appsource.microsoft.com/en-us/product/power-bi/helpshift.helpshift-support-analytics) | 게임 라이브 운영 | C07 | Helpshift 리포트의 '문의량 · 백로그 추이' → C07 글 수 지수 옆에 고객 문의량 추이를 같은 주 단위로 겹쳐 보는 보조 지표(가능할 경우) | 검색 결과만 | 유료 |
| S262 | [AccelByte Analytics Service (내장 대시보드)](https://docs.accelbyte.io/gaming-services/services/analytics) | 게임 라이브 운영 | G | AccelByte 내장 대시보드의 MAU · DAU · CCU 묶음 → G 게임 지표 카드에 스팀 동시 접속(CCU)과 PC방 지표를 한 줄로 묶는 배치 | 검색 결과만 | 유료 |
| S265 | [모바일인덱스 월간 인기 앱 · 게임 순위 리포트](https://www.fnnews.com/news/202501091414360663) | 국내 여론 · 트렌드 | G | 모바일인덱스 월간 MAU 순위 리포트 → G 게임 지표에 PC방 순위와 같은 '순위 + 이용자 수' 형식의 월간 요약 한 줄 | 검색 결과만 | 확인 불가 |
| S267 | [OP.GG OP Tier (승률 · 픽률 · 밴률 종합 티어, 패치 필터)](https://opgg.helpscoutdocs.com/article/311-op-tier) | 게임 커뮤니티 분석 | C10 | OP.GG의 '패치 버전 필터' → C10 · C08에서 '이번 업데이트 이후' 기간을 버전 단위로 고르는 필터 | 검색 결과만 | 무료 공개 |
| S273 | [Metabase (Metabot · 알림 · 대시보드 구독 · 문서 댓글)](https://raw.githubusercontent.com/metabase/metabase/master/README.md) | 오픈소스 대시보드 도구 | C10 | Metabase documents(장문 분석 + 댓글 초대) → C10 주간 보고를 문서형으로 내고 운영팀 댓글로 판단 보정 | 열람 | 오픈소스 |
| S274 | [Apache Superset](https://raw.githubusercontent.com/apache/superset/master/README.md) | 오픈소스 대시보드 도구 | C07 | Superset 시맨틱 레이어의 사용자 정의 지표 → C07 '글 수 지수(평시 = 100)'를 한 곳에서 정의해 커뮤니티 · 게시판별 차트가 같은 계산을 쓰도록 | 열람 | 오픈소스 |
| S275 | [Streamlit](https://raw.githubusercontent.com/streamlit/streamlit/master/README.md) | 오픈소스 대시보드 도구 | C10 | Streamlit의 '스크립트 → 웹 앱' 방식 → 주간 수집 · 분류 파이프라인 결과를 빠르게 내부 검수용 화면(C11 분류 샘플 검토)으로 띄우는 프로토타입 | 열람 | 오픈소스 |
| S276 | [Plotly Dash + Dash Gallery(dash-sample-apps)](https://dash.gallery) | 오픈소스 대시보드 도구 | C10 | Dash README의 'PDF 보고서처럼 꾸민 Financial report 앱' → C10 주간 보고 인쇄 화면을 대시보드와 같은 코드로 만들기 | 열람 | 오픈소스 |
| S277 | [Panel (HoloViz) 앱 갤러리](https://panel.holoviz.org/gallery/index.html) | 오픈소스 대시보드 도구 | C02 | Panel 갤러리 'Model serving monitor(응답 시간 · 드리프트 · 알림)' → C11 AI 분류 모델의 주간 정확도 드리프트 · 비용 경보 화면 | 열람 | 오픈소스 |
| S279 | [Redash (쿼리 · 대시보드 · 알림)](https://raw.githubusercontent.com/getredash/redash/master/README.md) | 오픈소스 대시보드 도구 | C02 | Redash의 '시각화와 그 쿼리를 같이 공유해 동료 검토' → C11 방법 공개: 지표 카드마다 집계 쿼리 링크 | 열람 | 오픈소스 |
| S280 | [Tremor (React 대시보드 컴포넌트, BadgeDelta)](https://tremor.so/) | 오픈소스 대시보드 도구 | C07 C08 | Tremor BadgeDelta의 5단계(강한 증가 · 증가 · 변화 없음 · 감소 · 강한 감소) → C08 순감성 지수 카드에 평시 대비 방향 배지를 단계로 표시 / Tremor NPM 예제의 '제목 + 큰 숫자 + AreaChart' 카드 → C07 커뮤니티별 글 수 지수 카드 | 열람 | 오픈소스 |
| S281 | [Grafana (시간 범위 비교 · 메트릭→로그 전환 · 알림)](https://raw.githubusercontent.com/grafana/grafana/main/README.md) | 오픈소스 대시보드 도구 | C03 | Grafana의 '라벨 필터를 유지한 채 메트릭 → 로그 전환' → C03 이슈 근거: 지표 칸을 누르면 같은 커뮤니티 · 주차 · 주제 필터로 원문 글 목록으로 이동 | 열람 | 오픈소스 |
| S282 | [Observable Framework 예제(쇼케이스 대시보드)](https://observablehq.com/framework/examples) | 오픈소스 대시보드 도구 | C07 | Observable 'plot' 예제의 '일별 값 + 7일 · 28일 이동평균' → C07 일별 글 수에 평시(8주) 기준선을 겹쳐 그리기 / 데이터 로더로 빌드 시 스냅샷을 만드는 구조 → 주간 배치 대시보드를 정적 페이지로 고정해 C10 주간 보고 재현성 확보 | 열람 | 오픈소스 |
| S285 | [US Airlines Sentiment Analysis (Streamlit)](https://github.com/prathameshThakur/Sentiment-Analysis) | 오픈소스 대시보드 도구 | C08 C03 | '항공사별 감성별 트윗 수' 비교 → C08 커뮤니티(인벤 · 아카라이브 · 공식 · 레딧)별 감성 비율 나란히 비교 / 사이드바에 감성별 실제 트윗 표시 → C03 대표 글을 감성 선택에 맞춰 바로 보여 주기 | 열람 | 오픈소스 |
| S287 | [Financial Times Visual Vocabulary](https://github.com/Financial-Times/chart-doctor/tree/main/visual-vocabulary) | 대시보드 디자인 갤러리 | C08 C07 | 'Deviation — 0 · 목표 · 장기 평균 대비 +/−, 감성(긍정 · 중립 · 부정)에도 사용' → C08 순감성 지수와 C07 지수를 '평시 = 100' 기준 diverging bar로 | 열람 | 무료 공개 |
| S288 | [IBM Carbon 데이터 시각화 — Dashboards 가이드](https://v10.carbondesignsystem.com/data-visualization/dashboards) | 대시보드 디자인 갤러리 | C01 C07 | Carbon '프레젠테이션 vs 탐색 대시보드' 구분 → 첫 화면(C01 · C02)은 프레젠테이션형, C09 · C07 상세는 탐색형 탭으로 분리 / '추세 · 고점 · 저점 주석' 가이드 → C07 · C08 추이 차트에 운영 공지 · 업데이트 날짜 주석 | 검색 결과만 | 무료 공개 |
| S289 | [Atlassian Design — Data visualization color](https://atlassian.design/foundations/color/data-visualization-color) | 대시보드 디자인 갤러리 | C09 | '범주 5~6색 제한 + 나머지 묶기' → C09 주제 지도의 주제 색을 상위 5~6개 + 기타로 제한 / 상태 토큰(caution · critical) → C02 이슈 수준 배지 색을 별도 토큰으로 고정하고 글자 라벨 병기 | 검색 결과만 | 무료 공개 |
| S290 | [Our World in Data Grapher / Explorer](https://github.com/owid/owid-grapher) | 공개 대시보드 | C07 C10 | Explorer(지표 · 차원을 드롭다운으로 바꾸는 한 화면) → C07 · C08을 '커뮤니티 · 지표 · 일별/주별' 선택형 한 차트로 통합 | 열람 | 무료 공개 |
| S293 | [지표누리 / e-나라지표](https://www.index.go.kr/unity/potal/eNara/sub/EnaraIntro.do) | 국내 여론 · 트렌드 | C01 C07 | 지표별 '그래프 + 통계표 + 의미분석' 3단 구성 → C07 · C08 지표 화면마다 차트 · 표 · 해설 한 줄을 고정 배치 | 검색 결과만 | 무료 공개 |
| S295 | [Mobbin (실제 앱 화면 라이브러리)](https://www.saasui.design/best-saas-dashboard-ui-inspiration) | 대시보드 디자인 갤러리 | C02 | 'UI 요소별 검색'으로 실제 SaaS의 알림 목록 · 이상 징후 카드 화면 모으기 → C02 이슈 후보 목록 레이아웃 비교 | 검색 결과만 | 로그인 필요 |
| S296 | [Dribbble — Insights · Peaks analysis 대시보드 샷](https://dribbble.com/FDM/shots) | 대시보드 디자인 갤러리 | C06 | 'Peaks analysis'(언급 급등 구간 분석) 화면 → C06 급상승 키워드 · C07 글 수 급등 주차를 피크 단위 카드로 | 검색 결과만 | 무료 공개 |
| S297 | [ReUI 대시보드 블록(stats · chart, shadcn 기반)](https://reui.io/blocks/application/chart/chart-2) | 대시보드 디자인 갤러리 | C07 C08 | ReUI Stats 1의 '증감 배지 + vs last month 한 줄' → C07 카드에 'vs 평시(8주 평균)' 문구를 고정 / Chart 2의 '큰 값 + 스파크라인 + 배지' → C08 커뮤니티별 순감성 카드 4개(인벤 · 아카라이브 · 공식 · 레딧) 한 줄 | 검색 결과만 | 오픈소스 |
| S298 | [Flourish Cards 템플릿 (KPI 카드 그리드)](https://helpcenter.flourish.studio/hc/en-us/articles/8761573940879-Cards-an-overview) | 대시보드 디자인 갤러리 | C10 | '큰 숫자 + 위 캡션 + 아래 보조 숫자 줄' 카드 → C10 주간 보고 첫 장의 숫자 카드(이번 주 값 · 평시 · 13주 최고) | 검색 결과만 | 로그인 필요 |
| S299 | [Power BI Data Stories — Online Sentiment Analysis](https://community.fabric.microsoft.com/t5/Data-Stories-Gallery/Online-Sentiment-Analysis/m-p/27680) | BI 갤러리 | C08 | '브랜드 모니터링 · 감성 · 트래픽' 8페이지 분할 → C07 글 수와 C08 감성을 별도 페이지로 두되 같은 필터 공유 | 검색 결과만 | 무료 공개 |
| S300 | [Power BI Data Stories — COVID-19 Sentiment Analysis](https://community.powerbi.com/t5/Data-Stories-Gallery/COVID-19-Sentiment-Analysis/m-p/1042410) | BI 갤러리 | C08 C11 | 외부 감성 API 점수(0~1) 사용 사례 → C11에 '감성 점수 출처(모델)'를 명시하는 칸 | 검색 결과만 | 무료 공개 |
| S301 | [ZoomCharts Power BI Dashboard for Review Analysis](https://www.zoomcharts.com/en/microsoft-power-bi-custom-visuals/dashboard-and-report-examples/view/power-bi-dashboard-for-review-analysis) | BI 갤러리 | C08 | '본문 감성 vs 제목 감성' 분리 점수 → C11에서 제목만 분류한 감성과 정독(본문) 감성의 차이를 비교 표시 | 검색 결과만 | 무료 공개 |
| S304 | [#WorkoutWednesday · KPI 타일 (BAN + 스파크라인 + 최고 · 최저 표시)](https://www.phdata.io/blog/adding-context-to-kpis-in-tableau/) | BI 갤러리 | C07 C10 | 'WINDOW_MAX/WINDOW_MIN 점만 표시' 스파크라인 → C10 13주 추이 스파크라인에 13주 최고 · 최저 주차만 점으로 표시 | 검색 결과만 | 무료 공개 |
| S306 | [LLM Pulse 무료 Looker Studio 템플릿 (순감성 −100~+100)](https://llmpulse.ai/blog/free-looker-studio-template-ai-llm-tracking/) | BI 갤러리 | C08 | '5단계 감성 + 순감성 −100~+100' 척도 → C08 순감성 지수 정의 · 축 범위 참고 | 검색 결과만 | 무료 공개 |
| S307 | [Tableau Exchange — Automated Narrative Insights (vPhrase)](https://exchange.tableau.com/products/280) | AI 인사이트 | C01 | 차트 옆 자동 서술 패널 → C01 결론을 해당 차트 바로 옆에 붙이는 배치 | 검색 결과만 | 유료 |
| S308 | [Holistics Canvas Dashboard — Period Comparison · KPI Metric](https://docs.holistics.io/docs/dashboard-period-comparison) | BI 갤러리 | C07 C10 | 대시보드 하나의 '비교 기준' 컨트롤이 모든 KPI에 적용 → C10 주간 보고에서 비교 기준(평시 8주 · 전주 · 4주 전)을 한 번에 바꾸기 | 검색 결과만 | 유료 |
| S319 | [Hex Threads (대화형 분석)](https://hex.tech/blog/introducing-threads/) | AI 인사이트 | C01 | '에이전트 단계 + 차트 캐러셀' 표시 → C04 정독 요약에서 AI가 읽은 6건 · 판단 단계를 순서대로 보여 주기 | 검색 결과만 | 유료 |
| S321 | [GoodData Key Driver Analysis](https://www.gooddata.com/docs/cloud/experimental-features/key-driver-analysis) | AI 인사이트 | C04 | '동인 분석 = 연관, 원인 확정은 별도' 구분 → C04 원인 가설에 '가설(연관)'과 '확인됨' 라벨을 나눠 신뢰도 표시 | 검색 결과만 | 유료 |

## 뺀 곳과 이유

- S004 [Power BI Data Stories Gallery](https://community.fabric.microsoft.com/t5/Power-BI-Updates-Blog/Share-inspiration-in-the-new-Data-Stories-Gallery-and-get-a-t/ba-p/5175167) — 공개 갤러리 자체만 확인됨, 우리 구성요소에 맞는 개별 화면 근거 없음
- S007 [Tableau Public 2024 visualization trends (KPI scorecards)](https://www.sellersdorsey.com/insights/health-data-visualization-resource-hub/tableau-public-2024-visualization-trends/) — 트렌드 리뷰 글, 구체 대시보드 화면 정보 없음
- S010 [Looker Studio Report / Template Gallery](https://docs.cloud.google.com/looker/docs/studio/create-a-report-from-a-template?authuser=0) — 데이터 소스별 템플릿 목록뿐, 우리 구성요소에 맞는 개별 화면 근거 없음
- S022 [Domo AI Chat](https://www.domo.com/ai/ai-chat) — 대화형 질의 기능으로 우리 구성요소에 맞는 화면이 없음
- S036 [Klipfolio Klip Gallery / Dashboard Gallery](https://support.klipfolio.com/hc/en-us/articles/215546308-Pre-built-Klips-and-the-Klip-Gallery) — 마케팅 · 영업 KPI 위젯 갤러리, 우리 구성요소에 맞는 화면 근거 없음
- S038 [Hex Magic / Notebook Agent vs Sigma 'explain this chart'](https://hex.tech/compare/sigma-vs-hex/) — 경쟁사 비교 마케팅 페이지, 대시보드 화면 정보 없음
- S044 [NN/g: Dashboards - Making Charts and Graphs Easier to Understand (preattentive)](https://www.nngroup.com/articles/dashboards-preattentive/) — 일반 디자인 원칙 글, 특정 대시보드 화면 없음
- S045 [GOV.UK Service Manual - performance metrics & service dashboards](https://www.gov.uk/service-manual/measuring-success/how-to-set-performance-metrics-for-your-service) — 지침 문서이며 공개 대시보드는 폐지됨, 화면 정보 없음
- S048 [XM Discover (formerly Clarabridge Studio)](https://www.qualtrics.com/articles/news/qualtrics-announces-discover/) — 출시 발표 기사, 대시보드 화면 정보 없음
- S050 [Ask Athena / Insights Assistant](https://medallia.com/platform/athena) — 질의응답형 기능으로 우리 구성요소에 맞는 화면이 없음
- S053 [Vizia command center](https://www.brandwatch.com/blog/launching-brandwatch-vizia/) — 벽면 상황판으로 우리 주간 대시보드와 무관, 오래된 출시 자료
- S067 [Canny Autopilot](https://platform.softwareone.com/product/canny/PCP-2063-3520) — 리셀러 소개 페이지, 대시보드 화면 정보 없음
- S072 [Yext review dashboard (AgencyAnalytics)](https://agencyanalytics.com/integrations/yext) — 통합 소개 페이지, 일반 리뷰 지표 나열뿐 구체 화면 없음
- S073 [Crisis Oracle / Narratives AI](https://www.newswire.com/view/content/pulsar-launches-crisis-oracle-to-help-brands-anticipate-reputational-22722470) — 보도자료, 대시보드 화면 정보 없음
- S075 [AI Sentinel](https://www.digimind.com/en/news/digimind-launches-ai-sentinel-and-releases-digimind-social-10.0) — 출시 뉴스 한 문장, 대시보드 화면 정보 없음
- S077 [Creativ game-publisher sentiment study (LLM)](https://www.tokenpost.kr/news/ai/253971) — 연구 결과 보도 기사, 대시보드 화면 없음
- S078 [썸트렌드 클라우드 AI 분석 / 썸트렌드 에어](https://www.mt.co.kr/article/2026030615341696439) — 보도 기사만, 화면 구성 확인 불가
- S081 [민원정보분석시스템 / 민원예보 / 한눈에 보는 민원 빅데이터](https://smartcity.go.kr/2022/03/31/국민권익위-한-해-2천만-건에-달하는-민원-빅데이터-분/) — 보도 기사, 대시보드는 계획 단계로 화면 정보 없음
- S084 [KT AI 기반 VOC 통합 포털](https://twig24.com/news/IT/2024/06/14/20240614020007) — 사내 시스템 보도 기사, 화면 정보 없음
- S085 [LG유플러스 VOC LAB](https://www.lg.co.kr/media/release/27264) — 사내 시스템 보도자료, 화면 정보 없음
- S086 [Engagement / Overview Dashboards](https://docs.gameanalytics.com/features/dashboards/engagement) — 자사 텔레메트리(DAU · 리텐션) 대시보드로 우리 구성요소와 무관
- S087 [Benchmarks (GameIntel)](https://docs.gameanalytics.com/gameintel/benchmarks/overview) — 텔레메트리 기반 수익 · 리텐션 벤치마크로 우리 구성요소와 무관
- S088 [Unity Analytics Dashboard (legacy)](https://docs.unity3d.com/2020.3/Documentation/Manual/UnityAnalyticsDashboard.html) — 구버전 텔레메트리 대시보드로 우리 구성요소와 무관
- S089 [Game Manager Trends](https://devdocs.xbox.com/services/playfab/data-analytics/learn-data/trends/trends-overview) — 텔레메트리 KPI 대시보드로 우리 구성요소와 무관
- S090 [Sales & Activation Reports - Wishlists](https://partner.steamgames.com/doc/marketing/wishlist/reporting) — 개발사용 판매 · 위시리스트 지표로 우리 구성요소와 무관
- S091 [Steam Discount History dashboard](https://respawn.outlookindia.com/gaming/gaming-news/valve-finally-opens-the-black-box-on-steam-sale-performance) — 판매 지표이며 뉴스로만 확인, 우리 구성요소와 무관
- S103 [Helpshift AI Agent Copilot / player analytics](https://www.keywordsstudios.com/en/ai-technology/ai-technology-products/helpshift/) — 상담원용 도구 소개, 대시보드 화면 정보 없음
- S104 [SentiSum for gaming](https://www.sentisum.com/industries/gaming) — voc-16과 같은 제품의 업종 마케팅 페이지, 화면 정보 추가 없음
- S105 [GDC 2024: How LiveOps Allows Games to Be Played as Intended, Always](https://gdcvault.com/play/1034436/How-LiveOps-Allows-Games-to) — 강연 소개만, 화면 정보 없음
- S107 [King at GDC18: AI anomaly detection for live ops (recap)](https://www.anodot.com/blog/quick-reflections-on-gdc18/) — 행사 후기 블로그, 화면 정보 없음
- S108 [Game Analytics Pipeline on AWS](https://aws.amazon.com/solutions/guidance/game-analytics-pipeline-on-aws/) — README에 대시보드 화면 설명 없음, 텔레메트리 파이프라인으로 우리 구성요소와 무관
- S109 [deltaDNA Benchmark Dashboard](https://www.pocketgamer.biz/retooled-deltadna-benchmark-dashboard) — 텔레메트리 수익 · 리텐션 벤치마크, 우리 구성요소와 무관
- S111 [AppMagic top charts (via GameDevReports recaps)](https://gamedevreports.substack.com/p/appmagic-top-mobile-games-by-revenue-119) — 모바일 매출 순위 뉴스레터, 우리 구성요소와 무관
- S113 [Game Health dashboards (Grafana Cloud)](https://docs.accelbyte.io/gaming-services/services/utilities/grafana-cloud-observability/game-health-dashboards) — 서버 · 서비스 상태 지표로 우리 구성요소와 무관
- S115 [게임트릭스 PC방 순위 (로스트아크 보도)](https://www.inews24.com/view/1314033) — 뉴스 기사, 게임트릭스 화면 자체 정보 없음
- S118 [인벤 자유게시판 토픽모델링 연구](https://www.koreascience.or.kr/article/CFKO202233649502421.pdf) — 학술 연구, 대시보드 화면 없음
- S119 [Mobile Game KPIs guide (metric bundles + diagnosis tree)](https://appfollow.io/blog/mobile-game-kpis) — 모바일 수익 KPI 가이드 글, 화면 없음 · 우리 구성요소와 무관
- S120 [로스트아크 업데이트 후 지표 발표](https://economist.co.kr/2022/07/13/it/general/20220713190007617.html) — 뉴스 기사, 화면 정보 없음
- S137 [Sensor Tower 리뷰 AI 분석](https://www.pocketgamer.biz/analytics-specialist-sensor-tower-are-producing-ai-driven-insights-reports) — 리뷰 분석 대시보드 화면 정보 없음(보도만). Sensor Tower Live Ops는 앞 조사에 있음
- S147 [UserVoice AI insights](https://australia.powerbi.microsoft.com/it-it/blog/monitor-and-visualize-your-uservoice-data-with-power-bi) — UserVoice 자체 대시보드 · AI 화면 정보 없음(마케팅 문구 · 타사 연동 블로그만)
- S159 [한국타이어 생성형 AI 기반 VOC 분석 시스템](https://www.hankooktire.com/global/en/company/media-list/media-detail.629492.html) — 보도자료만 있고 대시보드 화면 정보 없음
- S166 [AI Trend Analysis (Google Play 리뷰, 과제 저장소)](https://awesome.ecosyste.ms/projects/github.com%2Fsubha2414%2Fai-trend-analysis) — Pulsegen과 같은 과제의 미완성 버전, 대시보드 화면 없음(중복)
- S170 [devtodev AI-Powered Dashboard Insights](https://www.devtodev.com/resources/news/introducing-ai-powered-dashboard-insights) — 제목만 있어 판단 불가(게임 분석 도구라 후속 확인 권장)
- S177 [NetBase Quid (Quid Discover · Monitor · Predict)](https://trustradius.com/products/netbase-quid) — 리뷰 사이트 문장뿐이라 구체 화면 · AI 요약 방식을 판단할 근거가 없음
- S218 [타파크로스 (트렌드업 · KPR 인사이트 트리)](https://www.newswire.co.kr/newsRead.php?no=940350) — 보도자료 · 회사 소개뿐이라 대시보드 화면 정보가 없음('트루스토리' 제품은 확인 안 됨)
- S219 [펄스케이(Pulse-K)](https://brochure.konantech.com/wp-content/uploads/2024/04/회사소개서_e브로슈어_20240425.pdf) — 회사소개서 한 줄 소개뿐, 화면 · 기능 정보와 현재 운영 여부 확인 불가
- S225 [VG Insights (Video Game Insights)](https://lava.vginsights.com/about) — 검색 결과에 대시보드 화면 · 감성 기능 정보가 없음(판매 추정 도구 소개뿐)
- S230 [Esports Charts 시청자 통계 (언론 인용)](https://www.sheepesports.com/es/articles/valorant-masters-toronto-2025-final-peaks-at-1-104m-viewers/en) — e스포츠 대회 시청자 수 뉴스 인용뿐, 대시보드 화면 정보 없음 · VOC와 무관
- S234 [maple.gg (메이플스토리 랭킹 · 빌드 · 계산기)](https://www.exitlag.com/blog/maplestory-rankings-2/) — 캐릭터 랭킹 · 계산기 중심으로 VOC · 동향 대시보드 구성요소와 맞는 화면 정보 없음
- S237 [넥슨 인텔리전스랩스 (AI · 데이터 조직 소개)](https://biz.newdaily.co.kr/site/data/html/2024/01/04/2024010400173.html) — 커뮤니티 여론 · VOC 대시보드 정보 없음(조직 · 기술 소개 기사)
- S238 [넷마블 AI센터 · AI&Tech랩](https://news.bizwatch.co.kr/article/mobile/2025/09/12/0033) — VOC · 여론 대시보드 정보 없음(기업 AI 동향 기사)
- S239 [엔씨소프트 AI센터 연구 조직](https://nocutnews.co.kr/news/4939156) — VOC · 여론 분석 대시보드 정보 없음
- S241 [컴투스 Tableau 사례](https://www.tableau.com/ko-kr/solutions/customer/com2us-creating-new-rules-game-analysis-user-friendly-data) — VOC · 감성 화면 정보 없음(셀프서비스 분석 사례)
- S248 [Modulate ToxMod](https://www.stork.ai/ja/modulate-toxmod) — 공식 대시보드 · 리포트 정보 없음(저신뢰 집계 페이지뿐), 음성 모더레이션으로 범위도 다름
- S250 [Nakama Console (게임 서버 내장 웹 UI)](https://github.com/heroiclabs/nakama) — 게임 서버 운영 콘솔로 VOC · 커뮤니티 · 감성 화면이 없음
- S251 [Snowplow (게임 행동 데이터 파이프라인)](https://snowplow.io/games) — 데이터 수집 파이프라인이며 대시보드 화면이 없음(최신판은 오픈소스가 아닌 Limited Use License)
- S252 [Balancy (라이브옵스 · 수익화 플랫폼)](https://www.pocketgamer.biz/industry/balancy/) — 대시보드 화면 정보 없음(회사 소개 수준)
- S253 [Gamesight](https://www.cbinsights.com/company/player-xp/alternatives-competitors) — 마케팅 측정 회사로 감성 · VOC 대시보드 정보 없음
- S264 [Mixpanel Board Templates](https://docs.mixpanel.com/docs/boards/templates) — 게임 · 커뮤니티 VOC와 직접 맞는 템플릿 없음(범용 제품 분석 템플릿)
- S266 [한국콘텐츠진흥원 게임이용자 실태조사](https://www.kocca.kr/global/2023_11+12/sub06_01.html) — 연간 보고서(PDF)로 대시보드 화면 없음
- S294 [서울 열린데이터광장 시각화](https://data.seoul.go.kr/) — 검색 결과에 구체 대시보드 화면 구성이 없어 판단 불가
- S320 [Salesforce CRM Analytics (Einstein)](https://www.salesforce.com/products/crm-analytics/) — 마케팅 페이지뿐이고 대시보드 AI 요약 화면이 확인되지 않음(Einstein Discovery는 앞 조사와 중복)

중복으로 합친 항목:

- BERTopic (토픽 모델링 · 시간별 · 클래스별 토픽, LLM 라벨) (<https://github.com/MaartenGr/BERTopic>) → 'BERTopic (topics over time / per class / LLM representation)'와 같은 곳

## 열람 시도 기록

2026-10-31 ~ 11-01, 이 작업 환경(클라우드 세션)에서 시도한 결과.

| 시도 | 주소 | 결과 |
|---|---|---|
| WebFetch | https://www.geckoboard.com/dashboard-examples/ | 실패: getaddrinfo ENOTFOUND (세션 허용 도메인 밖) |
| WebFetch | https://docs.aws.amazon.com/quicksight/latest/user/gen-bi-executive-summaries.html | 실패: ENOTFOUND |
| WebFetch | https://www.tableau.com/viz-gallery | 실패: ENOTFOUND |
| WebFetch | https://steamdb.info/charts/ | 실패: ENOTFOUND |
| WebFetch | https://www.brandwatch.com/products/consumer-research/ | 실패: ENOTFOUND |
| curl | https://www.tableau.com, https://public.tableau.com, https://help.tableau.com, https://grafana.com, https://learn.microsoft.com, https://www.nngroup.com, https://steamcharts.com, https://en.wikipedia.org, https://cdn.jsdelivr.net, https://huggingface.co | 실패: 프록시가 연결 거부(connect_rejected) |
| curl | https://r.jina.ai/…, https://web.archive.org/… (읽기 중계 · 보관본) | 실패: 연결 거부 |
| curl | https://hyunxn-01.github.io/…, https://observablehq.github.io/, https://evidence-dev.github.io/ (GitHub Pages) | 실패: 연결 거부 |
| curl | https://api.github.com/repos/… | 403 |
| curl | **https://raw.githubusercontent.com/…** | **성공(200)** — 공개 GitHub 저장소 파일 읽기 가능 |
| curl | **https://pypi.org/project/…** | **성공(200)** |
| curl | https://registry.npmjs.org/… | 성공(200) — 패키지 정보만 |

정리: 라이브 대시보드 · 갤러리 · 제품 문서 사이트는 모두 막혔다. 열람은 GitHub 저장소 문서와 PyPI 페이지로 한정된다. 더 열어 보려면 세션 환경 설정의 Network access에서 허용 도메인을 추가해야 한다.

