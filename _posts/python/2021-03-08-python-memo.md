---

layout: post
current: post
cover:  assets/built/images/python-logo.png
navigation: True
title: Python - 나만의 메모장을 만들어보자.
date: 2020-03-07 20:20:00
tags: [python]
class: post-template
subclass: 'post tag-python'
author: Hono
---

#### <i class="fa fa-list-alt"></i> 나만의 메모장을 만들기

python을 이용해 기본적인 나만의 메모장을 만들어 보려 한다.

나는 컴퓨터로 공부하는 경우가 많기 때문에 메모장을 활용하는 경우가 많다.

그런데 몇 가지 기능이 있으면 조금 더 편리하게 사용할 수 있겠다는 생각을 해보았다.

------

1. 추가 버튼을 누르면 가족의 작성되었던 텍스트는 위로 저장되고 텍스트 창 초기화

2. 저장 버튼을 누르면 자동으로 파일명 그날 날짜로 저장

3. 삭제 버튼을 누르면 위에 저장되어 있던 내용 삭제

4. 프로그램 크기 수정 가능



이 정도로만 전체적인 프레임을 짜보고 만들어보자.

------

<i class="fa fa-pencil-square-o"></i> tkinter 라이브러리를 통하여 GUI 프로그램을 사용하자

1. 창 생성하기

~~~ python
from tkinter import *

win = Tk()
win.title("호노의 Memo")

win.mainloop
~~~

tkinter를 가져와서 이렇게 코드 작성하면 밑에 사진처럼 창이 뜰 것이다.

![창 생성하기](https://user-images.githubusercontent.com/79001968/111900949-a4c4c680-8a78-11eb-81c0-590f8c22855c.png)

------

<i class="fa fa-pencil-square-o"></i> 창이 이렇게 만들어졌으면 텍스트 창과 버튼을 넣을 것이다. 

아래 코드를 대충 설명을 하면 프레임을 사용함으로써 구역을 나눠서 사용할 것이다.

 지금은 1개의 프레임이라서 보이지는 않지만, 점차 프레임을 나눔으로써 위젯들의 배치를 보기 좋게 할 것이다

datetime 라이브러리를 가져와서 프레임 안에 라벨 위젯을 만들어주고 현재 날짜를 넣어줬다.

~~~ python
from tkinter import *
import datetime

date = datetime.date.today()

win = Tk()
win.title("호노의 Memo")
win.geometry("600x300")

# 제목 프레임
title_frame = Frame(win)
title_frame.pack()

date_text = Label(title_frame, text = date)
date_text.pack()

win.mainloop()
~~~



![날짜 생성](https://user-images.githubusercontent.com/79001968/111900923-82cb4400-8a78-11eb-8fa9-81ade54c36c0.png)

------

<i class="fa fa-pencil-square-o"></i> 버튼을 생성해주자 안에 첫 번째 버튼의 텍스트는 "저장"으로 하자. 

물론 이 저장 버튼은 클릭을 했을 눌리는 작동은 하지만 함수를 정의해 주지 않았기에 아무 기능이 없다.

~~~python
# 제목 프레임
title_frame = Frame(win)
title_frame.pack()

date_text = Label(title_frame, text = date)
date_text.pack()

button_save = Button(title_frame, padx=5, pady=5, width=12, text="저장")
button_save.pack(fill="both")
~~~



![저장 버튼](https://user-images.githubusercontent.com/79001968/111901476-d25f3f00-8a7b-11eb-86c8-cd4106d9361e.png)

------

<i class="fa fa-pencil-square-o"></i> 이제 여러 가지 위젯들을 하나씩 추가해보도록 하자.

 내용을 입력할 수 있는 텍스트 창과 이 텍스트 내용을 리스트에 추가하고 삭제할 수 있는 버튼도 같이 추가해줬다. 

- 프레임을 만들고 왼쪽에서부터 위젯을 순서대로 넣었다고 생각하면 된다. ( 코드는 위에서부터 입력이 되는 구조) 만약 본인이 원하는 위치가 있다면 코드의 줄을 바꾸어서 배치도 해보자.

~~~python
# 파일 프레임
file_frame = Frame(win)
file_frame.pack(padx=5,pady=5)

txt = Text(file_frame, width=50, heigh=3)
txt.pack(side="left", expand=True)
txt.insert(END, "내용을 입력하세요")

button_add = Button(file_frame, padx=5, pady=5, width=12, text="추가")
button_add.pack(side="left")

button_del = Button(file_frame, padx=5, pady=5, width=12, text="삭제")
button_del.pack(side="left")

~~~

![위젯 중간](https://user-images.githubusercontent.com/79001968/111905692-56232680-8a90-11eb-92d9-1d7d1c988759.png)

------

<i class="fa fa-pencil-square-o"></i> 이제 버튼들이 추가되었다면 리스트를 리스트 박스를 추가하도록 하자.

~~~python
#리스트 프레임
list_frame = Frame(win)
list_frame.pack(fill="both", padx=5, pady=5)

scrollbar = Scrollbar(list_frame)
scrollbar.pack(side = "right", fill="y")

list_file = Listbox(list_frame, selectmode="extended", height=15, yscrollcommand=scrollbar.set)
list_file.pack(side="left", fill="both", expand=True)
scrollbar.config(command=list_file.yview)
~~~

![리스트](https://user-images.githubusercontent.com/79001968/111910262-051d2d80-8aa4-11eb-992d-37898c961f30.png)

나는 여기서 리스트 박스가 중간에 가도록 하는 것이 편할 것 같아서 #제목 프레임과 #

파일 프레임 사이에 #리스트 박스를 코딩하였다.

이렇게 하면 이제 레이아웃은 다잡았다고 할 수 있다. 이제는 함수를 정의해주고 기능들을 구현해보도록 하자.

​	list_file - selectmode 파라미터에 대한 정보

- browse : 단일 선택, 방향키 이동 시 선택
- single : 단일 선택, 방향키 이동 후 스페이스바로 선택
- multiple : 다중 선택, 마우스 클릭이나 방향키 이동 후 스페이스바로 선택
- extended : 다중 선택, 마우스 드래그나 쉬프트키 + 방향키 이동으로 선택

------

<i class="fa fa-pencil-square-o"></i> 이제 함수를 정의해 보도록 하자.

~~~python
import tkinter.messagebox as msbox
~~~

~~~python
filename = str(date) + '.txt'
~~~

~~~python
def saveFile():
    file = open(filename, "w")
    ts = str(list_file.get(0, END))
    file.write(ts)
    file.close
    msbox.showinfo("알림", "정상적으로 저장되었습니다.")
~~~

~~~python
button_save = Button(title_frame, padx=5, pady=5, width=12, text="저장", command=saveFile)
button_save.pack(fill="both")
~~~

알림 기능을 사용하기 위해 messagebox를 import 해주자.

filename을 현재 시각으로 저장하기 위해 date 메소드를 사용하고 숫자 형이기에 str로 묶어준다. 이후 + .txt를 작성해주면 파일명이 20xx-xx-xx.txt로 저장이 된다.

이렇게 save File 함수를 정의해 준 뒤 원래 있던 button_save에 command=save File을 추가해주도록 하자.

이러면 이제 '저장' 버튼을 눌렀을 때 해당 날짜.txt 파일로 저장이 된다.

위에 함수에 대해서 간단하게 설명을 하자면

파일을 쓰기 상태로 생성을 한 뒤, 첫 번째 글자부터 마지막까지 파일을 str 형태로 변환 후 가져온다. (str를 사용하는 이유는 숫자의 형태도 함께 저장하기 위해)

생성한 파일에 가져온 텍스트를 작성하고 파일을 닫아줘야 파일이 저장되는 구조이다.

마지막으로 저장이 되었는지 확인을 하기 위해 messagebox를 이용해 알림 기능을 넣는다. 

![저장 창](https://user-images.githubusercontent.com/79001968/111911223-fa649780-8aa7-11eb-98bb-e1962561f08b.png)

 저장 버튼을 눌렀을 때 알림창

![파일 저장](https://user-images.githubusercontent.com/79001968/111911283-444d7d80-8aa8-11eb-8f58-c772d3d62ec4.png)

파일이 현재 날짜.txt 파일로 저장되는 것을 확인 할 수 있다. 

------

<i class="fa fa-pencil-square-o"></i> 이제 '추가','삭제' 버튼도 함수를 정의해 준 뒤 버튼에 커맨드를 해주면 된다.

~~~python
#함수 정의
def saveFile():
    file = open(filename, "w")
    ts = str(list_file.get(0, END))
    file.write(ts)
    file.close
    msbox.showinfo("알림", "정상적으로 저장되었습니다.")

def addList():
    index = txt.get("1.0", END)
    if index == '':
        return
    list_file.insert(END, txt.get("1.0", END))
    txt.delete("1.0", END)

def deleteList():
    index = list_file.curselection()
    list_file.delete(index)
~~~

~~~python
button_add = Button(file_frame, padx=5, pady=5, width=12, text="추가", command=addList)
button_add.pack(side="left")

button_del = Button(file_frame, padx=5, pady=5, width=12, text="삭제", command=deleteList)
button_del.pack(side="left")
~~~



------

<i class="fa fa-pencil-square-o"></i> 마지막 단계이다. 이 계산기 파일을 exe 파일로 만들어줄 것이다.

~~~python
pip install pyinstaller
~~~

~~~python
c:\myfolder>pyinstaller example.py
~~~

위의 명령어를 터미널에 입력하면 build, dist 파일과 example.spec이 생성된다.

여기서 dist 파일에 들어가면 example.exe 파일이 생성된 것을 확인 할 수 있다.

(주의할 점!) 파일저장 경로와 파일에 띄어쓰기가 있으면 오류가 난다. 혹시 파일명과 폴더명에 띄어쓰기가 있다면 수정하도록 하자.

![exe](https://user-images.githubusercontent.com/79001968/111913108-f8063b80-8aaf-11eb-9bd5-24e84febb674.png)

------

<i class="fa fa-smile-o"></i> 이로써 나만의 메모장 만들기를 마무리!

![마무리](https://user-images.githubusercontent.com/79001968/111913185-56331e80-8ab0-11eb-82a7-7c0740f98da3.png)

<script src="https://gist.github.com/HAN-Sang-Ho/f095afee62a7db69d0755b2b1fc93af6.js"></script>