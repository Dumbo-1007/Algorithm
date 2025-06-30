---
tags:
  - Android
---
**Android聊天软件的开发RSA加解密的密钥生成步骤：**
- 安装OpenSSL
- 打开命令提示符，进入存放密钥的文件夹
- 生成密钥。在命令提示符输入：
	- `openssl genrsa -out private_key.pem 1024`
	- `openssl rsa -in private_key.pem -out public_key.pem -pubout`
	- `openssl pkcs8 -topk8 -in private_key.pem -out pkcs8_private_key.pem`
- 打开密钥目录下的`public_key.pem`和`pkcs8_private_key.pem`，提取`----BEGIN PUBLIC KEY----`
  和`----END PUBLIC KEY----`之间的字符串，就够分别得到公私密钥

**Android 项目工程下面的 assets 目录的作用是：**
- 主要存放一些资源文件，这些资源会被原封不动打包到apk里面

**简述 Android 操作系统的特点**
- Android 是谷歌发布的基于 Linux 的开源手机平台，该平台由操作系统，中间件，用户界面和应用软件组成，是第一个可以完全定制，免费，开放的手机平台。
- Android 底层使用开源的 Linux 操作系统，同时开放了应用程序开发工具，使所有程序开发人员都在统一，开放的开发平台上进行开发，保证了 Android 应用程序的可移植性。

**描述 Android 平台体系结构的层次划分**
- Android 采用了软件堆层的架构，共分为四层： Linux 内核，中间件层，应用程序框架层和应用程序层。

**简述 Intent 的定义与用途**
- Intent 是一个动作的完整描述，包含了动作的产生组件、接收组件和传递的数据信息。Intent 为 Activity 、Service 和 BroadcastReceiver 等组件提供交互能力，将一个组件的数据和动作传递给另一个组件。Intent 最常见的一个用途就是启动 Service 和 Activity ；另一个用途是在 Android 系统上发布广播消息，广播消息可以是接收到特定数据或消息，也可以是手机上的信号变化或电池状态信息等。

**Activity 的生命周期以及7个生命周期函数**
- Activity 的状态变化是人为操作的，而这些状态的变化，也会触发一些事件，叫它生命周期事件。
1. onCreate()：当创建 activity 时被调用，主要完成一些初始化工作，例如设置布局文件，对按钮绑定监听器，加载 savedlnstanceState 参数。
2. onStart()：当 Activity 被用户可见时调用。
3. onRestart()：重新启动 Activity 时调用，该活动仍在栈中，而不是启动新的活动。
4. onResume()：Activity 开始与用户交互时调用，即该 activity 获得了用户的焦点（无论是启动还是重新启动一个活动，该方法总是被调用）。
5. onPause()：Activity 被暂停或收回 cpu 和其他资源时调用，该方法用于保存活动状态的。
6. onStop()：Activity 被停止并转为不可见状态时调用，如果第 2 个 activity 没有完全遮挡第 1 个 activity，则不调用。
7. onDestory()：Activity 被完全从系统内存中移除时调用。

**为什么要使用布局管理器？**
- 根据屏幕的大小，管理容器内的控件，自动适配组件在手机屏幕中的位置

**6 大布局管理器作用？**
- LinearLayout、TableLayout、RelativeLayout、FrameLayout、AbsoluteLatout、GridLayout

**简述网络布局管理器作用**
- 网格布局管理器将容器划分为行×列的网格，每个控件置于网格中，当然也可以通过设置相关属性使一个控件占据多行或多列。

**简述 TableLayout 中重要属性及作用**
- android:stretchColumns：为 TableLayout 容器里面设置属性，表示被设置的这些列可拉伸。
- android:shrinkColumns：为 TableLayout 容器里面设置属性，表示被设置的这些列可收缩。
- android:layout_column：在容器里面的控件设置属性，指定该控件在 <span style="background:#f2634a">TableRow</span> 中的指定列。

**Android UI 组件类图主要分为两大部分，都是什么？**
- View（视图：普通控件）、ViewGroupe（容器：布局管理器）

**简要说明 SQLite 数据库创建过程**
- 首先创建一个类继承 SQLiteOpenHepler ，重写 onCreate 方法并在该方法中创建表，使用创建出的SQLiteOpenHelper的子类对象的 getWritableDatabase() 方法获得一个可读写的数据库对象。

**请简述 BaseAdapter 适配器的4个抽象方法以及他们的具体作用**
- getCount()：得到 item 条目的总数
- getItem(int position)：根据 position 得到某个 item 的对象
- getItemId(int position)：根据 position 得到某个 item 的 id 
- getView(int position, View convertView, ViewGroup parent)：得到相应 position 对应的 item 视图

**社交软件开发的一般步骤有哪些？**
- 社交软件的市场分析
- 社交软件的功能分析
- 服务器的搭建
- 客户端的实现

**简述 socket 通信基础**
 - 所谓 socket 通常也称作”套接字“，用于描述 IP 地址和端口，是一个通信链的句柄。应用程序通常通过"套接字"向网络发出请求或者应答网络请求。 Socket 和 ServerSocket 类库位于 java.net 包中。ServerSocket 用于服务器端，Socket是建立网络连接时使用的。在连接成功时，应用程序两端都会产生一个 Socket 实例，操作这个实例，完成所需的会话。

**简述服务器、客户端通过 socket 方式连接服务器的方法**
- 服务器：使用 ServerSocket 监听指定的端口，等待客户连接请求，客户连接后，会话产生；在完成会话后，关闭连接。
- 客户端：使用 Socket 对网络上某一个服务器的某一个端口发出连接请求，一旦连接成功，打开会话；会话完成后，关闭 Socket。

**简述 Android 聊天客户端框架 listview 中 item 的两种处理方法**
- 使用 getItemViewType() 和 getViewTypeCount()，根据不同 type 显示不同的 item。 (聊天界面的左右聊天布局例如文字 item，图片 item，语音 item 等等，可以看 MessageAdapter.java 文件)。
- 建一个 itemview 的方法(不同风格定义不同的 java 文件)： 将 view 的处理和逻辑分散到另外一个文件中，也实现了不用 item 不同风格的功能。比如在 ItemView 包中，我们创建了 ImageGridSingleTypeView。 这个只需要在getLayoutResourceId()中设置 R.layout.xx 布局文件。然后再 initView（）初始化布局就好。 然后在 notifyDataChanged（）来设置每个 view 的数据。 这样的好处是可以分别处理，易于管理。不会让 adapter 的代码过于复杂。

**Thread 类代表线程类，它的两个最主要的方法是什么？**
- `start()`用于启动线程，而`run()`则定义了线程执行的任务

**在 android 中有两种实现线程 thread 的方法是什么？**
- 继承 Thread 类：创建自定义线程类继承 Thread，重写 run() 方法，并通过 start() 启动线程。
- 实现 Runnable 接口：定义 Runnable 接口的实现类，<span style="background:#f2634a">通过 Thread 构造函数传递 Runnable 实例并启动</span>。

**请简述 Handle 的作用**
- Handle 是 Android 中用于处理异步任务和消息传递的组件。通过 Handle，可以将耗时的操作放在子线程中执行，避免阻塞主线程。同时，Handler 还可以将子线程中的消息传递到主线程中进行处理，实现子线程与主线程之间的通信。

**Looper 中有 2 个比较重要的方法是什么？**
- 在 Android 中，`Looper` 是消息处理机制的核心组件，它通过 `prepare()` 和 `loop()` 两个方法来实现消息的创建和处理。`prepare()` 用于初始化 `Looper`，而 `loop()` 用于启动消息循环，确保消息能够被正确地分发和处理

**安卓三种线程同步方式是什么？**
- synchronized 关键字：通过对代码块或方法的修饰，确保同一时间只有一个线程可以访问被锁定的资源
- volatile 关键字：保证被修饰的变量的修改所有线程可见
- Lock 接口及其实现类：实现更加丰富的锁机制
