### 01. 개요

---

- 머니볼이란 영화를 아시나요 🙂? 아직이시라면, 장차 데이터 분석가로 취업을 하고 커리어를 이어 가실 예정이시라면 더더욱 보시길 추천드립니다.  '머니볼'은 전통적인 직관과 경험에 의존하던 야구계에 데이터 분석을 도입하여 성공을 거둔 사례를 보여주기 때문입니다. 이는 데이터 기반 의사결정의 힘을 잘 보여주는 예시입니다.
    
### 02. 배경

---

- ‘농구’ 라는 스포츠에서 머니볼과 같이 직관과 경험에 의존하는게 아닌 → 데이터에 근거한 의사결정 방식을 도입하고자 합니다.
- 이제 여러분은 NBA 경기 데이터를 심층 분석하여 팀 성과에 영향을 미치는 주요 요인을 파악하고, 선수의 기여도를 정량적으로 평가하여, 팀을 우승 시키기 위해 선수 영입/방출 전략을 세우는 전력분석팀 소속의 데이터 분석가가 되어보겠습니다.

### 03. 주제

---

- 탐색적 데이터 분석을 통하여(EDA) 농구란 스포츠에서 승리를 가져오기 위한 핵심 지표 선정과 근거를 제시해주세요.
- 이를 기반으로 NBA 팀 중, 하나의 팀을 선정하여(중복선택 가능), 핵심 성과지표(KPI)를 정의하여 선수 영입/방출 전략을 세워주세요.
- 데이터 EDA(Exploratory Data Analysis) 는 탐색적 데이터 분석을 의미합니다.
- EDA 는 크게 **이상치/결측치** 처리 및 **시각화** 로 나뉩니다.
- EDA 프로세스
 

### 04. 설명

---

- Game_Detail 테이블 컬럼 설명
    
    ```jsx
    FGM (Field Goals Made): 성공한 필드골 개수
    FGA (Field Goals Attempted): 시도한 필드골 개수
    FG_PCT (Field Goal Percentage): 필드골 성공률 (FGM/FGA)
    FG3M (3-Point Field Goals Made): 성공한 3점슛 개수
    FG3A (3-Point Field Goals Attempted): 시도한 3점슛 개수
    FG3_PCT (3-Point Field Goal Percentage): 3점슛 성공률 (FG3M/FG3A)
    FTM (Free Throws Made): 성공한 자유투 개수
    FTA (Free Throws Attempted): 시도한 자유투 개수
    FT_PCT (Free Throw Percentage): 자유투 성공률 (FTM/FTA)
    OREB (Offensive Rebounds): 공격 리바운드 개수
    DREB (Defensive Rebounds): 수비 리바운드 개수
    REB (Total Rebounds): 전체 리바운드 개수 (OREB + DREB)
    AST (Assists): 어시스트 개수
    STL (Steals): 스틸 개수
    BLK (Blocks): 블록 개수
    TO (Turnovers): 턴오버 개수
    PF (Personal Fouls): 개인 파울 개수
    PTS (Points): 득점
    PLUS_MINUS: 플러스/마이너스 (선수가 코트에 있는 동안 팀의 득실점 차이)
    ```
    
- TEAM 테이블 컬럼 설명
    
    ```jsx
    TEAM_ID: 팀의 고유 식별 번호
    MIN_YEAR: 팀의 기록이 시작된 최초 연도
    MAX_YEAR: 팀의 가장 최근 기록이 있는 연도
    ABBREVIATION: 팀의 약자 (예: LAL for Los Angeles Lakers)
    NICKNAME: 팀의 별명 (예: Lakers, Warriors, Celtics 등)
    YEARFOUNDED: 팀이 창립된 연도
    CITY: 팀의 연고지 도시
    ARENA: 팀의 홈 경기장 이름
    ARENACAPACITY: 경기장의 최대 수용 인원
    OWNER: 팀의 소유주 또는 소유 그룹
    GENERALMANAGER: 팀의 단장 (General Manager)
    HEADCOACH: 팀의 감독 (Head Coach)
    DLEAGUEAFFILIATION: NBA G 리그(이전의 D-리그) 제휴 팀 이름
    ```
    
- RANKING 테이블 컬럼 설명
    
    ```jsx
    TEAM_ID: 팀의 고유 식별 번호
    LEAGUE_ID: 리그의 고유 식별 번호 (NBA의 경우 보통 00)
    SEASON_ID: 해당 시즌의 식별자 (예: "2022-23")
    STANDINGSDATE: 이 순위 정보가 기록된 날짜
    CONFERENCE: 팀이 속한 컨퍼런스 (동부 또는 서부)
    TEAM: 팀 이름
    G (Games): 플레이한 경기 수
    W (Wins): 승리 수
    L (Losses): 패배 수
    W_PCT (Win Percentage): 승률 (승리 수 / 경기 수)
    HOME_RECORD: 홈경기 성적 (승-패)
    ROAD_RECORD: 원정경기 성적 (승-패)
    RETURNTOPLAY: 리그 중단 후 복귀 여부를 나타내는 지표 (주로 COVID-19 팬데믹 관련)
    ```
    
- GAME
    
    ```jsx
    GAME_DATE_EST: 경기 날짜 (동부 표준시 기준)
    GAME_ID: 각 경기의 고유 식별 번호
    GAME_STATUS_TEXT: 경기 상태 (예: 예정됨, 진행 중, 종료 등)
    HOME_TEAM_ID: 홈 팀의 식별 번호
    VISITOR_TEAM_ID: 원정 팀의 식별 번호
    SEASON: 해당 시즌 (예: "2022-23")
    TEAM_ID_home: 홈 팀의 식별 번호 (HOME_TEAM_ID와 동일)
    PTS_home: 홈 팀 득점
    FG_PCT_home: 홈 팀 필드골 성공률
    FT_PCT_home: 홈 팀 자유투 성공률
    FG3_PCT_home: 홈 팀 3점슛 성공률
    AST_home: 홈 팀 어시스트 개수
    REB_home: 홈 팀 리바운드 개수
    TEAM_ID_away: 원정 팀의 식별 번호 (VISITOR_TEAM_ID와 동일)
    PTS_away: 원정 팀 득점
    FG_PCT_away: 원정 팀 필드골 성공률
    FT_PCT_away: 원정 팀 자유투 성공률
    FG3_PCT_away: 원정 팀 3점슛 성공률
    AST_away: 원정 팀 어시스트 개수
    REB_away: 원정 팀 리바운드 개수
    HOME_TEAM_WINS: 홈 팀 승리 여부 (1은 홈 팀 승리, 0은 패배)
    ```
    

### 05. 데이터 예시

---

- 데이터 다운로드

    [nba_dataset.zip](https://prod-files-secure.s3.us-west-2.amazonaws.com/83c75a39-3aba-4ba4-a792-7aefe4b07895/24137193-a43d-44fe-8cfe-c6cfec184dac/nba_dataset.zip)
    
- 데이터 출처
    - https://www.kaggle.com/datasets/nathanlauga/nba-games/data
- 아래는 테이블 구성입니다.