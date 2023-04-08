# DataAnalysis_Together
데이터 분석 팀 프로젝트 (팀 투게더)

1) 프로젝트 이름 및 개요

프로젝트 이름: 올해의 시즌컬러를 반영한 인기 십자수 도안 예측

개요: 십자수는 예전에 많이 하던 취미활동으로 인테리어를 할 때 많이 쓰이기도 했다. 하지만 요즘에는 실로 하는 십자수를 많이 하는 편은 아니다. 대신 보석 십자수, 핸드폰 개임 등으로 십자수가 다시 인기를 얻기 시작했다. 이렇게 다양한 방식으로 다시 떠오르는 십자수와 올해의 시즌 컬러를 합쳐 인기 십자수 도안을 예측할 것이다. 올해의 시즌컬러를 예측하고 그냥 도안에 넣는 것이 아닌 시즌 컬러와 어울리는 색조합 중에서도 사람들에게 인기 많은 색조합을 도안에 넣을 것이다. 전년도 기반으로 올해의 시즌컬러를 예측해서 시즌컬러가 들어간 도안을 넣었을 때 인기가 있을 것이라는 것을 예측하겠다.

2) 데이터베이스 구성

2-1) 개체-관계 다이어그램
  ![image](https://user-images.githubusercontent.com/92281591/230472307-e6ecf60a-d6aa-4aea-88b4-bfbf7f7672ec.png)

2-2) 릴레이션 스키마

도안 릴레이션

|도안번호|도안이름|카테고리|
|:---:|:---:|:---:|

실 릴레이션

|실번호|실이름|실헥스코드|도안번호|색조합표번호|
|:---:|:---:|:---:|:---:|:---:|

색조합표 릴레이션

|색조합표 번호|헥스코드1|헥스코드2|헥스코드3|헥스코드4|좋아요수|시즌컬러 색이름|실번호|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|

시즌컬러 릴레이션

|시즌컬러 색 이름|시즌컬러 년도|시즌컬러 헥스코드|시즌컬러 색|시즌컬러 연상언어|팬톤 번호|
|:---:|:---:|:---:|:---:|:---:|:---:|

팬톤 릴레이션

|팬톤 번호|팬톤 년도|분기|도시|팬톤 색이름|팬톤 헥스코드|컬러버전|팬톤 색|팬톤 연상언어|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|

3) 데이터 분석  
3-1) 데이터 시각화 
-역대 시즌 컬러 주기 그래프

![image](https://user-images.githubusercontent.com/92281591/230476442-2391029d-2009-44a9-9cd2-5e31a1b1fa51.png)

 
역대 시즌 컬러의 주기를 표현한 R 그래프이다. Y축은 스펙트럼의 색을 글로 표현한 것이고, y축은 년도를 나타냈다. 역대 시즌 컬러들의 데이터를 한눈에 볼 수 있게 하면서 한 색깔의 주기가 어느정도 되는 지 한눈에 알아볼 수 있다. 

-23년도 예상 시즌컬러 시각화

![image](https://user-images.githubusercontent.com/92281591/230476477-43d25dc2-4589-4e18-a851-32e7e53db42d.png)
 
위 그래프는 2023년도의 예상 시즌 컬러의 색을 보여주기 위해 그래프로 나타내었다. 헥스코드나 이름으로 만 쓰는 것을 색을 알아볼 수 없다고 생각하여 예측한 23년도 시즌컬러를 시각화 한 것이다.

-23년도 예상 시즌 컬러 중 Waterspout의 인기 색조합 5개
 
 
 ![image](https://user-images.githubusercontent.com/92281591/230476503-47ef0a8c-9442-4d86-910e-1578dee0b7d2.png)


예상한 23년도 시즌 컬러중 하나인 Waterspout의 인기 색조합 상위5개의 색조합 그래프이다. x축은 막대에 표현한 색의 헥스코드를 위에서부터 차례대로 쓴 것이다. y축은 각 색조합의 사람들의 좋아요 수를 나타낸 것이다. 전체적으로 각 색조합의 색을 비교하면서 어떤 색조합이 인기가 많은 지 한 눈에 알아볼 수 있게 만들었다.

-23년도 예상 시즌 컬러 중 Poppy Seed의 인기 색조합 5개

![image](https://user-images.githubusercontent.com/92281591/230476549-fcff2b29-111d-4455-8a29-bb95f99da2a3.png)

 
예상한 23년도 시즌 컬러중 하나인 Poppy Seed의 인기 색조합 상위5개의 색조합 그래프이다. x축은 막대에 표현한 색의 헥스코드를 위에서부터 차례대로 쓴 것이다. y축은 각 색조합의 사람들의 좋아요 수를 나타낸 것이다. 전체적으로 각 색조합의 색을 비교하면서 어떤 색조합이 인기가 많은 지 한 눈에 알아볼 수 있게 만들었다.


3-2) 예측 모델 결정 

1.R시각화 그래프, 예측모델: 23년도 시즌 컬러(Poppy Seed, Waterspout) 
  예상한 시즌 컬러의 색을 표현하는 것은 그래프로 충분히 가능하다고 생각되어서 R을 그대로 쓰기로 결정했다. 예상 시즌 컬러를 글로 헥스코드만 쓰기에는 이전 컬러들과 비교하기도 어렵다고 생각되어서 R로 시각화 해줄 것이다.

2.웹, 예측모델: 인기 색조합과 도안
  도안과 색조합을 표현하는 데 웹을 선택한 이유는 웹이 가장 도안의 느낌을 표현하기 괜찮다고 생각했다. 도안과 시즌컬러의 색조합표를 보여주기에 R과 같이 그래프 같은 것으로 표현하기가 어렵다고 생각되어 웹으로 예시 도안과 그것에 어울릴 만한 색조합표들을 보여줄 것이다. 
  

3-3) 검증 방법론 

-21년도 시즌 컬러를 통해서 23년도 시즌컬러를 검증할 것이다.

-ColorHunt 라는 색조합표 사이트에서 6년전부터 최근5월 24일까지의 사람들의 좋아요수가 누적되어있다. colorhunt라는 사이트의 색조합들과 각 색의 헥스코드 그리고 사람들의 좋아요수의 데이터들을 정보로 만들었다. 여기서 예측한 23년도 시즌 컬러를 ColorHunt에서 검색해서 좋아요수가 높은 순서대로 나열을 했다. 그리고 나열한 시즌컬러의 색조합들을 도안과 합쳐서 인기도안이라는 것을 검증할 것이다.

4) 결과

4-1) 예측 모델 검증 결과

21년도 시즌컬러를 예측하여 23년도의 정확성을 증명하였다
런던과 뉴욕의 봄여름과 가을겨울의 시즌컬러 후보들의 색의 상징과 헥스코드를 넣어서 R에서 만든 시즌컬러주기를 보고 다음에 나올 색을 예측하였다. mysql에서 색을 입력하여 그 색들의 상징성들을 보고 그 당시의 사회성을 반영해서 21년도 시즌컬러를 뽑았다. 그리고 실제 21년도의 컬러를 확인해보니 결과가 똑같이 나왔다.

4-2) 최종 결과물 

-R최종 결과물

 ![image](https://user-images.githubusercontent.com/92281591/230477033-b507c8a7-c12e-4e4c-8a11-eca04ae67fbf.png)


R script를 실행시키면 역대 시즌 컬러의 주기를 볼 수 있고 그 옆에 23년도 시즌 컬러를 표현해서 주기에 들어갔을 때를 비교해 볼 수 있도록 하였다. 그리고 밑에는 예상 23년도 시즌 컬러인 waterspout와 poppy seed의 인기 색조합들을 가가 표현해 주었다. 각 컬러마다 인기의 정도와 어떤 조합인지를 한 눈에 알아볼 수 있다.

-웹 최종 결과물

 ![image](https://user-images.githubusercontent.com/92281591/230477075-fed13fab-8190-4e40-aa8a-322c1e28b415.png)


웹사이트 화면에서 도안목록에서 자신이 원하는 종류의 도안을 선택하면 선택한 종류에 맞게 예시 도안과 도안에 어울리는 색조합들이 나오게 하였다. 색조합은 예시도안에 한정적으로 한 것이 아닌 그 카테고리에 어울리는 색으로 뽑은 것이다.

4-3) 토의

-올해의 시즌컬러를 추가하기로 결정함

초반에는 색조합표, 실색만 써서 도안과 섞어 웹 페이지를 제작하려 했으나, 상의를 거쳐 올해의 시즌 컬러까지 데이터가 추가로 필요하게 되었다. 올해의 시즌 컬러를 추가로 입수하기로 하였다.

-22년도 시즌컬러의 변수

22년도 시즌 컬러인 베리페리가 팬톤이 자체적으로 만든 컬러라는 변수가 생겼다. 따라서 22년도가 아닌 21년도로 23년도를 검증을 하게되었다.

-사회성을 코드로 표현하기 어려움

올해의 시즌컬러를 정하는 법 : 색상의10년주기, 런던 뉴욕 컬러, 사회성
주기나 컬러 분류는 R로 만들 수 있었지만 사회성은 코드로 표현 넣기 어려웠다. (23년도 예시: 우크라이나 전쟁, 코로나 해방) 따라서 사회성을 자체적으로 판단했다.

datafile) 예측 모델 훈련시 사용된 데이터와 검증시 사용한 데이터 
 - 형식은 csv or 엑셀 or SQL문

<검증시 사용한 데이터>
-(2021.csv)
-2021 예상 컬러색 뽑기 

    SELECT * FROM ds_color.seasoncolor;
    SELECT colorname,Hexcode,color, SYMBOL FROM ds_color.rn2021
    WHERE color ='YELLOW' OR color='GRAY'

-2021 팬톤(뉴욕, 런던) 겹치는 컬러

    SELECT colorname,hexcode,cv, SYMBOL, COUNT(Hexcode),count(colorname),count(cv) FROM ds_color.rn2021
    GROUP BY Hexcode
    HAVING COUNT(Hexcode) > 1;

<훈련시 사용된 데이터>

-(2023.csv)

-2023 예상 컬러색 뽑기 

    SELECT * FROM ds_color.seasoncolor;
    SELECT colorname,Hexcode,color, SYMBOL FROM ds_color.rn2223
    WHERE color ='BLUE' OR color='GRAY'

-2023 팬톤(뉴욕, 런던) 겹치는 컬러

    SELECT colorname,Hexcode,cv, SYMBOL, COUNT(Hexcode),count(colorname),count(cv) FROM ds_color.rn2223
    GROUP BY Hexcode
    HAVING COUNT(Hexcode) > 1;

첨부 1) 데이터베이스 구성에 사용된 SQL 소스 코드

<R에 쓰인 mysql 코드>

-2023년도 시즌 컬러

    RN23 <- dbGetQuery( ds_color,
                        "SELECT colorname,Hexcode,cv, COUNT(Hexcode),count(colorname),count(cv) FROM ds_color.RN2223
    GROUP BY Hexcode
    HAVING COUNT(Hexcode) > 1")


-2023년 시즌 컬러 Poppy Seed의 색조합 좋아요순 상위 5개

    Like58575C <- dbGetQuery( ds_color,
                              "SELECT HexCol1, HexCol2, HexCol3, HexCol4, Popular FROM ds_color.likecolor 
    WHERE HexCol1 = '58575C' OR HexCol2 = '58575C' OR HexCol3 = '58575C' OR HexCol4 = '58575C' 
    ORDER BY Popular  DESC limit 5")


-2023년 시즌 컬러 Waterspout의 색조합 좋아요순 상위 5개

    Like7AD1D8 <- dbGetQuery( ds_color,
                              "SELECT HexCol1, HexCol2, HexCol3, HexCol4, Popular FROM ds_color.likecolor 
    WHERE HexCol1 = '7AD1D8' OR HexCol2 = '7AD1D8' OR HexCol3 = '7AD1D8' OR HexCol4 = '7AD1D8' 
    ORDER BY Popular  DESC limit 5")

