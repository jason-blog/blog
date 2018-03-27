<pre class="prettyprint lang-js linenums">http://www.cnblogs.com/bingoidea/archive/2011/03/31/2000726.html
</pre>
<pre class="prettyprint lang-js linenums">一、什么是注释 

    说起注释，得先提一提什么是元数据(metadata)。所谓元数据就是数据的数据。也就是说，元数据是描述数据的。就象数据表中的字段一样，每个字段描述了这个字段下的数据的含义。而J2SE5.0中提供的注释就是java源代码的元数据，也就是说注释是描述java源代码的。在J2SE5.0中可以自定义注释。使用时在@后面跟注释的名字。 
                                                                                    
二、J2SE5.0中预定义的注释 

    在J2SE5.0的java.lang包中预定义了三个注释。它们是Override、Deprecated和SuppressWarnings。下面分别解释它们的含义。 

       1.Override注释：仅用于方法（不可用于类、包的生命或其他），指明注释的方法将覆盖超类中的方法（如果覆盖父类的方法而没有注 
释就无法编译该类），注释还能确保注释父类方法的拼写是正确（错误的编写，编译器不认为是子类的新方法，而会报错） 
       2.@Deprecated注释：对不应再使用的方法进行注释，与正在声明为过时的方法放在同一行。使用被     Deprecated注释的方法，编译器会 
提示方法过时警告（”Warring”） 
       3.@SuppressWarnings注释：单一注释，可以通过数组提供变量，变量值指明要阻止的特定类型警告（忽略某些警告）。数组中的变量指明要阻止的警告@SuppressWarnings(value={”unchecked”,”fallthrough”})） 

三、自定义注释@interface 

@interface：注释声明，定义注释类型（与默认的Override等三种注释类型类似)。请看下面实例： 

注释类1： 

package a.test; 

import java.lang.annotation.Documented; 
import java.lang.annotation.ElementType; 
import java.lang.annotation.Retention; 
import java.lang.annotation.RetentionPolicy; 
import java.lang.annotation.Target; 

@Documented 
@Retention(RetentionPolicy.RUNTIME) 
@Target(ElementType.TYPE) 
public @interface FirstAnno { 
String value() default "FirstAnno"; 
} 

注释类2： 

package a.test; 

import java.lang.annotation.Documented; 
import java.lang.annotation.ElementType; 
import java.lang.annotation.Retention; 
import java.lang.annotation.RetentionPolicy; 
import java.lang.annotation.Target; 

@Documented 
@Retention(RetentionPolicy.RUNTIME) 
@Target(ElementType.METHOD) 
public @interface SecondAnnotation { 
//  注释中含有两个参数 
    String name() default "Hrmzone"; 
    String url() default "hrmzone.cn"; 

} 

注释类3： 

package a.test; 

import java.lang.annotation.Documented; 
import java.lang.annotation.ElementType; 
import java.lang.annotation.Retention; 
import java.lang.annotation.RetentionPolicy; 
import java.lang.annotation.Target; 

@Documented 
@Retention(RetentionPolicy.RUNTIME) 
@Target(ElementType.FIELD) 
public @interface Kitto { 
String value() default "kitto"; 
} 

使用类： 

package a.test; 
@FirstAnno("http://hrmzone.cn") 
public class Anno { 
@Kitto("测试") 
private String test = ""; 
//  不赋值注释中的参数，使用默认参数 
    @SecondAnnotation() 
    public String getDefault() { 
            return "get default Annotation"; 
    } 
    @SecondAnnotation(name="desktophrm",url="desktophrm.com") 
    public String getDefine() { 
            return "get define Annotation"; 
    } 

} 

测试类： 

package a.test; 

import java.lang.reflect.Field; 
import java.lang.reflect.Method; 
import java.util.ArrayList; 
import java.util.List; 

public class AnnoTest { 
public static void main(String[] args) throws ClassNotFoundException { 
  // 要使用到反射中的相关内容 
  Class c = Class.forName("a.test.Anno"); 
  Method[] method = c.getMethods(); 
  boolean flag = c.isAnnotationPresent(FirstAnno.class); 
  if (flag) { 
   FirstAnno first = (FirstAnno) c.getAnnotation(FirstAnno.class); 
   System.out.println("First Annotation:" + first.value() + "\n"); 
  } 

  List&lt;Method&gt; list = new ArrayList&lt;Method&gt;(); 
  for (int i = 0; i &lt; method.length; i++) { 
    list.add(method[i]); 
  } 

  for (Method m : list) { 
   SecondAnnotation anno = m.getAnnotation(SecondAnnotation.class); 
   if(anno == null) 
    continue; 
   
   System.out.println("second annotation's\nname:\t" + anno.name() 
     + "\nurl:\t" + anno.url()); 
  } 
  
  List&lt;Field&gt; fieldList = new ArrayList&lt;Field&gt;(); 
  for(Field f : c.getDeclaredFields()){//访问所有字段 
   Kitto k = f.getAnnotation(Kitto.class); 
   System.out.println("----kitto anno: " + k.value()); 
  } 
} 

} 


结合源文件中注释，想必对注释的应用有所了解。下面深入了解。 
     深入注释： 
     @Target:指定程序元定义的注释所使用的地方，它使用了另一个类：ElementType，是一个枚举类定义了注释类型可以应用到不同的程序元素以免使用者误用。看看java.lang.annotation 下的源代码： 

@Documented  
@Retention(RetentionPolicy.RUNTIME)  
@Target(ElementType.ANNOTATION_TYPE)  
public @interface Target {  
    ElementType[] value();  
} 


     ElementType是一个枚举类型，指明注释可以使用的地方，看看ElementType类： 
public enum ElementType {  
     TYPE, // 指定适用点为 class, interface, enum  
     FIELD, // 指定适用点为 field  
     METHOD, // 指定适用点为 method  
     PARAMETER, // 指定适用点为 method 的 parameter  
     CONSTRUCTOR, // 指定适用点为 constructor  
     LOCAL_VARIABLE, // 指定使用点为 局部变量  
     ANNOTATION_TYPE, //指定适用点为 annotation 类型  
     PACKAGE // 指定适用点为 package  
} 
     @Retention：这个元注释和java编译器处理注释的注释类型方式相关，告诉编译器在处理自定义注释类型的几种不同的选择，需要使用RetentionPolicy枚举类。此枚举类只有一个成员变量，可以不用指明成名名称而赋值，看Retention的源代码： 

@Documented  
@Retention(RetentionPolicy.RUNTIME)  
@Target(ElementType.ANNOTATION_TYPE)  
public @interface Retention {  
    RetentionPolicy value();  
} 
     类中有个RetentionPolicy类，也是一个枚举类，具体看代码： 

public enum RetentionPolicy {  
     SOURCE, // 编译器处理完Annotation后不存储在class中  
     CLASS, // 编译器把Annotation存储在class中，这是默认值  
     RUNTIME // 编译器把Annotation存储在class中，可以由虚拟机读取,反射需要  
} 
     @Documented：是一个标记注释，表示注释应该出现在类的javadoc中，因为在默认情况下注释时不包括在javadoc中的。 

所以如果花费了大量的时间定义一个注释类型，并想描述注释类型的作用，可以使用它。 

注意他与@Retention(RetentionPolicy.RUNTIME)配合使用，因为只有将注释保留在编译后的类文件中由虚拟机加载， 

然后javadoc才能将其抽取出来添加至javadoc中。 
     @Inherited：将注释同样继承至使用了该注释类型的方法中（表达有点问题，就是如果一个方法使用了的注释用了@inherited， 

那么其子类的该方法同样继承了该注释） 
注意事项： 
     1.所有的Annotation自动继承java.lang.annotation接口 
     2.自定义注释的成员变量访问类型只能是public、default；(所有的都能访问，源作者没用到函数：getDeclaredFields而已) 
     3.成员变量的只能使用基本类型（byte、short、int、char、long、double、float、boolean和String、Enum、Class、annotations以及该类型的数据）(没有限制，大家可以修改测试一下，就清楚) 
     4.如果只有一个成员变量，最好将参数名称设为value，赋值时不用制定名称而直接赋值 
     5.在实际应用中，还可以使用注释读取和设置Bean中的变量。 </pre>