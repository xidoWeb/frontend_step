# php란?
PHP (공식적 PHP Hypertext Preprocessor) 는 Server - side HTML-embedded 스크립트 언어입니다.
즉, PHP는 서버에서 실행되며 HTML을 포함한 스크립트 언어라는 말입니다.
HTML을 포함하고 있기 때문에 HTML 파일을 PHP 확장자 (.php )로 저장하여도 아무 지장없이 사용할 수 있습니다.

__[ 참조 사이트 1 ](http://www.ezphp.net/lecture/)__ | 
__[ 참조 사이트 2 ](https://secure.php.net/manual/kr/index.php)__

## 시작에 앞서

```php
  <!DOCTYPE html>
  <html>
    <head>
      <meta charset="utf-8" />
      <title>예제</title>
    </head>
    <body>
      <?php
          echo "안녕, 나는 PHP 스크립트야!"; 
      ?>
    </body>
  </html>
```
위코드는 php 일부 입니다. (확장자명 *.php)  
하지만! 자세히 들여다보면 우리가 알고있는 html코드가 들어있습니다.  
바꿔말하자면 php는 html코드와 함께 사용이 가능하며 일부를 적용하여 사용한다는 점입니다.  
PHP 페이지는 "무언가"(여기서는, "안녕, 나는 PHP 스크립트야!"를 출력)를 하는 추가적인 코드를 가진 HTML입니다.  
html코드처럼 시작과 끝이 존재하며, 코드작성시 &lt;?와 ?&gt; 를 입력하고 내부에 작성합니다.  
일부는 &lt;?php  ?&gt; 코드로 작성하기도 합니다.

__PHP__가 클라이언트측 __자바스크립트__ 등과 구별되는 점은 이 코드는 서버에서 실행하여, 
HTML 생성하여 전송하는 점입니다.   
클라이언트는 스크립트 실행 결과만을 받게 되고, 그 코드의 모양(&lt;? ?&gt; 내부코드)은 알 수 없습니다.  
웹 서버를 설정하여 모든 HTML 파일을 PHP가 처리하게 할 수 있으며,   
그러면 사용자가 무엇으로 처리하는 지 알 방법은 없습니다.  

PHP를 사용하는 가장 큰 이득은 초보에게는 매우 쉽고, 전문가에게는 많은 고급 기능을 제공한다는 점입니다.

지금부터 하나씩 차근차근 익혀나가겠습니다.!
조금씩 조금씩 포기하지 않으면 해결 할 수 있습니다.

## 목차
1. [php 사용하기 앞서! 서버설치하기]()
  - [autoset](http://autoset.net)
  - [apmsetup](http://apmsetup.com)
  - [윈도우용 : wamp](http://apmsetup.com)
  - [맥용 : mamp](https://www.mamp.info/en/)
  - [php+mariaDB사용 : xampp](https://www.apachefriends.org/index.html)
1. [에디트 설치 및 사용](/edit_program/edit.md)
1. [기본 php 이해하기](./phpStep_01.md)
1. [기본 문법이해하기]()
1. [사용하기]()
1. [SQL 이해하기]()
1. [SQL 주요 항목]()






___
__[처음으로 돌아가기](../README.md)__