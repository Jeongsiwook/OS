## System call이 어떻게 작동하는가?
### 간단히 말해서, system call은 다음과 같다
1. User application program은 system call에 대해 argument를 설정한다.
2. Arguments가 모두 설정된 후에, program은 system call 명령을 실행한다.
3. 이 instruction은 exception을 발생시킨다: processor가 new address로 건너뛰고, 거기서 실행중인 code를 시작하는 event
4. New address의 instruction은 user program의 state를 저장하고,   
원하는 system call을 파악, 해당 system call을 구현하는 kernel의 function을 call,   
user program의 state를 복원, control을 다시 user program으로 되돌린다.

* Open() system call을 호출하는 user application에 대해 시각적 설명
<img src="https://github.com/Jeongsiwook/OS/blob/master/image/Open()%20system%20call.png?raw=true" width="450px" height="300px" title="">
  + System call interface(OS가 이용할 수 있는 system call link 역할을 한다)는 OS kernel에 의도된 system call을 호출
  + system call state 및 모든 return 값을 반환한다는 점에 유의해야 한다.
  + Caller는 system call이 어떻게 구현되는지 또는 실행 중에 무엇을 수행하는지 알 필요가 없다.   
  
* 다른 예: write() system call을 호출하는 C 프로그램이 printf() library call을 호출하는 경우
  <img src="https://github.com/Jeongsiwook/OS/blob/master/image/write()%20system%20call.png?raw=true" width="450px" height="300px" title="">

## Fork() system call
