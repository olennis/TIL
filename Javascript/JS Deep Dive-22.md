# this

---

# this?

책에서의 this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기참조변수라고 정의된다. 생성자 함수 내부에서는 프로퍼티 또는 메소드를 추가하기 위해 자신이 생성할 인스턴스를 참조할 수 있어야 한다. 하지만 생성자 함수에 의한 객체 생성 방식은 먼저 생성자 함수를 정의한 이후 new 연산자와 함께 생성자 함수를 호출하는 단계가 추가로 필요하다. 이 때 생성자 함수를 정의하는 시점에서는 아직 인스턴스가 생성되기 전이므로 생성자 함수가 생성할 인스턴스를 가리키는 식별자를 알 수 없다. 이 때 사용되는 것이 this 식별자이다. 

this는 js엔진에 의해 암묵적으로 생성되며, 코드 어디서든 참조 할 수 있다. 함수를 호출하면 arguments 객체와 this가 암묵적으로 함수 내부에 전달된다. 단 **this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.**

`바인딩은 식별자와 값을 연결하는 과정을 의미한다.` 

또한 this는 객체의 프로퍼티나 메소드를 참조하기 위한 자기 참조 변수이므로 일반적으로 객체의 메소드 내부 또는 생성자 함수 내부에서만 의미가 있다. 따라서 strict mode가 적용된 일반 함수 내부의 this에는 undefined가 바인딩 된다. 

---

### 함수 호출 방식, this 바인딩

1. 일반 함수 호출
    - 기본적으로 this에는 전역객체가 바인딩 된다.

    ```jsx
    function checkThis () {
    	console.log(this) // window
    }
    ```

    - strict mode에서는 undefined가 바인딩 된다.
    - 메소드 내에서 정의한 중첩 함수도 일반 함수로 호출되면 중첩 함수 내부의 this 에는 전역객체가 바인딩 된다.

    ```jsx
    var value = 1 // var 키워드로 선언한 전역 변수 value는 전역 객체의 프로퍼티다.
    const value = 1; // const 키워드로 선언한 전역 변수 value 는 전역 객체의 프로퍼티가 아니다.

    const obj = {
    	value: 100,
    	foo(){
    		console.log(this) // obj
    		
    		function bar() {
    			console.log(this) // window
    		}
    		
    	}
    }
    ```

    - 이처럼 일반 하수로 호출된 모든 함수 내부의 this에는 전역 객체가 바인딩 된다. 하지만 메소드 내에서 정의한 중첩 함수 또는 메소드에게 전달한 콜백함수가 일반함수로 호출될 때 메소드 내의 중첩 함수 또는 콜백 함수의 this가 전역 객체를 바인딩 하는 것은 문제가 있다. 그렇기 때문에 메소드 내부의 중첩 함수나 콜백함수의 this 바인딩을 메소드의 this 바인딩과 일치시키기 위한 방법은 다음과 같다.

    ```jsx
    var value = 1; 

    const obj = {
    	value : 100,
    	foo () {
    		const that = this;
    		setTimeout(function () {
    			console.log(that.value) // 100	
    		},100)
    	}
    }
    obj.foo()
    ```

2. 메소드 호출
    - 메소드 내부의 this에는 메소드를 호출한 객체가 바인딩 된다. 주의 할 점은 **메소드를 소유한 객체**가 아닌, **메소드를 호출한 객체**가 바인딩 된다는 것이다.

    ```jsx
    const person = {
    	name : 'kim',
    	getName () {
    		return this.name
    	}
    }
    console.log(person.getName())//kim
    ```

    - 프로토 타입 메소드 내부에서 사용된 this도 일반 메소드와 마찬가지로 해당 메소드를 호출한 객체에 바인딩 된다.

    ```jsx
    function Person (name){
    	this.name = name	
    }
    Person.prototype.getName = function() {
    	return this.name
    }

    const me = new Person('Lee')
    console.log(me.getName()) // Lee

    Person.prototype.name = 'kim'
    console.log(Person.prototype.getName()) //kim

    //첫번째의 경우 getName 메소드를 호출한 객체는 me다. 따라서 getName 메소드 내부의 this는 me를 가리키며 this.name === Lee다.
    //두번째의 경우 getName 메소드를 호출한 객체는 Person.prototype이다. 
    ```

3. 생성자 함수 호출
    - 생성자 함수 내부의 this에는 생성자 함수가 (미래에) 생성할 인스턴스가 바인딩 된다.
    - new 연산자와 함께 호출하지 않으면 생성자 함수로 동작하지 않는다. → 일반적인 함수의 호출이다.
    - 일반함수로 호출된 내부의 thsi는 전역 객체를 가리킨다.
4. apply, call, bind 메소드에 의한 간접 호출
    - apply, call, bind 메소드는 Function.prototype의 메소드이기 때문에 이들 메소드는 모든 함수가 상속받아 사용 할 수 있다.
    - apply와 call 메소드는 함수를 호출하면서 첫번째 인수로 전달한 특정 객체를 호출한 함수의 this에 바인딩한다.
    - arguments 객체와 같은 유사배열 객체에 배열 메소드를 사용하는 경우가 call과 apply의 대표적인 용도로 볼 수 있다. arguments객체는 배열이 아니기 때문에 slice와 같은 배열 메소드를 사용할 수 없지만, call과 apply를 이용한다면 가능하다.

    ---

    ### 요약

    일반 함수 호출 → this: 전역객체

    메소드 호출 → this: 메소드를 호출한 객체

    생성자 함수 호출 → this: 생성자 함수가 (미래에) 생성할 인스턴스

    apply, call, bind → this: apply/call/bind 메소드에 첫번째 인수로 전달한 객체
