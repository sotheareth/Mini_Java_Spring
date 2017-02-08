# Mini_Java_Spring

### To get ko, en shortcut language two character

````sh
String shortLanguageTwoCharacter = LocaleContextHolder.getLocale().toLanguageTag();

````

### To sort data in collection, collections use interface comparator
### To sort data in collection, collections use interface comparable

````sh

import java.util.Comparator;

public class Person implements Comparable<Person>, Comparator<Person> {
	private String id;
	private String name;

	Person(String id, String name) {
		this.id = id;
		this.name = name;
	}

	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	@Override
	public String toString() {
		return "Person [id=" + id + ", name=" + name + "]";
	}

	@Override
	public int compareTo(Person o) {
		return this.name.compareTo(o.name) + 
			this.id.compareTo(o.id);
	}

	@Override
	//sort by name
	public int compare(Person o1, Person o2) {
		return o1.name.compareTo(o2.name);
	}

}
````

# To create custom annotation
```code
@Target({ElementType.TYPE, ElementType.METHOD})
@Retention(RetentionPolicy.RUNTIME)
@Documented
public @interface Redundancy {

	 boolean value() default true;
}
```

#To use on class and method

```code
@Redundancy
public class A {
	....
}
```

#To excute annotation in aop
create pointcut on package classes

```code
@Aspect
public class RundancyExecution {

	@Pointcut("execution(* com.bizmob.api.service.*.*(..))")
	private void anyServiceMethod() {}

	//pointcut get from above
	@Before(pointcut = "anyServiceMethod", )
  	public void doAccessCheck() {
   	 // ...
  	}
}
```
