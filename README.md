# 백준 문제 풀이와 커밋을 한번에 해주는 자동화 프로그램

이 코드는 일상의 어떤 행동을 자동화할 수 있는 지 고민하다가 나온 코드입니다.  
IT분야를 공부하는 사람이라면 매일 반복적으로 하는 행동이 있습니다.  
바로 '백준 문제 풀이'와 '깃허브 커밋'입니다.

크롤링과 ChatGPT를 하나로 묶어 자동화를 했습니다.

이 반복되는 행동을 자동으로 해주는 '자동화' 프로그램을 만들기로 했습니다.  
이 프로그램의 기능은 다음과 같습니다.  

## 기능 

(선택) 최초에 한번만 실행하면 됨.
+ DB에 백준 문제를 수집하고 저장함. [수집 범위: 문제 번호, 문제 이름, 내가 풀어서 맞았는지, 사람들이 도전해서 맞은 횟수]

(메인)
1. DB에서 풀이할 문제를 선정한다. 문제 선정의 기준은 사람들이 도전해서 맞은 횟수가 많으면서 내가 풀지 않은 문제입니다. 도전 횟수가 많은 순서로 SORTING되어 선정됩니다.
2. 문제 정보를 ChatGPT에 입력해서 솔루션을 얻습니다.
3. Baekjoon 사이트에 접속하여 로그인하고 문제를 제출하는 url로 접근합니다.
4. 얻은 Solution을 입력하고 제출합니다.
5. 체점동안 기다리며 체점이 끝나고 나면 결과를 확인합니다.
6. 5의 결과가 정답이면 DB정보를 수정하여 맞은 문제로 변경하고 오답이라면 2로 돌아가서 새로운 솔루션을 얻고 재제출 합니다.
7. 정답이라면 코드를 파일로 저장하고 Github 저장소에 Commit을 진행합니다.

아무튼 위와 같은 과정으로 버튼 한번으로 백준 문제풀이부터 제출, 깃헙 push까지 한방에 해줍니다.


## install

0. mysql을 설치하고 __baekjoon__ DB를 생성한다.
1. 필요한 모듈을 설치한다.
```
# cmd
>> pip install -r reruirements.txt
```
2. user_info.json 파일명을 info.json으로 변경하고 파일 속에 개인정보를 입력한다. 입력 정보는 다음과 같다.
	+ database root password
	+ 백준 ID와 password
	+ openai api key


## 실행법
cmd에 아래 명령어를 입력한다.
```
>> python main.py
```

