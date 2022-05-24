# 오픈소스 소프트개론 과제 (2)
```
1) 리눅스 명령어 (**top, ps, jobs, kill**) 에 대해서...
2) ** Vim Editor** 의 매크로 명령어 (*q*) 에 대해서...
```
---
## 1) ***리눅스 명령어***
+ (1) **top**
: 시스템 프로세스/메모리 사용 현황을 실시간으로 출력하는 명령어

--시스템의 상태를 전반적으로 가장 빠르게 파악 가능(CPU, Memory, Process)
```
-n : 지정한 숫자만큼 화면 출력을 갱신한 후 이름
-u : 지정한 사용자의 프로세스를 모니터링
-b : 출력결과를 파일이나 다른 프로그램으로 전달
-d : 화면갱신주기를 초 단위로 설정
-p : 지정한 PID 프로세스를 모니터링
-----
shift + p : CPU 사용률 내림차순으로 정리
shift + m : 메모리 사용률 내림차순으로 정리
shift + t : 프로세스가 돌아가고 있는 시간 순
a : 메모리 사용량에 따라 정렬
b : Batch 모드로 작동
1 : CPU Core별로 사용량 보여줌

```
*출처* : [리눅스 명령어 top](https://inpa.tistory.com/entry/LINUX-%F0%9F%93%9A-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EA%B4%80%EB%A6%AC-%EB%AA%85%EB%A0%B9%EC%96%B4-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-Foreground-Background " top 명령어 ")
+ (2) **ps**
: 현재 실행중인 프로세스를 목록을 보여주는 리눅스 명령어

-- 주로 파이프라인, grep명령어와 함께 사용하여 특정 프로세스를 확인하는데 많이 사용된다.
```
-----
-e : 실행중인 모든 프로세스의 정보를 출력한다.
-l : 긴 포맷으로 보여준다
-f : 프로세스에 대한 자세한 정보를 출력한다.(PPID 확인 가능
-u [사용자이름] : 특정 사용자에 대한 모든 프로세스의 정보를 출력
-p pid: pid로 지정한 프로세스의 정보를 출력
- A : 모든 프로세스 출력 (-e) 와 동일
-----
e : 프로세스 정보와 함께 프로세스의 환경변수 정보도 출력
u : 프로세스 소유자의 이름, CPU 사용량, 메모리 사용량 등 상세 정보를 출력
a : 터미널에서 실행한 프로세스의 정보를 출력
x : 실행중인 모든 프로세스의 정보를 출력
```
*출처* : [리눅스 명령어 ps](https://arer.tistory.com/150 "ps명령어")

[리눅스 명령어 ps (2)](https://inpa.tistory.com/entry/LINUX-%F0%9F%93%9A-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EA%B4%80%EB%A6%AC-%EB%AA%85%EB%A0%B9%EC%96%B4-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-Foreground-Background "ps명령어")
+ (3) **jobs**
:작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경 되었지만 보고되지 않은 상태 등을 표시하는 명령어다. (현재 세션의 작업 상태를 표시)

```
-l : 나열되는 각 작업에 대한 추가 정보를 제공하고 이 정보에는 작업번호, 현재작업, 프로세스 그룹ID,상태,작업을 시작한 명령이 포함된다.
-n : 최종 통지된 이후 중지 또는 종료한 작업만 표시한다.
-p : 선택된 작업에 대한 프로세스 그룹 리더의 프로세스 ID를 표시한다.
-----
state : 다음 값 중 하나를 표시합니다(POSIX 로케일에서).
Running
작업이 신호에 의해 일시중단되지 않았으며 종료하지 않았음을 나타냅니다.
Done
작업이 완료되어 종료 상태 0을 리턴했음을 나타냅니다.
Done (code)
작업이 정상적으로 완료되었으며 지정된 0이 아닌 종료 상태 코드로 종료했음을 나타냅니다. 이 코드는 10진수로 표시됩니다.
Stopped
작업이 일시 중단되었음을 나타냅니다.
Stopped (SIGTSTP)
SIGTSTP 신호가 작업을 일시 중단했음을 나타낸다
Stopped (SIGSTOP)
SIGSTOP 신호가 작업을 일시 중단했음을 나타낸다.
Stopped (SIGTTIN)
SIGTTIN 신호가 작업을 일시 중단했음을 나타낸다.
Stopped (SIGTTOU)
SIGTTOU 신호가 작업을 일시 중단했음을 나타낸다. 
```
*출처* [리눅스 명령어 jobs](https://itwiki.kr/w/%EB%A6%AC%EB%88%85%EC%8A%A4_jobs " jobs 명령어")

[리눅스 명령어 jobs(2)](https://www.ibm.com/docs/ko/aix/7.2?topic=j-jobs-command " jobs 명령어")

+ (4) **kill**
:프로세스에 특정한 *signal*을 보내는 명령어

--- 일반적으로 종료되지 않는 프로세스를 종료 시킬 떄 많이 사용한다.
```
SIGHUP : 연결 끊기, 프로세스의 설정파일을 다시 읽음
SIGINT : 인터럽트
SIGQUIT : 종료
SIGILL : 잘못된 명령
SIGTRAP : 트랩 추적
SIGBUS : 버스 에러
SIGFPE : 고정 소수점 예외
SIGKILL : 죽이기
SIGSEGV : 세그멘테이션 위반
SIGPIPE : 읽을 것이 없는 파이프에 대한 시그널
SIGALRM : 경고 클릭
SIGTERM : 소프트웨어 종료 시그널
SIGSTKFLT : 프로세서 스택 실패
SIGSCHLD : 자식 프로세서의 상태변화
SIGCONT : STOP 시그널 이후 계속 진행할 떄 사용
SIGSTOP : 정지
SIGTSTP : 키보드에 의해 발생하는 시그널

```
*출처* : [리눅스 명령어 kill](https://bigsun84.tistory.com/355 " kill 명령어" )

[리눅스 명령어 kill](https://inpa.tistory.com/entry/LINUX-%F0%9F%93%9A-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EA%B4%80%EB%A6%AC-%EB%AA%85%EB%A0%B9%EC%96%B4-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-Foreground-Background " kill 명령어 " )
## 2) ***Vim editor***의  매크로 명령어 (q)
+ **q**
1) __같은 명령 반복 매크로__

 (1) *q+a : a키에 recording시작
 
 (2) q : recording 종료


