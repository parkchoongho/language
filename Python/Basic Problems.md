### Baseball Game

```python
import random

numlist = [0,1,2,3,4,5,6,7,8,9]

anslist = random.sample(numlist, 3)
count = 0
print("0과 9 사이의 서로 다른 세 숫자를 랜덤한 순서로 뽑았습니다.")
print("\n")
print("세 수를 하나씩 차례대로 입력하세요.")

while True:
    mylist = []
    while True:
        firstinput = int(input("1번째 수를 입력하세요.: "))
        if firstinput > 9 or firstinput < 0:
            print("범위를 벗어나는 수입니다. 다시 입력해주세요.")
            continue
        mylist.append(firstinput)
        break
    while True:
        secondinput = int(input("2번째 수를 입력하세요.: "))
        if secondinput in mylist:
            print("중복되는 수 입니다. 다시 입력해주세요.")
            continue
        if secondinput > 9 or secondinput < 0 :
            print("범위를 벗어나는 수입니다. 다시 입력해주세요.")
            continue
        mylist.append(secondinput)
        break
    while True:
        thirdinput = int(input("3번째 수를 입력하세요.: "))
        if thirdinput in mylist:
            print("중복되는 수 입니다. 다시 입력해주세요.")
            continue
        if thirdinput > 9 or thirdinput < 0 :
            print("범위를 벗어나는 수입니다. 다시 입력해주세요.")
            continue
        mylist.append(thirdinput)
        break
    strike = 0
    ball = 0
    for i in range(0, len(anslist)):
        if anslist[i] == mylist[i]:
            strike += 1
        else:
            ball += 1
    count += 1
    print("{}S {}B".format(strike, ball))
    if strike == 3:
        print("축하합니다. {}번만에 세 숫자의 값과 위치를 모두 맞추셨습니다.".format(count))
        break
```

### Finding Pitagoras

```python
a = 0
b = 0
c = 0

for a in range(1,333):
    for b in range(a + 1, 500):
        c = 1000 - a -b
        if a**2 + b**2 == c **2:
            print(a*b*c)
```

### Flip

```python
numbers = [2, 4, 6, 8, 10, 12, 14]

# 리스트 뒤집기
# 코드를 입력하세요.
for i in range(len(numbers) // 2):
    left_index = i
    right_index = len(numbers) - left_index - 1
    
    temp = numbers[left_index]
    numbers[left_index] = numbers[right_index]
    numbers[right_index] = temp

print("뒤집어진 리스트: " + str(numbers))
```

