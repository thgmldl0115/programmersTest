**프로그래머스 코딩테스트 연습 0단계**

- import java.util.Arrays;
- import java.util.Collections;
- import java.lang.Math;
- import java.util.ArrayList;


> - 배열 정렬 : Arrays.sort(배열);
> - 배열 자르기 : Arrays.copyOfRange(배열, 시작인덱스, 끝인덱스)
> - 문자열.length();, 배열.length;
> - 문자열 비교 "c".compareTo("f"); // -3 (아스키코드 : c = 99, f =102)
> - 정규식 기억해두기 (String answer = myString.replaceAll("[a-k]", "l");)
> - 배열과 리스트 비교. 둘 다 활용하기.
> - ArrayList<String> a = new ArrayList<>(); 
> - split 마지막 값이 빈 값일 경우, 그 값도 배열에 포함시키는 방법
>> String[] li = myString.split("x", -1);


> - 리스트 정렬 Collections.min(list); (배열정렬은 Arrays.sort(배열);)
> - Collections.reverse(list);
> - (string 타입의 문자열).charAt(index); -> char타입 한글
> - 문자열.lastIndexOf(하위문자열); -> 문자열의 하위 문자열이 마지막으로 나타나는 위치 반환
> - Arrays.eqauls(배열a, 배열b); ->  a와 b의 인덱스들을 모두 비교
> - stack (후입선출) 값추가: add(), push() / 값제거: pop() / 마지막 요소 : peek()

> - java : 배열을 리스트로, 리스트를 배열로
```
// 1. 원본 배열
Integer[] arr = { 1, 2, 3, 4, 5 };
// 2. 원본 배열을 List로 변환
List<Integer> list = Arrays.asList(arr);
// 3. Collections.reverse() 메소드를 사용하여 list를 거꾸로 변환
Collections.reverse(list);
// 4. 리스트를 배열로 변환
Integer[] reverseArr = list.toArray(arr);

```
> - java : 실수를 정수로 변환. int answer = (int) Math.floor(d);
>> 유클리드 호제법 (암호화및실습 코드)
```
def GCD(a,b):
    dividend = a # 첫번째 피제수는 a.
    divisor = b # 첫번째 제수는 b.
    while divisor != 0:   # != 은 "같지 않다"를 의미
        quotient = dividend // divisor
        remainder = dividend % divisor
        dividend = divisor  
        divisor = remainder
    return abs(dividend)  #  GCD는 양수이므로 절대값 명령어 abs()를 사용
```
<hr>

**푼 문제 정리**

- 배열 만들기 2
```
import java.util.*;
class Solution {
    public int[] solution(int l, int r) {
        List<Integer> list = new ArrayList<>();
        String regx = "^[^12346789]*$";
        for (int i = l; i <= r; i++) {
            if (String.valueOf(i).matches(regx)) {
                list.add(i);
            }
        }
        if (list.size() > 0) {
            int[] result = new int[list.size()];
            for (int i = 0; i < list.size(); i++) {
                result[i] = list.get(i);
            }
            return result;
        }
        return new int[]{-1};
    }
}
```

- 분수의 덧셈
```
class Solution {
    public int[] solution(int numer1, int denom1, int numer2, int denom2) {
   
        // 통분하여 더하기
        int denom = denom1 * denom2;
        int numer = numer1 * denom2 + numer2 * denom1;
        
        // 최대공약수 구하기
        int dividend = (denom>numer)? denom: numer; 
        int divisor = (denom>numer)? numer: denom; 
        int gcd = 0;
        while(divisor != 0){   
            int quotient = dividend / divisor;
            int remainder = dividend % divisor;
            dividend = divisor;
            divisor = remainder;
        }
        gcd = Math.abs(dividend);
        
        // 약분하기
        int finalden = denom / gcd;
        int finalnum = numer / gcd;
        int[] answer = {finalnum, finalden};
        
        return answer;
    }
}
```
- 최댓값 만들기
```
import java.util.Arrays;
class Solution {
    public int solution(int[] numbers) {
        int answer = 0;
        int[] maxs = new int[numbers.length];
        for(int i=0; i<numbers.length; i++){
            int idx = 0;
            int[] list = new int[numbers.length-1];
            for(int j=0; j<list.length; j++){
                 if(i!=j){
                     list[idx++] = numbers[i] * numbers[j];
                 }
            }
            Arrays.sort(list);
            maxs[i] = list[numbers.length-2];
        }
        Arrays.sort(maxs);
        answer = maxs[numbers.length-1];
        return answer;
    }
}
```
