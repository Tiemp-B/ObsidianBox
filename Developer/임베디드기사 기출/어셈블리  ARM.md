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