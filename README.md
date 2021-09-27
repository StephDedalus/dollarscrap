# dollarscrap
Проект, который касается скрапинга сайта Банка России. Вывод данных валюты (доллар за период 1998-2021 годов)


Порядок моих действий: 
1) Так как я занимаюсь страпингом первый раз, то перваый шаг - изучение материала по теме. В конечном счете начал делать задание, обращая за помощью https://www.dataquest.io/blog/web-scraping-python-using-beautiful-soup/. 


USAGE
import requests 
from bs4 import BeautifulSoup
import lxml.html as lh
import pandas as pd

3)  Я встретился с ошибкой 403, которую решил путем добавления в код информации о пользователе. Это помогло мне решить данную проблему. 
url = 'https://cbr.ru/currency_base/dynamics/?UniDbQuery.Posted=True&UniDbQuery.so=0&UniDbQuery.mode=1&UniDbQuery.date_req1=&UniDbQuery.date_req2=&UniDbQuery.VAL_NM_RQ=R01235&UniDbQuery.From=01.01.1998&UniDbQuery.To=09.09.2021'
headers = {'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36'}
re = requests.get(url, headers=headers)

4) Получение информации с сайта
re.content
soup = BeautifulSoup(re.content, 'html.parser')
5) Я получил доступ к БД,заранее отформотировав даты от 1998 года по 2021. Мне пришлось пренебречь некоторыми годами, потому что не удалось решить проблему с запятыми. 

6) Произвел анализ страницы, просмотрев исходный код страницы. Нашел строчки в коде, которые отвечают за таблицу с данными о курсе доллара с 1998 - 2021 года.
7) Нашел все "td" 
8) И потом прочитал таблицу с помощью pandas
9) После этого скачал в формат excel.
10) Открыл новый файл в jupyter notebook 
11) Далее построил графики с помощью seaborn. 
