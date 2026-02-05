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

