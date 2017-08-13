# Observer pattern

Observer pattern 이란 subject 가 observers 들의 list 를 들고 있고 subject 의 
state 가 변경되었을 때, observer 들에게 알리는 design pattern 이다.

model-view-controlloer architectural pattern 의 key part 이기도 하다.

## Coupling and typical pub-sub implementations

일반적인 observer pattern 의 구현은 subject 와 observer 가 서로의 pointer 를 
들고 있어서 내부를 접근 할 수 있어 tightily coupled 되어있다고 여겨진다. 
그러나 이러한 구현은 speed, scalability 등등 여러 문제가 존재한다.

Publish-subsribe pattern (non-pooling) 구현은 이러한 문제를 subject 와 observer 
사이에 message queue server 와 message handler 를 두어서 해결한다. Observer 들은 
certain message 들을 subscribe 하고 message server 는 그러한 message 가 들어오면 
observer 들에게 알려준다. Observer 들은 sender 를 모르고 sender 는 receiver 를 
모르므로 decoupling 된다.
