https://blog.csdn.net/jingzi123456789/article/details/72123937

``![img](https://img-blog.csdn.net/20171015172524055?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvQ19TYW5kYW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

1. # 流的分类

     

    ### 按数据流的方向不同：输入流，输出流。

    output.write(xxx),   括号里()是要输出(写)的内容，必须有东西(参数)，不能无参

    ​              创建文件流时必须得有个源文件，输入和输出都相当于一样东西插着管子，必须得有个被插管子的东西

    

    内存流 ByteArrayOutputStream ，操作都是从顶到下，但编程需要从低到上，下是一个对象 到 对象流 到  内存流，然后从内存流里去出来 ，包装上对象流，再输出的过程，有点像计算机网络的东西，

     文件流、内存流、socket的流，都是节点流，相当于数据链路层；

    而处理流相当于网络层，是依赖于处理流的。

    ​                ByteArrayOutputStream baos=new ByteArrayOutputStream();
    ​		//字节数组流（内存流），属于节点流，和文件流同级的内存流，对应的模型是内存
    ​		ObjectOutputStream oos = new ObjectOutputStream(baos);
    ​		//对象流（序列化流），属于处理流，处理流是处理 节点流 的，必须依附节点流

    ​			oos.writeUTF("你好啊朋友");
    ​			oos.writeInt(1111);

    ​	    	    oos.writeObject(new Date());

    ​             	  oos.writeObject(对象)；

    ​		byte[] buf = baos.toByteArray();  //很重要，返回的是内存里的字节内容
    ​		ByteArrayInputStream bais =new ByteArrayInputStream(buf);
    ​		ObjectInputStream ois = new ObjectInputStream(bais);

    ​                  	String msg = ois.readUTF();
    ​	      	    int age = ois.readInt();

    ​                          Object date = ois.readObject();
    ​            	      Object obemployee1 = ois.readObject();

    

    

    

    

    input.read(),   ()里如果无参，就返回读到的一个字节或字符或-1；有参数就把东西放在这里面，返回一个

    ​                         读到的内容（字节或字符）长度的int，同样没有就是-1

    ##### 文件输入流：是把文件变成流输入到Java来，input.read(data),把流流到（读入到）byte[]数组里

    ​        InputStream input = new FileInputStream(file);

    ​        byte[] data = new byte[1024];

    ​	while ((n= **input.read(data)**) != -1) {...}

    ##### 文件输出流：OutputStream output = new FileOutputStream(file);

    

    下图是一个复制程序，也即输入流和输出流对接，

    文件->文件输入流ip->ip.read  ->byte[]  sz->op.write(sz)->文件输出流op ->文件(复制)

    ![1557245368431](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\1557245368431.png)

    按处理数据单位不同：字节流，字符流。
    （1） 字节流：数据流中最小的数据单元是字节。
    （2）字符流：数据流中最小的数据单元是字符， Java中的字符是Unicode编码，一个字符占用两个字节。

    #### 按功能不同：节点流，处理流。

     处理流：是对一个已存在的流的连接和封装，通过所封装的流的功能调用实现数据读写。
    如BufferedReader。处理流的构造方法总是要带一个其他的流对象做参数。一个流对象经过
    其他流的多次包装，称为流的链接。 

    （1）程序用于直接操作目标设备所对应的类叫节点流。
    （2）程序通过一个间接流类去调用节点流类，以达到更加灵活方便地读写各种类型的数据，这个间接流类就是处理流。

    ##### 处理流一般要套在节点流上

    ```java
    FileInputStream fis = new FileInputStream("d:\\JavaProject\\TestBufferStream1.java"); 
    
    BufferedInputStream bis = new BufferedInputStream(fis);
    ```

    

    

    ### 

    ### 2.1 节点流的类型

    这里写图片描述![这里写图片描述](https://img-blog.csdn.net/20170515115140908?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvamluZ3ppMTIzNDU2Nzg5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

    （1）File 文件流。对文件进行读、写操作 ：FileReader、FileWriter、FileInputStream、FileOutputStream。、
    （2）Memory
    1）从/向内存数组读写数据: CharArrayReader与 CharArrayWriter、ByteArrayInputStream与ByteArrayOutputStream。
    2）从/向内存字符串读写数据 StringReader、StringWriter、StringBufferInputStream。
    （3）Pipe管道流。 实现管道的输入和输出（进程间通信）: PipedReader与PipedWriter、PipedInputStream与PipedOutputStream。

    ### 3.1 处理流的类型

2. ![è¿éåå¾çæè¿°](https://img-blog.csdn.net/20170515115247115?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvamluZ3ppMTIzNDU2Nzg5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

    - （1）Buffering缓冲流：在读入或写出时，对数据进行缓存，以减少I/O的次数：BufferedReader与BufferedWriter、BufferedInputStream与BufferedOutputStream。 
    - （2）Filtering 滤流：在数据进行读或写时进行过滤：FilterReader与FilterWriter、FilterInputStream与FilterOutputStream。 
    - （3）Converting between Bytes and Characters 转换流：按照一定的编码/解码标准将字节流转换为字符流，或进行反向转换（Stream到Reader）：InputStreamReader、OutputStreamWriter。 
    - （4）Object Serialization 对象流 ：ObjectInputStream、ObjectOutputStream。 
    - （5）DataConversion数据流： 按基本数据类型读、写（处理的数据是Java的基本类型（如布尔型，字节，整数和浮点数））：DataInputStream、DataOutputStream 。 
    - （6）Counting计数流： 在读入数据时对行记数 ：LineNumberReader、LineNumberInputStream。 
    - （7）Peeking Ahead预读流： 通过缓存机制，进行预读 ：PushbackReader、PushbackInputStream。 
    - （8）Printing打印流： 包含方便的打印方法 ：PrintWriter、PrintStream。

    ---------------------


#### 这里说一下字节数组流（ByteArrayI/OStream）

和文件字节流FileI/OStream相对应，字节数组流是内存里面的流，可以说是内存流，对应的、抽象的是电脑或网络里的一块内存，但不是你定义的byte[]数组，

这是把文件->程序->内存，再从内存->程序->文件，不要把程序和这内存搞混了，

用文件流控制文件的输入输出，（这里插一句，Java操作文件是通过操作系统的，中间有一个操作系统才是直接操作文件的）（对象都是实际东西的抽象，用File的对象控制真正的文件），把文件流—>Java的byte[]

![1557240522534](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\1557240522534.png)

