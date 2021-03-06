
# CNN 모델, OpenCV, 자연어 처리를 활용한 신발 분류 및 태그 추천 MiniProject

## 프로젝트 설명
신발 사진을 찍으면 그 신발이 어느 카테고리("브랜드-품목")에 속하는지 판별, 예측해준다. 또한, 요즘 SNS에서 사진을 올릴 때 태그를 같이 추가해서 올리는 사용자들이 많아졌는데 이때 어떠한 태그를 추가할까 고민하는 과정을 단축해주기 위해 관련 태그를 추천해준다.

## 프로젝트 구조
> ## 데이터 수집 (크롤링)
- 신발 이미지
- 신발 리뷰
- 출처 : 무신사 홈페이지

> ## 신발 이미지 - 데이터 전처리 과정
https://colab.research.google.com/drive/1odmAwyhzv_0oPOZ74TIdTVHtSP8Ds6VH#scrollTo=hfTblMkXgjNx
- 카테고리("브랜드-품목") 지정
  - 나이키-Running, 반스-Canvas, 슈펜-Canvas, 아디다스-Running, 아식스-Running, 엑셀시오르-Canvas, 컨버스-Canvas, 프로스펙스-Running, 휠라-Running, Other-Sneakers
- 카테고리 선정 기준
  - 로고가 신발 외관에 있어 눈에 띄는가?, 해당 카테고리의 품목 개수가 150개 이상인가?
- 다리, 발목 등 신체의 일부가 포함되어있는 사진, 신발이 포함되어있지 않는 영수증 등의 사진으로 인해 예측 정확도가 낮았음
  - 신발이 포함 안 되어있는 사진은 수작업으로 삭제
  - OpenCV 라이브러리에 관해 책, 공식 docs를 통해 객체 탐지와 엣지 검출 방법에 관해 연구한 후, Canny Edge 검출 방법을 통해 신발의 위치 좌표를 찾아 직사각형으로 crop 한 뒤, 신발을 제외한 배경은 검은색으로 변화시킴
- 데이터의 개수가 다른 카테고리에 비해 적은 카테고리(예, 휠라-Running)와 데이터의 개수가 많은 카테고리(예, 반스-Canvas)로 인해 특정 카테고리로의 과적합 발생 가능성 존재
  - data augmentation, data 삭제를 통해 카테고리별 데이터의 개수를 맞춰줌

> ## 리뷰 데이터 - 자연어 처리
- 중복 데이터, 결측값, 특수기호, 이모티콘, 숫자 제거 (Pandas)
- 띄어쓰기, 맞춤법 교정 (Py-Hanspell)
- 토크나이저의 장단점, 한글의 품사 연구 후 원하는 단어의 어미, 쪼개진 정도에 알맞는 토크나이저 선정 (Okt)
- 불용어 제거
- 최대 문장 길이 한정
- 커스텀 단어 사전 만들기
- 태그 추출

> ## CNN 모델링

> ## 모델 검증 및 평가

## 개발 환경
Windows10

## 개발 언어
Python

## 개발 라이브러리
Tensorflow, Keras, OpenCV, Matplotlib, Pandas, Py-Hanspell, Mecab, Okt, BeautifulSoup, Selenium

## 개발 도구
Jupyter, Colab, Pycharm

## 사용 장비
NVIDIA GPU-RTX 2070
