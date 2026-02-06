#### btc.py
```python
import requests as req

url = "https://api4.binance.com/api/v3/ticker/price?symbol=BTCUSDT"
rel = req.get(url).text

btc = rel[29:34]          
won = str(int(btc) * 1450)     

print("비트코인 가격:", btc + "원")
print("원화가격:", won[:1] + "억 " + won[1:5] + "만 " + won[5:] + "원")
```

#### disp.py
```python
# print 응용2
import time as t
print("기대하세요.", end='\r')
t.sleep(1.5)
print("드디어~~~", end='\r')
t.sleep(1.5)
print("개방합니다!", end='\r')
t.sleep(1.5)
```

#### test.py
```python
print("테스트 해볼게요.")
a = 123
b = 234
print(a)
b
```

#### usd.py
```python
import requests as r

btc = "https://api4.binance.com/api/v3/ticker/price?symbol=BTCUSDT"
usd = "https://oapi.koreaexim.go.kr/site/program/financial/exchangeJSON?authkey={한국수출입은행 API키}&data=AP01"

r1 = r.get(btc).json()
r2 = r.get(usd).json()

usd_krw = float(
    [x['deal_bas_r'] for x in r2 if x['cur_unit'] == 'USD'][0]
    .replace(',', '')
)

r3 = float(r1['price']) * usd_krw

print(f"{int(r3):,}", "원")
```

#### web.py
```python
import requests as req
import webbrowser as wb

# 위성위치
url = "http://api.open-notify.org/iss-now.json"
# 탑승자 명단
url2 = "http://api.open-notify.org/astros.json"

result = req.get(url).json()
lat = result['iss_position']['latitude'] # 위도
lon = result['iss_position']['longitude'] # 경도

result2 = req.get(url2).json()["number"]

url = f"https://www.google.com/maps?q={lat}, {lon}"

print(f"현재 {result2}명이 탑승한 인공위성(국제우주정거장) 위치를 열겠습니다. 위도: {lat}, 경도: {lon}")
wb.open(url)
```
