---
cssclasses:
  - hover-reveal
---
## [Q.17-11]
Q. C언어에서 printf("%X", 15);를 실행하면 출력되는 결과는?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    F
  </div>
</details>
## [Q.24-7 / Q.18-2]
Q. malloc() 함수로 메모리를 할당받은 후, 할당받은 메모리를 해제하는 함수는?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    free()
  </div>
</details>
## [Q.24-3 / Q.17-4]
Q. 상속받은 메서드를 하위 클래스에서 수정하거나 재정의하는 것은?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    오버라이딩
  </div>
</details>
## [Q. 17-1 / Q.23-7]
Q. C언어에서 공용체를 나타내는 키워드는?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    union
  </div>
</details>
## [Q. 23-18]
Q. 다음 C언어 코드 중 오류가 발생하는 행을 찾고 이유를 설명하시오.
```C
char *ptr1;
char *ptr2;
ptr1 = malloc(512);
ptr2 = malloc(512);
ptr2 = ptr1;
free(ptr1);
free(ptr2);
```
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    free(ptr2) 행이 에러가난다.
    이미 할당 해제된 메모리를 다시 할당 해제하였다.
  </div>
</details>
## [Q.21-13]
Q. 다음 C언어 코드의 출력 결과를 쓰시오
```C
#include<stdio.h>
void main(){
int a=31, b=27, c=19;
printf("%d", ((a=(a>b)?a:b)?a:c));
}
```
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    31
  </div>
</details>
## [Q.18-6]
Q. 다음 C 프로그램 소스를 보고, 출





















