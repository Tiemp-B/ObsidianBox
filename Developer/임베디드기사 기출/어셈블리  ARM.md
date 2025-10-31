---
cssclasses:
  - hover-reveal
---
## [Q.24-8]
Q. Watchdog 레지스터 주소가 0xEA200000이고, 값이 1일 때 ON, 0일 때 OFF이다. 다음 어셈블리 코드가 Watchdog를 끄는 코드일 때 빈칸을 채우시오
```
(   )
mov r1, #0x0
str (    ) [r0]
```

<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    ldr r0, =0xEA200000 <br>
    r1
  </div>
</details>
## [Q.24-5 / Q.19-5]
Q. 8bit LED 주소가 0x30002000부터 시작하고, 9번째 bit가 1이면 LED Enable, 0이면 Disable일 때, 전체 LED가 켜질 때, 0x00부터 0xFF까지 차례대로 켜는 ARM 어셈블리 코드의 빈칸을 채우시오.
```
mov r0, 0x30000000
mov r1, #0x000F0000
(   )
LOOP mvn r3, r2
orr r4, r3, #0x100
str r4, [r0, #0x2000]
```
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    mov r2, #0xFF
  </div>
</details>
## [Q.17-11]
Q. C언어에서 printf("%X", 15);를 실행하면 출력되는 결과는?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    F
  </div>
</details>

