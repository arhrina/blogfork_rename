---
layout: post
title: JavaScript Object, this
subtitle: js, json
date: 2020-04-13T20:20:25.000Z
author: Arhrina
categories: update

tags: js
---

## JavaScript Object

자바스크립트의 객체는 properties와 values로 이루어진다

변수는

```javascript
var car = ferrari;
```

방식으로 선언되어서 자료에 따라 변수의 자료형이 정해진다

변수는 하나에 하나의 값만을 담을 수 있지만, object는 여러개의 값을 담을 수 있다

```java
Map<String, String> car = new HashMap<String, String>();
car.put("name", "ferrari");
car.put("color", "red");
car.put("horsePower", "670"); //  String에 String으로 선언하였으므로 본래 들어가야할 숫자가 아닌 문자열로 값을 넣었다
```



자바에서의 Key, Value 쌍으로 저장되는 Map과 같이 자바스크립트의 object도 name, value 쌍으로 저장된다



```javascript
var car = { name:"ferrari", color:"red", horsePower:670};
```

읽기 편하게 중간에 공백이나 줄바꿈을 하여도 같은 결과를 얻는다

```javasciprt
var car = {
	name : "ferrari",
	color : "red",
	horsePower : 670
};
```

이러한 object에 대한 접근은,

<b>objectName.propertyName</>이나

<b>objectName["propertyName"]</b>으로 접근한다

```javascript
console.log(car.name);
console.log(car["name"]);
```

메서드를 value로 지정해서 저장할 수도 있으며 이럴 경우 메서드를 사용할 이름은 property가 된다

```javasciprt
var car = {
	speed : 0;
	accelerator : function(){ return this.speed = 350; }
	};

car.accelerator(); // 메서드임을 의미하는 괄호는 반드시 작성되어야한다. 안해주면, 메서드의 정의를 return한다
console.log(car.speed); // 출력값은 350
```

### String, Number, Boolean으로 객체를 선언하는 것은 피하자. 코드의 성능에 지장을 미친다




## JavaScript의 중요한 키워드, this

자바스크립트에서 this는 this가 속해있는 scope를 참조하고 있는 범위를 뜻한다

<h4>어디서 쓰이고 있는지가 가장 중요하다</h4>

예를 들어서, 메서드 안에서 쓰이는 this는, this를 가지고 있는 객체(메서드가 정의된)를 뜻한다

```javascript
var language = {
	myFirst : "C",
	mySecond : "Cpp",
	myThird : "Java",
	myFirstLanguage : function() {
		return this.myFirst + " is my First learning language"; // 이 경우 this가 속해있는 메서드를 가지고 있는 object는 language이다.
	}
};
```

this가 혼자 쓰인다면 global object를 뜻하며, strict mode("use strict";를 사용한 모드. 추후 포스팅)에서는 this는 undefined(java로 굳이 치자면 null point exception이 뜰 값. null이나 문자열 ""과는 엄연히 다르다)

html(혹은 js) 이벤트 안에서는 element를 뜻한다


```javascript
<button onclick="this.style.background-color='green'">
  클릭하면 녹색됨 // this는 여기서 element인 button
</button>
```


<h4>이러한 this의 사용 scope를 항상 주의해서 사용해야하며, 잘 사용하면 아주 편리하게 코드를 짤 수 있다</h4>