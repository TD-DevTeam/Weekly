# Observable

ReactiveX 에서 observer 는 Observable 을 subscribe 한다. Observable 이 item 이나 
sequence of items 를 emit 하면 observer 는 react 한다. Observable 이 미래에 무엇을 
하든 적절하게 반응하는 observer 를 만들기 때문에, Observable 이 object 를 emit 
할 때 까지 기다릴 필요가 없어 concurrent 한 operation 을 용이하게 한다.

## Background
ReactiveX 에서는 instructions 들이 parallel 로 실행 되며, 그 결과들이 arbitrary order 
로 observer 에 의해서 capture 된다. Method 를 *calling* 하는 것이 아니라, data 를 
retrieving 하고 transforming 하는 mechanism 을 Observable 형태로 정의 하고, observer 
가 이것을 *subscribe* 한다. Observer 는 Observable 이 data 를 emit 할 때 마다 포착하고 
대응한다.

## Establishing Observers
Ordinary method call 의 flow 는 다음과 같다.

1. Call a method
2. Store the return value from that method in a variable
3. Use that variable and its new value to do something useful

```kotlin
// make the call, assign its return value to `returnVal`
val returnVal = someMethod(itsParameters)
// do something useful with returnVal
```

Asynchronous model 의 flow 는 다음과 같다.

1. Define a method that does something useful with the return value 
from the asynchronous call; this method is part of the *observer*
2. Define the asynchronous call itself as an *Observable*
3. Attach the observer to that Observable by *subscribing* it (this also 
initiates the actions of the Observable)
4. Go on with your business; whenever the call returns, the observer's 
method will begin to operate on its return value or values -- the *items* 
emitted by the Observable

```kotlin
// defines, but does not invoke, the Subsriber's onNext handler
// (in this example, the observer is very simple and has only an onNext handler)
val myOnNext = { it -> do something useful with it }
// defines, but does not invoke, the Observable
val myObservable = someObservable(itsParameters)
// subscribes the Subscriber to the Observable, and invokes the Observable
myObservable.subsribe(myOnNext)
// go on about my business
```

### onNext, onCompleted, and onError
