# The-program-should-be-easy-and-spaced

## 클린코드

## PHP는 템플릿

## PHP

## 피카소의 황소
핵심을 이해하고 간결하고 이해하기 쉽게 만드는 것이 좋다.  
<span style="color:blue">**즉, 쉬운것을 어렵게 하지 말자는 것이다.**</span>
  - 객체지향이 절차지향의 위에 있는것이 아니다. 서로 장단점을 가지고 있으며 보완을 하면 더 좋다
  - 피카소는 본래의 황소도 잘그린다. 기본에 충실해야 핵심을 잘 파악 할 수 있는 것이다.
<img src="imgs/피카소-황소.png" width="440">
<br>

예를 들면 다음과 같다.
  - DB 설계할때 시스템 현황에 맞지 않게 너무 많은 정규화는 오히려 더 많은 시간을 필요 하게 된다.  
    (역정규화는 속도를 더 빠르게 하기 위해 사용 되기도 한다.)
  - 상속을 너무 많이 하게 되면 디버깅 할 때 부모 찾아 삼만리가 된다.  
    (일부 중복이 나쁜것은 아니다.)
  - 코드 재사용은 분명 좋은것이다. 하지만 너무 이부분에 몰입하면 더 복잡해 진다.  
    너무 많은 함수 메소드를 만드는 것은 분명 후회하게 된다.(남을 힘들게 한다)  
    (이해하기 쉽고 간결하고 수정하기 쉬운것이 더 좋다) 

  
**✔프로그램머의 오래된 유머가 있는데 다음과 같은 것이다.**
```
문제) 화면에 hello를 출력 하시오.

🤦‍♂️ JAVA
public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("hello");
  }
}

🤦‍♂️ C
int main() {
  printf("hello");
}

🤦‍♂️ NodeJS(JavaScript)
console.log("hello");

🤦‍♂️ PHP 
echo 'hello';

👌 전문가, 해커
리눅스 쉘에서 echo hello
```


## 