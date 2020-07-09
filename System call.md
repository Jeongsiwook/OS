System call이 어떻게 작동하는가?
==============================
간단히 말해서, system call은 다음과 같다
--------------------------------------
1. User application program은 system call에 대해 argument를 설정한다.
2. Arguments가 모두 설정된 후에, program은 system call 명령을 실행한다.
3. 이 instruction은 exception을 발생시킨다: processor가 new address로 건너뛰고, 거기서 실행중인 code를 시작하는 event
4. New address의 instruction은 user program의 state를 저장하고,   
원하는 system call을 파악, 해당 system call을 구현하는 kernel의 function을 call,   
user program의 state를 복원, control을 다시 user program으로 되돌린다.

* Open() system call을 호출하는 user application에 대해 시각적 설명
