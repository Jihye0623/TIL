
# 불용어 전처리
1. 원본 텍스트 입력
2. 원본 텍스트에서 "."을 기준으로 나눈 리스트 제작
3. 리스트의 문장들을 soynlp의 only_hangle로 한글만 추출
4. 형태소 분석기를 이용해 리스트로 형태소만 반환
5. 불용어 사전으로 필터링하여 필요한 형태소만 남긴 리스트 반환
6. 빈 문자열, 중복된 단어 제거하고 한 문장으로 만들기

<br/>



<br/>
<br/>
<br/>

**입력 문자**<br/><br/>
아이쿠 감기에 걸렸습니다. 컨디션이 매우 Bad합니다... 겨우 9월이 되었을뿐인데 이곳 저곳 다니다보니 감기에 걸렸나봅니다. 구체적으로 말하자면 땀이 주룩주룩나기 시작합니다. 구토를 할지언정 오로지 한이음에 집중하도록 하겠습니다.

<br/>

**출력**

['감기 걸렸습니다 컨디션 매우 합니다 ', '되었을 뿐 인데 곳 다니다 보니 감기 걸렸 봅니다 ', '구체 하자면 땀 나기 시작 합니다 ', '구토 한이음 집중 하도록 하겠습니다’]

<br/><br/>
---

```
!pip install soynlp
!pip install konlpy
```

```
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from soynlp.normalizer import *
from konlpy.tag import Okt

stop_words="..."
input_text="아이쿠 감기에 걸렸습니다! 컨디션이 매우 Bad합니다... 겨우 9월이 되었을뿐인데 이곳 저곳 다니다보니 감기에 걸렸봅니다. 구체적으로 말하자면 땀이 주룩주룩나기 시작합니다. 구토를 할지언정 오로지 한이음에 집중하도록 하겠습니다."


input_text = input_text.split('.')

text_list = []

for i in input_text:
  i = only_hangle(i)
  text_list.append(i)


okt = Okt()

text_result = []

for t in text_list:
  t=okt.morphs(t)
  text_result.append(t)

filtering = []

for result in text_result:
  f=[]
  for res in result:
    if res not in stop_words:
        f.append(res)
  filtering.append(f)

print(filtering)

```
