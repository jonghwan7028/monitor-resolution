# monitor-resolution
How to fix monitor by commanding in a terminal Ubuntu 18.04.3

# Ubuntu 18.04.3 Monitor resolution resetting

제가 가지고 있는 컴퓨터는 서버로 모니터가 VGA로만 지원이 됩니다. 하지만 모니터는 1920x1080 이거든요. 이사항을 해결하기 위해 인터넷을 뒤졌는데 몇가지 사항이 정리되어 공유합니다.

## 1. 현재 가능한 모니터 크기 확인하기
```
sudo xrandr
```
제 모니터는 최대로 1920x2048 가능하다고 나오네요. 현재 모니터는 1920x1080 이어서 다음과 같은 명령어를 실행하였습니다.
```
cvt 1920 1080
sudo xrandr --newmode "1920x1080_60.00" #cvt 입력후 나온 값들을 복사해서 붙여넣는다
sudo xrandr --addmode VGA-1 "1920x1080_60.00"
xrandr
sudo xrandr --output VGA-1 --mode "1920x1080_60.00"
```
하지만, 부팅을 하면 설정이 사라지기 때문에 이것을 부팅하면서 자동으로 실행되도록 설정을 할 필요가 있다.
우분투 18.04는 startup applicatrion preference 에서 이 기능을 제공한다. 이 앱을 실행하면 창이 나오는데
* add 
* command 에  xrandr --output VGA-1 --mode "1920x1080_60.00"을 추가하면 된다.
