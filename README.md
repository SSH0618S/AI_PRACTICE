# AI_PRACTICE
  레벤슈타인 거리를 이용한 챗봇 구하기. 

  제시된 과제에 맞도록 코드 구성하지 못 했습니다.

```
# 레벤슈타인 거리 구하기
def calc_distance(a, b): 
    if a == b: return 0 
    a_len = len(a) # a 길이
    b_len = len(b) # b 길이
    if a == "": return b_len
    if b == "": return a_len
    
    matrix = [[] for i in range(a_len+1)] # 1차원 초기화
    for i in range(a_len+1): # 0으로 초기화
        matrix[i] = [0 for j in range(b_len+1)]  # 2차원 초기화    
    for i in range(a_len+1):
        matrix[i][0] = i
    for j in range(b_len+1):
        matrix[0][j] = j
    for i in range(1, a_len+1):
        ac = a[i-1]
        for j in range(1, b_len+1):
            bc = b[j-1] 
            cost = 0 if (ac == bc) else 1 
            matrix[i][j] = min([
                matrix[i-1][j] + 1,     # 문자 제거
                matrix[i][j-1] + 1,     # 문자 삽입
                matrix[i-1][j-1] + cost # 문자 변경
            ])            
    return matrix[a_len][b_len]
```
