# 多线程

*  **IntentService**

    IntentService也是一种service，但是，与普通service不同的是，这种service执行在自身内部的子线程当中，而且当处理完传入的intent之后，就会自动杀死自己。

    * 使用要通过startService，bind会返回null，通过重写onHandleIntent实现服务内容
    
    * 可以在intentservice中处理耗时操作

    * 内部使用HandlerThread实现

    * 在获取Handler时，要记得默认获取的是子线程的looper，不是ui线程的

---

* **HandlerThread**

    handlerThread也是一种thread，不过，与一般thread不同的是，它自身就有了looper，也就是说，这种线程是为了处理消息而生的，只能通过往Handler发消息来使任务执行。

    * 一般像新线程一样初始化，但是不用传入runnable，而是通过获取thread.getLooper()来在外边创建一个这个线程所对应的Handler，然后通过post或者sendMessage方法使执行。所以内容实在Handler中的handlemessage中实现

    * 可以调用thread.quit()结束looper循环

    * 通过调用start() 使线程准备好looper并跑起来，不是run哦

---

* **Handler**

    Handler就是一个looper锁暴露出来的接口，让外部来提交任务，然后在handleMessage内部处理任务的

    * 可以通过post()和sendMessage()来添加消息任务到looper中

---

* **Looper**
    
    通俗点就是一个泵，一个处理消息的泵，但它是个静态类，一个线程只能拥有一个looper，不然会报错

    * 对于一个没有looper的线程来说，可以这样参考HandlerThread中的run方法，一般为首先查看是否已经有looper，looper.myLooper()，没有就Looper.prepare(),然后就可以Looper.loop()了

    * 可以通过Looper.getMainLooper()来获取UI线程的looper，一般用来更新界面

---

* **MessageQueue**

    一个looper对于一个消息队列，用来存放消息，然后looper从中顺序取出执行任务

---

* **AsyncTask**

    android 提供给开发者使用的异步处理方法，但是它的本质是，把任务放到一个全局的executor中执行，所以，使用这个方式不能做时间太长的操作，当然也可以将后台任务提交到自己传入的executor中来执行

    * 类型参数有三个，分别代表传入参数类型，进度参数类型，结果类型

    * 必要重写的是doInbackGround

    * execute是放到全局的executor中执行，

    * executeOnExecutor是传入一个executor来放到里面执行

---

* **ExecutorService**

    虽然executorservice不仅仅是Android里的，但是也会经常用到，需要说明的是，executor只是个接口，只有execute这个方法，而executorService是继承Executor的接口，提供了常用的线程处理方法，一般我们使用Executors这个工厂里的构建方法来获取ExecutorService就足够使用的了。

    * 通过submit来提交任务，可以是callable或者runnable

    * shutdown是不允许提交任务了，然后等已提交任务执行完

    * shutdownNow() 方法阻止等待任务启动并试图停止当前正在执行的任务

---

* **Callable**

    是一个interface，Callable需要传入一个类型参数，代表返回结果的类型，内部实现的方法call返回就会有这样一个类型的结果

---

* **Runnable**

    是一个interface，没有返回类型，直接实现run方法即可

---

* **Future**

    是对提交后的线程的控制的一个Interface，包括获取结果，判断状态，取消等，FutureTask是对该接口的唯一实现类，他是一个实现了runnable和future的接口的类。

    * cancel（True）是会取消正在执行的任务，但真正的中断需要靠内部的实现来做到，也就是说可以自动处理中断比如：thread.sleep时就可以

    * cancel（false）取消除了正在执行的任务。

    
