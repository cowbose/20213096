# 오픈소스SW개론 01분반
## 20213096 김도형
### 유닉스 명령어 top
+ 시스템의 상태를 전반적으로 가장 빠르게 파악 가능
+ 옵션 없이 입력하면 interval 간격으로 화면을 갱신하여 정보를 보여줌
+ top 실행 전 옵션


        순간의 정보를 확인하려면 -b 옵션
    
    
        top 실행 주기 설정하려면 -n 옵션
+ top 실행 후 명령어


        shift + p : CPU 사용률 내림차순
    
    
        shit + m : 메모리 사용률 내림차순
    
    
        shift + t : 프로세스가 돌아가고 있는 시간 순
    
    
        k : kill. k 입력 후 PID 번호 작성. signal은 9
    
    
        f : sort field 선택 화면 -> q 누르면 RES순으로 정렬
    
    
        a : 메모리 사용량에 따라 정렬
    
    
        b : Batch 모드로 작동
    
    
        1 : CPU Core별로 사용량 보여줌
+ ps와 top의 차이점


        ps는 ps한 시점에 proc에서 검색한 cpu 사용량
    
    
        top은 proc에서 일정 주기로 합산해 cpu 사용율 출력
    
    <img width="670" alt="스크린샷 2018-07-18 20 25 32" src="https://user-images.githubusercontent.com/86956159/172050180-b3ed8b6b-2680-4f7e-b0d7-7f52c3de89b1.png">

+ 3:58 : 3시간 58분 전에 서버가 구동
+ load average : 현재 시스템이 얼마나 일을 하는지를 나타냄. 3개의 숫자는 1분, 5분, 15분 간의 평균 실행/대기 중인 프로세스의 수. + + CPU 코어수 보다 적으면 문제 없음
+ Tasks : 프로세스 개수
+ KiB Mem, Swap : 각 메모리의 사용량
+ PR : 실행 우선순위
+ VIRT, RES, SHR : 메모리 사용량 => 누수 check 가능
+ S : 프로세스 상태(작업중, I/O 대기, 유휴 상태 등)


#### VIRT, RES, SHR
+ 현재 프로세스가 사용하고 있는 메모리
+ VIRT


        프로세스가 사용하고 있는 virtual memory의 전체 용량
        
        
        프로세스에 할당된 가상 메모리 전체
        
        
        SWAP + RES
+ RES


        현재 프로세스가 사용하고 있는 물리 메모리의 양


        실제로 메모리에 올려서 사용하고 있는 물리 메모리
        
        
        실제로 메모리를 쓰고 있는 RES가 핵심!
+ SHR


        다른 프로세스와 공유하고 있는 shared memory의 양
        
        
        예시로 라이브러리를 들 수 있음. 대부분의 리눅스 프로세스는 glibc라는 라이브러리를 참고하기에 이런 라이브러리를 공유 메모리에 올려서 사용
        
