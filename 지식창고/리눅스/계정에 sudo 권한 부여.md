## 사건
우분투 설치 후 첫 계정에 sudo 권한이 없는 상황

## 해결
재부팅하면서 shift 키를 눌러 GRUB(GRand Unified Bootloader)로 켠 후 __Advanced options for Ubuntu__ -> __recovery mode__ -> __root Drop to root shell prompt__ 로 들어가면 root 권한의 CLI를 실행할 수 있다.
그 후
```bash
mount -o remount ,rw /
usermod -aG sudo user


```