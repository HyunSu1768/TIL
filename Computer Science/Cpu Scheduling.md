### 👾 CPU 스케줄러
***
#### CPU 스케줄링이란?
* 프로세스는 생성되고 난 뒤 여러 상태를 거치게 된다. 운영체제의 CPU 스케줄러는 준비 상태의 프로세스 중에서 어떤 프로세스에게 CPU를 할당할지 결정한다. 이를 CPU 스케줄링이라고 한다. 또한 Dispatcher 는 CPU 제어권을 CPU 스케줄러에 의해 선택된 프로세스에게 넘깁니다.이를 Context Switch라고 합니다
#### 장기 스케줄링과 단기 스케줄링
* 규모에 따라 분류된다
#### 장기 스케줄링 ( Long-term scheduler )
* 가장 큰 틀에서 이루어지는 CPU 스케줄링. 고수준 스케줄링, 작업 스케줄링 이라고도 합니다.
* 프로세스에 Memory(및 각종 자원)을 주는 문제를 스케줄링이라고 합니다.
* 전체 시스템의 부하를 고려하여 작업 요청을 받아들일지, 거부할지에 대한 결정을 합니다. 즉 지금의 상태를 프로세스를 인정하는 작업을 장기 스케줄러가 합니다.
* 장기스케줄링의 결정에 따라 시스템 내의 프로세스 총 개수가 정해집니다.
* 최근 운영체제에서는 보통 장기 스케줄러가 없다. 프로그램을 실행시키면 바로 준비 상태에 돌입한다.
#### 중기 스케줄링 ( Medium-term scheduler, Swapper )
* 장기스케줄링은 프로세스의 활성화 승인을 다룬다면 중기 슼케줄링은 이미 활성화가 된 프로세스들에 대한 관리를 한다.
* 시스템의 과부하를 막기 위해 활성화된 프로세스들의 중지 여부를 결정하여 활성화된 프로세스 수를 조절함.
* 즉, 여유 공간 마련을 위해 프로세스를 통째로 메모리에서 디스크로 쫓아낸다. ( Swap out )
* 중기 스케줄링에 의해 중지된 프로세스들은 보류 상태가 된다.
#### 단기 스케줄링 ( Short-term scheduler, CPU scheduler )
* 가장 작은 단위의 스케줄링을 단기 스케줄링이라고 한다.
* 어떤 프로세스에 CPU를 할당할지, 어떤 프로세스를 대기상태로 보낼지 등을 결정함
* 단기 스케줄러가 어떤 기준에 따라 프로세스를 선택하고 어느 정도 자원을 배분할지에 따라 시스템에 큰 영향을 끼침.
* 단기 스케줄링은 스케줄링 중에서도 핵심인 부분이다.
***
#### CPU 스케줄링의 목적
* 모든 프로세스가 적당히, 공평하게, 효율적으로 자원을 할당받는 것이다. 하지만 다양한 상황에서 이를 만족시키는건 쉽지 않다. 자연스럽게 이를 위한 고려사항들을 떠울리게 되고 그에 맞는 알고리즘들이 설계되었다.
#### 공평성, 호율성, 안정성, 확장성, 반응 시간 보장, 무한 연기 방지
* 공평성 : 프로세스에게 자원을 배분하는 과정이 공평해야 한다.
* 효율성 : 시스템 자원이 쉬는 시간이 없어야 한다. ( 약간 클오클 장인 놀게 냅두면 안되는거처럼 ) 
* 안정성 : 중요 프로세스들은 우선권을 주어야 한다. 또한 프로세스가 많아도 안정적으로 돌아가야 한다.
* 확장성 : 시스템 자원이 늘어나는 경우 이 혜택이 시스템에 반영되어야 한다.
* 반응 시간 보장 : 프로세스의 요구가 있을 경우 적절한 시간 안에 반응을 해줘야 한다.
* 무한 연기 방지 : 특정 프로세스의 작업이 무한정 연기되면 안된다.

#### 스케줄링 시 고려사항
* 위에서 살펴본 목적을 이루기 위해 고려해야 하는 사항들
##### 선점형 스케줄링과 비선점형 스케줄링
* 선점(preemptive)이란 빼앗을 수 있음을 말한다. 즉 선점과 비선점 스케줄링 방식은 어떤 프로세스가 CPU를 할당받으면 이를 운영체제에 의해 강제로 회수할 수 있는것인지 아닌지에 대한 내용
##### 선점형 스케줄링
* 선점형 스케줄링의 경우 운영체제가 필요하다고 판단하면 실행 상태에 있는 프로세스의 작업을 중단시키고 새로운 작업을 시작할 수 있음. Timeout 상황, Interrupt, System call 등이 발생한 경우 현재 실행 상태에 있는 프로세스의 CPU를 강제로 회수하고 다른 프로세스에게 CPU 를 할당해줄 수 있는 스케줄링 방식
* 선점형 스케줄링은 Context swithch 로 인한 오버헤드가 발생한다. 그러나 하나의 프로세스가 CPU를 독점한다는 것은 동시에(느낌상) 여러 작업을 할 수 없다는 의미이므로 대부분의 저수준 스케줄러는 선점형 스케줄링 방식을 사용함
* 오버헤드란 인터럽트로 인해 프로세스가 원래 하던 일을 멈추고 인터럽트에 대한 대응을 하는데 그 시간이 10초가 걸릴것이 그 이상의 시간이 걸리게 하는것을 오버헤드라고 함
##### 비선점형 스케줄링
* 비선점형 스케줄링의 경우 어떤 프로세스가 실행 상태에 들어가면 그 프로세스가 끝나거라 CPU를 자진 반납하는 경우가 아니면 계속 실행된다. 이는 Context Switch에 대한 오버헤드도 없고 스케줄러가 할 일도 적어져 효율적일 수 있으나 전체 시스템의 처리율이 떨어지게 된다
#### 프로세스 우선순위
* 프로세스 간에도 우선순위가 존재할 수 있다. 프로세스는 크게 커널 프로세스와 일반 프로세스로 나뉘는데 CPU 스케줄러는 보통 커널 프로세스를 높은 우선순위에 둔다. 커널과 관련된 작업들은 보통 일반 프로세스보다 중요하기 때문이다. 여기서 우선순위가 높다는 것은 일반적으로 더 빨리 자주 실행된다는 의미입니다. 시스템 자원을 더 많이 받는다는 것이죠.
  * 커널 프로세스란 운영체제의 핵심이 되는 프로세스를 말한다.
* 일반 프로세스 간에도 우선순위가 존재합니다. 비디오 플레이어와 워드 작업이 같은 우선순위라면 실시간으로 영상을 출력해야 하는 비디오 플레이어가 끊기고 맙니다. 이러한 문제 해결을 위해서는 프로세스 간에도 우선순위를 매겨야 한다는 사실이 합리적입니다.
#### CPU bound process 와 IO bound process
* CPU bound process , I/O bound process , CPU burst , I/O burst 란?
  * CPU burst는 CPU 를 사용하는 시간이라는 뜻이고 , I/O burst 는 입출력을 사용하는 시간입니다.
  * 즉 CPU bound process 는 CPU burst가 많은 프로세스이고 I/O bound process 는 I/O burst가 많은 프로세스를 의미합니다
* 따라서 스케줄링 시 I/O bound process 를 CPU bound process 보다 앞에 두는것이 효율적입니다.
  * I/O bound process 는 CPU 에게서 할당받은 시간보다 빨리 대기상태로 바뀝니다. 하지만 CPU bound process 는 할당받은 시간을 모두 쓰기때문입니다.
#### 전면 프로세스와 후면 프로세스
* 전면 프로세스는 GUI를 사용하는 OS에서 맨 앞에 놓인 프로세스를 의미합니다. 이 글을 읽고있는 브라우저는 전면 프로세스라고 할 수 있겠죠. 전면 프로세스는 사용자와 상호작용이 가능합니다.
* 반면 후면 프로세스는 상호작용이 없습니다. 예로는 압축 프로그램입니다.
