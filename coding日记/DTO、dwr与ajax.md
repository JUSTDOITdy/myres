#### DTO（Data Transfer Object）数据传输对象

DTO是Data Transfer Object 的简写，既数据传输对象。

是一种设计模式之间传输数据的软件应用系统。数据传输目标往往是数据访问对象从数据库中检索的数据。数据传输对象与数据交互对象或数据访问对象之间是一个不具备有任何行为除了存储和检索的数据。（访问和存取器）

表现层于应用层之间是通过DTO来进行交互的，数据传输对象是没有行为的POCO对象，他的目的是为了对领域对象进行数据封装，实现层与层之间的数据传递。为何不直接将领域对象进行数据传递？因为领域对象更注重领域，DTO更注重数据。由于“富领域模型”的特点，这样会直接将领域对象的行为暴露给表现层。

​    DTO本身不是业务对象，他是根据UI需求进行设计的。简单来说Model面向业务，我们是通过业务来定义Model的。而DTO是面向UI，通过UI的需求来定义的，通过DTO我们实现了表现层与Model层之间的解耦，表现层不引用Model。如果开发过程中我们的模型变了，而界面没变，我们只需改Model而不需要去改动表现层。

#### DWR (Direct Web Remoting)是一个Web远程调用框架，会根据java类动态生成javascript代码。http://www.cnblogs.com/ygj0930/p/6686115.html

  JavaBean 是一种[JAVA语言](https://www.baidu.com/s?wd=JAVA%E8%AF%AD%E8%A8%80&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)写成的可重用组件。为写成JavaBean，类必须是具体的和公共的，并且具有无参数的构造器。JavaBean 通过提供符合一致性设计模式的公共方法将内部域暴露成员属性。众所周知，属性名称符合这种模式，其他Java 类可以通过自身机制发现和操作这些JavaBean 的属性。

VO即value object值对象
主要体现在视图的对象，对于一个WEB页面将整个页面的属性封装成一个对象。然后用一个VO对象在控制层与视图层进行传输交换。

DTO (经过处理后的PO，可能增加或者减少PO的属性)：
Data Transfer Object数据传输对象
主要用于远程调用等需要大量传输对象的地方。
比如我们一张表有100个字段，那么对应的PO就有100个属性。
但是我们界面上只要显示10个字段，
客户端用WEB service来获取数据，没有必要把整个PO对象传递到客户端，
这时我们就可以用只有这10个属性的DTO来传递结果到客户端，这样也不会暴露服务端表结构.到达客户端以后，如果用这个对象来对应界面显示，那此时它的身份就转为VO。

POJO（POJO是一种概念或者接口，身份及作用随环境变化而变化） ：
POJO有一些private的参数作为对象的属性。然后针对每个参数定义了get和set方法作为访问的接口
plain ordinary java object 简单java对象
即POJO是一个简单的普通的Java对象，它不包含业务逻辑或持久逻辑等，但不是JavaBean、EntityBean等，不具有任何特殊角色和不继承或不实现任何其它[Java框架](https://www.baidu.com/s?wd=Java%E6%A1%86%E6%9E%B6&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)的类或接口。
POJO对象有时也被称为Data对象，大量应用于表现现实中的对象。
一个POJO持久化以后就是PO。
直接用它传递、传递过程中就是DTO
直接用来对应表示层就是VO  

