# java-generic

* raw type
  * rawType은 제네릭이 도입되기 이전 코드와의 호환성을 위해 제공된다.
```java
public class RawType {
    public static void main(String[] args) {
        List rl = new ArrayList(); // 아무 원소나 넣을 수 있다.
        List<?> wl = new ArrayList<>(); // null 외에는 어떤 원소도 넣을 수 없다.

        rl.add(new Object());

        wl.add(null);
        // wl.add(new Object()); // compile error
        
        if (rl instanceof List) { // raw type을 써도 좋은 예.
            System.out.println("rl");
            List<?> o = (List<?>) rl;
        }

        if (wl instanceof List) {
            System.out.println("wl");
            List<?> o = (List<?>) wl;
        }

    }

}

```
* 공변/불공변
* BoundedType
  * `? extends ClassName`
    * read할때 사용한다.
    * write는 null밖에 할 수 없다. 
  * `? super ClassName`
    * write할때 사용한다.
    * read type은 Object이다.
  * `?`는 `? extends Object`와 동일하다.
  * `T super ClassName`은 불가능하다.
* Type Erasure
```
자바 컴파일러는 컴파일 과정에서 제네릭에 대한 타입소거를 진행.
타입소거란 타입정보를 컴파일 타임에만 유지하고, 런타임에는 삭제시키는것
과거 제네릭이 없던 버전과의 하위 호환성을 위함.
```

### 참고
* http://www.yes24.com/Product/Goods/65551284
* https://vagabond95.me/posts/generic-guide/
* https://futurecreator.github.io/2018/08/12/java-generics/
