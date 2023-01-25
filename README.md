# 고인물의 게임 추천(steam)

## :bell: Purpose

- 게임을 즐길 수 있는 시간이 유한한 게이머에게 본인의 취향에 맞는 게임 추천(ALS)

## 💾 Data(api)
- steam applist
- steam reviews 
## 💾 projcet 개요
![image](https://user-images.githubusercontent.com/88607278/214484062-178fd19c-1abb-4c4c-930a-845a63b5ad54.png)


## 📚 Tech Stacks
- Spark, Hadoop, MongoDB, 

## 환경설정
- GCP에서 4개의 인스턴스 생성 후 master 1대, worker 3대로 클러스터 구성
- 드라이버 : yarn
- zeppelin에서 모든 작업 진행


## 사용한 Steam API

### 1. 게임목록 확인(https://partner.steamgames.com/doc/webapi/ISteamApps)

- applist
    - apps- 응용 프로그램이 포함된 목록입니다.
        - appid- uint32 - 이 애플리케이션의 앱 ID입니다.
        - name- 문자열 - 이 애플리케이션의 이름입니다.


### 2. 게임리뷰(https://partner.steamgames.com/doc/store/getreviews)

- success- 쿼리가 성공한 경우 1
- query_summary- 첫 번째 요청에서 반환됨
    - num_reviews- 이 응답에서 반환된 리뷰 수
    - review_score- 리뷰 점수
    - review_score_desc- 리뷰 점수에 대한 설명
    - total_positive- 긍정적인 리뷰의 총 수
    - total_negative- 부정적인 리뷰의 총 수
    - total_reviews- 쿼리 매개변수와 일치하는 총 리뷰 수
- cursor- 리뷰의 다음 배치를 검색하기 위해 다음 요청에 전달할 값
- reviews
    - recommendationid - 추천 고유 ID
    - author
        - steamid - 사용자의 SteamID
        - num_games_owned - 사용자가 소유한 게임 수
        - num_reviews - 사용자가 작성한 리뷰 수
        - playtime_forever - 이 앱에서 평생 재생 시간 추적
        - playtime_last_two_weeks - 이 앱의 지난 2주 동안 추적된 플레이 시간
        - playtime_at_review- 리뷰 작성 시의 플레이 시간
        - last_played - 사용자가 마지막으로 플레이한 시간
    - language - 리뷰 작성 시 사용자가 표시한 언어
    - review - 서면 검토 텍스트
    - timestamp_created - 리뷰가 생성된 날짜(unix 타임스탬프)
    - timestamp_updated - 리뷰가 마지막으로 업데이트된 날짜(unix 타임스탬프)
    - voted_up - true 는 긍정적인 추천임을 의미합니다.
    - votes_up - 이 리뷰가 도움이 되었다고 생각하는 사용자 수
    - votes_funny - 이 리뷰가 재미있다고 생각한 사용자 수
    - weighted_vote_score - 유용성 점수
    - comment_count - 이 리뷰에 게시된 댓글 수
    - steam_purchase - 사용자가 Steam에서 게임을 구매한 경우 true
    - received_for_free - 사용자가 앱을 무료로 받았다는 상자를 선택한 경우 true
    - written_during_early_access - 게임이 앞서 해보기 상태일 때 사용자가 이 리뷰를 게시한 경우 true
    - developer_response- 개발자 응답 텍스트(있는 경우)
    - timestamp_dev_responded- 해당되는 경우 개발자가 응답한 Unix 타임스탬프
    

 ## 프로젝트에 대한 자세한 내용
 - [블로그](https://nothing-error.tistory.com/entry/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EA%B3%A0%EC%9D%B8%EB%AC%BC%EC%9D%98-%EC%8A%A4%ED%8C%80-%EA%B2%8C%EC%9E%84%EC%B6%94%EC%B2%9C-1%EA%B0%9C%EC%9A%94)
