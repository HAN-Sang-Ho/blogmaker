---

layout: post
current: post
cover:  assets/built/images/python-logo.png
navigation: True
title: Python - Crawling.
date: 2020-03-07 20:20:00
tags: [python]
class: post-template
subclass: 'post tag-python'
author: Hono
---

#### <i class="fa fa-list-alt"></i> Crawling

python을 이용해 크롤링 코드를 작성해 보려한다.

크롤링은 업무자동화의 기본이라고도 할 수 있는데

크롤링이란 분산되어 있는 문서에서 데이터를 검색하여 필요한 정보를 색인하는 기술이다.

이 색인하는 과정을 사람이 하는 것이 아니라 컴퓨터가 대신해주는 것이다.

간단한 코드만으로도 여러가지 일을 할 수 있다.

------

예를 들면 뉴스기사의 메인제목, 로또번호, 실시간 검색어 등등 자신에게 필요한 정보를 편하게 볼 수 있는 편리한 기능이다. 

대표적으로 호텔스컴바인,호텔스닷컴 등이 실제 사업에서 사용되는 기술이라고 볼 수 있다.

------

<i class="fa fa-pencil-square-o"></i> 나는 머신러닝 이미지인식 프로그램을 만드는 과정에서 이미지 데이터세트가 필요해서 연예인들의 사진을 크롤링 하는 코드를 작성해보려한다. 

![selenium](https://user-images.githubusercontent.com/79001968/113678186-54e13300-96f9-11eb-8557-3516aebea5b6.png)

크롤링을 하기 위해 Selenium을 사용할 것이다.

Selenium은 크롤링 외에도 메일을 보내는 등의 웹브라우저로 하는 기능을 구현할 수있다.

~~~ python
pip install selenium
~~~

우선 selenium을 설치해주자.

------

<i class="fa fa-pencil-square-o"></i>  설치를 완료하였다면 크롬에서 이미지를 가져올 것이기 때문에 ChromeDriver을 다운받아야한다.

![버전](https://user-images.githubusercontent.com/79001968/113679440-b8b82b80-96fa-11eb-9b32-a06560692d9d.png)

ChromeDriver을 다운받기 위해서는 Chrome의 버전을 확인해야하는데 이렇게 도움말에 Chrome 정보에서 확인하면된다.

![2](https://user-images.githubusercontent.com/79001968/114042346-4e50e800-98c0-11eb-9669-c84c26c51277.png)

ChromeDriver에서 본인의 컴퓨터에 맞는것을 찾아 다운 받으면 된다.

다운 받은 파일은 작성한 코딩을 저장할 폴더에 받으면 된다.(google.py와 같은 경로에 있어야함) 

------

~~~ python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

driver = webdriver.Firefox()
driver.get("http://www.python.org")
assert "Python" in driver.title
elem = driver.find_element_by_name("q")
elem.clear()
elem.send_keys("pycon")
elem.send_keys(Keys.RETURN)
assert "No results found." not in driver.page_source
driver.close()
~~~

셀레니움 공식 홈페이지에 있는 코드를 가져다 사용할 것이다.

출처 : https://selenium-python.readthedocs.io/getting-started.html

------

~~~python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

driver = webdriver.Chrome()
driver.get("http://www.python.org")
#assert "Python" in driver.title
#elem = driver.find_element_by_name("q")
#elem.clear()
#elem.send_keys("pycon")
#elem.send_keys(Keys.RETURN)
#assert "No results found." not in driver.page_source
#driver.close()
~~~

이렇게 위에 4줄을 남기고 우리는 Chrome을 사용할 것이니 웹드라이버를 Firefox()에서 Chrome()으로 바꾸어 주자.

![3](https://user-images.githubusercontent.com/79001968/114044395-2b273800-98c2-11eb-84b4-4f6bae6dfe5b.png)

python을 Run 해보면 이렇게 python페이지가 나오는 것을 볼 수 있다.

------

<i class="fa fa-pencil-square-o"></i> 이제 하나씩 기능들을 구현해보도록 하자.

첫번째로 구글에서 이미지를 받아오는 기능을 구현하기 위해 

```python
driver.get("https://www.google.co.kr/imghp?hl=ko&tab=ri&ogbl")
```

구글 이미지로 페이지를 지정해주도록 하자.

```python
elem = driver.find_element_by_name("q")
```

위의 코드는 검생창을 찾는 기능이다. 

조금 더 이해를 하자면 지정한 특정요소를 찾는다고 생각하면 될 것 같다.

![4](https://user-images.githubusercontent.com/79001968/114050177-01bcdb00-98c7-11eb-84ed-cdf98c82ea2b.png)

F12를 눌러 검색창 요소들을 확인해보면 여러가지 요소가 있는 것을 확인 해 볼 수있다. class , name, type 등등 정보가 나오게된다. 

우리는 이중 name의 element가 q인것을 확인 했으니 위에 코드를 사용하면 된다.

(상황에 따라 name이 아닌 class, id등으로 바꿔서 코드를 작성할 수 있다.)

이제 검색창을 찾았으니 입력을 해야한다.

```
elem.send_keys("pycon")
```

이 send_keys를 통해 원하는 값을 입력할 수 있다.

```
elem.send_keys("박보영")
elem.send_keys(Keys.RETURN)
```

데이터 세트의 자료가 필요하기 때문에 연예인 사진을 다운 받도록 해보자.

(저는 박보영님을 좋아하기...^^)

자 이렇게 코드를 수정하고 다시 실행해보도록하자.

Keys.RETURN은 엔터키를 의미한다.

![5](https://user-images.githubusercontent.com/79001968/114152087-cf5bbe00-9958-11eb-8879-7ed339e6564e.png)

코드를 실행해보면 이렇게 구글 이미지에서 박보영님을 검색한 결과를 볼 수 있다.

------

이제 사진을 다운 받는 방법에 대해서 코드를 작성할 것이다.

![6](https://user-images.githubusercontent.com/79001968/114155624-a6d5c300-995c-11eb-8b25-dbadee99fccb.png)

첫번째 우리가 사진을 받기 위해서는 사진을 클릭을한 후 

위에 사진처럼 '이미지를 다른 이미지로 저장...'을 눌르고 파일명을 작성한 후 저장을 할 것이다.

```python
driver.find_elements_by_css_selector(".rg_i.Q4LuWd")[0].click()
```

이렇게 코드를 작성하면 첫번째 사진을 선택하는 과정까지 왔다.

여기서 element가 아니라 elements를 사용한 이유는 사진의 개수가 여러개이고 이 사진들을 리스트 안에 넣기 위해서는 s를 붙혀줘야한다.

```
driver.find_element_by_xpath("./html/body/div[2]/c-wiz/div[3]/div[2]/div[3]/div/div/div[3]/div[2]/c-wiz/div/div[1]/div[1]/div/div[2]/a/img").get_attribute("src")
```

그 이후 각각의 사진의 src를 이용하여 저장을 할 것이다. 

그러기 위해서는 src의 주소를 가져와야하는데 위에 작성된 코드가 각 사진의 src를 가져오게된다.

------

이제 다운을하는 과정을 넣고 while과 for문을 통해 반복하면 된다.

그 전에 이 작업간 속도의 제한을 두지 않고 실행시키면 오류가 발생할 가능성이 크다.

그러므로 time 라이브러리는 통해  중간에 약간의 시간을 넣어 주도록하자.

```python
import time
time.sleep(0.8)
```

(0.8초의 간격)

```python
import urllib.request
urllib.request.urlretrieve(imgUrl, "박보영" + str(count) + ".jpg")
```

(Url 다운로드 및 이름, 확장자 지정)

------

이렇게 까지 작성을 하면 크롤링의 기능을 구현한 것이다.

하지만 여기서 한가지 문제점이 발생한다.

페이지에 노출되는 사진을 50장이므로 50장까지만 사진을 다운 받을 수 있다.

이 과정을 해결하려면 위에 코드들이 실행되기 전에 스크롤을 먼저 내리고 다운을 하면 된다.

```
SCROLL_PAUSE_TIME = 0.5

# Get scroll height
last_height = driver.execute_script("return document.body.scrollHeight")

while True:
    # Scroll down to bottom
    driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")

    # Wait to load page
    time.sleep(SCROLL_PAUSE_TIME)

    # Calculate new scroll height and compare with last scroll height
    new_height = driver.execute_script("return document.body.scrollHeight")
    if new_height == last_height:
        break
    last_height = new_height
```

while문을 통해 스크롤을 끝까지 내리도록 해보자.

![7](https://user-images.githubusercontent.com/79001968/114161620-3f6f4180-9963-11eb-9afe-1c4ca723d61d.png)

코드들을 실행해보면 이렇게 나의 폴더에 자동으로 사진이 저장되는것을 볼 수 있다.

------

이미지파일 크롤링 코드 소스

~~~python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time
import urllib.request

driver = webdriver.Chrome()
driver.get("https://www.google.co.kr/imghp?hl=ko&tab=ri&ogbl")
elem = driver.find_element_by_name("q")
elem.send_keys("박보영")
elem.send_keys(Keys.RETURN)

#스크롤 내리기
SCROLL_PAUSE_TIME = 0.5

# Get scroll height
last_height = driver.execute_script("return document.body.scrollHeight")

while True:
    # Scroll down to bottom
    driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")

    # Wait to load page
    time.sleep(SCROLL_PAUSE_TIME)

    # Calculate new scroll height and compare with last scroll height
    new_height = driver.execute_script("return document.body.scrollHeight")
    if new_height == last_height:
        break
    last_height = new_height

#Url 다운
images = driver.find_elements_by_css_selector(".rg_i.Q4LuWd")
count = 1
for image in images:
    try:
        image.click()
        time.sleep(0.8)
        imgUrl = driver.find_element_by_xpath("./html/body/div[2]/c-wiz/div[3]/div[2]/div[3]/div/div/div[3]/div[2]/c-wiz/div/div[1]/div[1]/div/div[2]/a/img").get_attribute("src")
        urllib.request.urlretrieve(imgUrl, "박보영" + str(count) + ".jpg")
        count = count + 1
    except:
        pass

google.py

~~~



<script src="https://gist.github.com/HAN-Sang-Ho/f095afee62a7db69d0755b2b1fc93af6.js"></script>