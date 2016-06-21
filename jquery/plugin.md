# jquery plugin 제작하기
jquery를 사용하다보면 다양한 반복을 하는것을 알 수 있습니다.  
심지어 여러곳의 홈페이지에서도 동일한 기능을 사용하기도합니다.  
이에 몇가지의 파일을 제작하여 다양한형태로 확장하여 사용할 수 있도록하면 편합니다.  
이를 Plug-In이라 불립니다.  
기존 플러그인을 사용할 수도 있지만, 직접 제작한 js파일을 플러그인으로 제작하면 유지보수면에서도 유리한부분이 있습니다.(직접 작성한 코드이니 이해면에서도 쉽습니다.)

```javascript
  $(this).parents().find('input').val();
```
위 코드는 항상 사용하던 방식중 하나입니다. 이를 플러그인으로 제작해보겠습니다.

## step_01
```javascript
  $.say= function(what){ alert('I Say ' + what); }
```
js함수를 선언하고 객체 프로퍼티로 할당하는것처럼 설정합니다.
위코드는 jQuery에서 사용하는 $형태를 적용시킨 예입니다.
하지만 jQuery외에도 $를 사용하는경우가 많으므로, 충돌을 방지하기 위한 형태로 수정해야 합니다.

```javascript
  jQuery.say = function(what){ alert('I Say ' + what); }
```
위와 같이 작성하면 $의 표현을 피할 수 있으나, 매번 jQuery를 대신 작성해야하거나, $에 익숙해진 분들에게는 어색한 형태로 나오기 쉽습니다.
이에 IIFE표현식(즉시실행함수)을 사용하여 처리합니다.

```javascript
  (function($){
    $.say = function(what){ alert('I Say ' + what); }
  })(jQuery)
```

### step_02
jQuery 전역함수는 실제로 jQuery객체의 메소드입니다. 따라서 jQuery 네임스페이스의 함수로 볼 수 있습니다.
jQuery 네임스페이스에 함수를 작성하면 일반 전역함수와의 충돌가능성은 적습니다.  
단, jQuery 메소드와 이름이 충돌하는지의 여부만 체크해주면 됩니다.

#### jQuery 라이브러리에서 제공하는 전역함수
- $.each()
- $.map()
- $.grep()

```javascript
// ---- 총합 구하기----
(function($){
  $.sum = function(array){
    var total = 0;
    $.cach(array, function(index, value){
      value = $.trim(value);
      value = parseFloat(value) || 0 ;
      
      total += value;
    });
    return total;
  };
})(jQuery);

// ---- 평균 구하기----
(function($){
  $.average = function(array){
    if($.isArray(array)){
      return $.sum(array) / array.length;
    }
    return '';
  };
})(jQuery);
```
위 코드는 배열을 받아 총계를 리턴하는 함수, 평균을 리턴하는 함수를 jQuery객체에 프로퍼티에 추가하여 간단한 플러그인을 제작했습니다.
이는 아래형태로 사용할 수 있습니다.

```javascript
  $.sum();
  $.average();
```

#### step_03
하지만 이렇게 제작된 전역함수는 jQuery네임스페이스 내 같은 이름을 가지는 함수와 충돌할 수 있습니다.  
이를 예방하기 위해 객체로 캡슐화 처리해야 합니다.

```javascript
  (function ($){
    $.mathUtils = {
      var total = 0;
      $.each(array, function(index, value){
        value = $.trim(value);
        value = parseFloat(value) || 0;
        
        total += value;
      });
    },
    averagel function(array){
      if($.isArray(array)){
        return $.sum(array) / array.length;
      }
      return '';
    };
  })(jQuery)
```
위의 패턴을 사용하면 jQuery,mathUtils 네임스페이스를 생성하고 정의된 함수를 jQuery객체의 프로퍼티인 mathUtils객체의 메소드로 처리됩니다.  
이에 아래와 같은 플러그인으로 제작할 수 있습니다.

```javascript
 $.mathUtils.sum(sum);
 $mathUtils.average(average);
```

#### step_04(객체 메소드)
앞서 jQuery 전역함수를 만들어 보았습니다.  
하지만 대부분의 jQuery 내장기능은 객체 메소드로 제공되고 있습니다.
이에 DOM일부를 조작하는 함수인 객체 메소드를 제작해 보겠습니다.

```javascript
  (function($){
    $.fn.swapClass = function(class1, class2){
      if(this.has.Class(class1)){
        this.removeClass(class1).addClass(class2);
      }
      else if(this.hasClass(class2)){
        this.removeClass(class2).addClass(class1);
      }
    };
  })(jQuery);
```
jQuery객체를 확장했던 전역함수와는 달리 객체 메소드는 jQuery.fn 객체를 확장처리하고 있습니다.(jQuery.fn은 jQuery.prototype의 별칭)  
위와같이 제작한 플러그인의 지점은 DOM 엘리먼트의 class를 변경하는 기능을 제공하고 있습니다.  
사용하는 방법은 아래와 같습니다.

```javascript
  $('div').swapClass('one','two');
```
기존의 &lt;div&gt;엘리먼트의 class가 'one'로  'two'라면 'one'로 변경이 된다고 예측할 수 있습니다.  


#### step_05(묵시적 반복)
위 설명된 객체 메소드는 DOM 엘리먼트 집합 중 최초의 &lt;div&gt;엘리먼트만 적용이 됩니다.  
하지만 일반적으로 사용되는 jQuery
따라서 Plug-In을 설계할 때 jQuery선택자가 복수인경우를 모두 감안해야 합니다.  
.each() 메소드를 이용하여 묵시적 반복을 수행하도록 수정합니다

```javascript
  (function($){
    $.fn.swapClass = function(class1, function2){
      this.each(function(){
        var $element = $(this);
        
        if ($element.hasClass(class1)){
          $element.removeClass(class1).addClass(class2);
        }
        else if($element.hasClass(class2)){
          $element.removeClass(class2).addClass(class1);
        }
      );
    };
  })(jQuery);
```

#### step_06(메소드 체인)
```javascript
  (function($){
    $.fn.swapClass = function(class1, class2){
      return this.each(function(){
        var $element = $(this);
        if( $element.hasClass(class1)){
          $element.removeClass(class1).addClass(class2);
        }
        else if( $element.has Class(class2)){
          $element.removeClass(class2).addClass(class1);
        }
      });
    };
  })(jQuery);
```

#### step_07(파일명 짖기)















