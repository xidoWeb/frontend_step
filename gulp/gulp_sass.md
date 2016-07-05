# GULP 사용법 익히기2(sass)
> **sass**는 기본적으로 ruby 기반이다.  
> 그렇다고 매번 **sass --watch -E utf-8 scss:css** 명령어를 입력하거나 **prepros** 등을 활용하기에는 번거롭다.
> 심지어 ruby를 이용하여 sass/scss를 compile 처리시 작업양이 많아지면 
> 변환시간이 느려진다는 문제가 발생한다.
> sass는 여러 언어의 기반으로 compile처리할 수 있도록 발전되었다.
> 이러한 여러 언어기반으로 compile하도록 만든것이 [LIBSASS](http://sass-lang.com/libsass)이다.
> node.js기반으로 처리하도록 되어 있으며, 속도 또한 ruby기반보다 빠르다. 
> 이제 **gulp**에 **sass**모듈을 첨부하여, 작동시켜보자!!

***terminal(cli)에서***   
* mac의 경우 설치시 앞부분에 sudo 를 입력한다.  
* **install**은 **i**로 요약할 수 있다.  
* **--global**은 -g로 요약 할 수 있다.  
* **--save-dev** 는 **-D**로 요약할 수 있다.

## 모듈의 이해
	모듈(Module)은 대체로 관련된 기능을 하나로 묶어 
	다른 코드와 결합도를 줄이고 재사용성을 높이 기 위해 사용한다.
	필요시 npm에서 필요 모듈을 검색하여 사용한다.
	
	node.js는 기본적으로 npm에 등록된 모듈들을 주로 사용한다.
	(npm이란?  Node Packaged Modules 의 약자 → 
	Node.js에서 사용되는 모듈을 패키지로 모아놓은 곳)
**<https://www.npmjs.com>**

### sass모듈 설치
- **terminal**에서 모듈을 찾아 설치

```cli
$ npm install gulp-sass --save-dev ↵ // mac의 경우 npm 앞에 sudo 입력
```
- **gulpfile.js**에서 내용 작성하기
- 







___
__[gulpfile.js 기본동작기능 익히기](./gulp_task.md)__   
__[grunt / gulp 메인 돌아가기](./grunt_gulp.md)__  
__[처음으로 돌아가기](../README.md)__