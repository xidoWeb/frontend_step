# GULP 사용법 익히기
> [gulp](http://gulpjs.com)는 **javascript task runner**로 **javascript build tool**이라 불린다. <br>
즉, 프로그램작업 및 개발을 좀 더 쉽고 빠르고 편하게 작업할 수 있도록 도와주는 기능을 한다.<br>  
대표적으로 
**minify(축약)**,
 **uglify(압축)**, 
 **concat(모음)**, 
 **compile(변환)**, 
 **watching(실시간 감시)**, 
 **validating(검사)** 
 기능 등이 있다.    

***terminal(cli)에서***   
* mac의 경우 설치시 앞부분에 sudo 를 입력한다.  
* **install**은 **i**로 요약할 수 있다.  
* **--global**은 -g로 요약 할 수 있다.  
* **--save-dev** 는 **-D**로 요약할 수 있다.

## 기초이해

### 기초 사용하기전!! 환경설치(간단이해)
1. Git을 설치한다. [git-scm](https://git-scm.com)   
   : **gitbash** 사용을위해(node기반의 명령어를 좀더 잘 실행한다는 장점이 있다.!!)
2. Node.js 를 설치한다. [node.js](https://nodejs.org): 현재기준(4.4.7버전)
   : node를 설치하면 **npm**( 노드JS로 만들어진 모듈을 웹에서 받아서 설치하고 관리해주는 프로그램 )이 같이 설치된다. 
  - 버전 및 설치  확인(terminal):  
  	`node --version && npm --versiion`  

___
### **Gulp**를 사용하기(terminal)   
#### 기본테스트_1
- 컴퓨터 전역에 기본설치    

```cli
$ npm install --global gulp-cli	↵ // mac의 경우 npm 앞에 sudo를 붙인다.  
$ gulp -v    ↵ // 버전 및 설치 확인  
```

- 폴더 생성 후 gulp설치(설치 후 폴더 확인해보면 **node_modules**폴더가 생성되어있음

```cli
$ npm install gulp --save-dev	↵	// mac의 경우 npm 앞에 sudo
``` 
- node_modules를 컨트롤할 **package.json** 파일생성

```cli
$ npm init -y ↵ // mac의 경우 npm 앞에 sudo, 내용은 추후 변경할 예정이므로 -y 포함
```

- **gulp**를 사용/ 컨트롤할 **gulpfile.js**파일생성

```cli
$ touch gulpfile.js	// 해당폴더에서 직접 생성시켜도 무방
```

- 동작 테스트(gulpfile.js파일을 열어 작성)

```javascript
var gulp = require('gulp');

gulp.task('hello', function(){
	console.log('----------------------------------------');
	console.log(' > hello gulp test');
	console.log('----------------------------------------');
});

```
- 위내용을 작성 후 terminal창에서 실행해서 결과확인

```cli
$ gulp hello ↵	// 동작상태를 파악
```
![gulp hello](img/gulp_task_t.png)

##### 테스트 내용 설명
1. node_modules에서 gulp를 가져와서 사용( **require('gulp')** )
2. **gulp**기능 업무실행(task) 및 업무 이름(hello) 부여( **gulp.task('hello')** )
3. **terminal**에서 작성 → gulp중 hello 호출 → log내용실행됨  
 
#### 기본테스트_2 
- gulpfile.js에서 추가 내용작성

```javascript
 gulp.task('default', ['hello']);
```
- **terminal**에서 작성후 확인  

```cli
$ gulp ↵ // 테스트_1과 같은 결과물 도출
```
##### 테스트 내용 설명
> gulp의 다양한 기능을 작성하여 사용할 예정이므로 매번
>  **gulp '이름호출'** 하기에는 번거롭기 때문에 <br>
  하나의 기능에 등록하여, 여러기능을 한번에 작동하도록 함('default'는 미리 설정되어있는 비어있는 이름값)





___
__[gulpfile.js 기본동작기능 익히기](./gulp_task.md)__  
__[gulp step2_sass 기능 익히기](./gulp_sass.md)__  
__[grunt / gulp 메인 돌아가기](./grunt_gulp.md)__  
__[처음으로 돌아가기](../README.md)__















