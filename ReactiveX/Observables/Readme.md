# Observables

Observable 은 asynchronous events 의 stream 을 다루기 위해 model 되었다. 
Observable 을 이용해서 callback 지옥에서 벗어날 수 있으며, code 의 가독성은 
더 좋아지고 error 의 경향이 적어진다.

## Observables Are Composable
Java 의 Future 의 경우 single level 의 asynchronous execurtion 을 다루는 데 
있어서 매우 straigtforward 하지만, conditional asynchronous execution flows 를 
다루는 것은 매우 어렵다. 그러나 Observables 은 asynchronous data 의 sequecne 와
flows 를 compose 하기 위해 설계되었다.

## Observables Are Less Opinionated
ReactiveX 는 특정 concurrency 나 asynchronicity 의 source 에 편향되어있지 않다. 
Observables 은 thread-pools, event loops, non-blocking I/O), actors (such as 
from Akka) 등을 사용해서 구현될 수 있다. Client code 는 Observables 과의 모든 
상호 작용을 blocking 구현이든 non-blocking 구현이든 asynchronous 하게 처리한다.


## Reactive Programming
Observables 의 경우 producer 는 value 가 available 하면 consumer 에게 push 한다.
Value 가 synchronous 하게 혹은 asynchronous 하게 올 수 있으므로 이러한 접근은 
좀더 flexible 하다.

Observerable type 일반적인 Observer pattern 에 두가지 semantics 이 추가되어 있다.

* Producer 는 consumer 에게 더 이상 가능한 data 가 없다고 알릴 수 있다.
* Producer 는 consumer 에게 error 가 발생 했다고 알릴 수 있다.
