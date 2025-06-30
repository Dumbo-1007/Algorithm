---
tags:
  - Android
---
---
## 应用组件

![[Pasted image 20250303205635.png]]
- ### ***Activities***
	一个活动标识一个具有用户界面的单一屏幕。==举个例子==，一个邮件应用程序可以包含一个活动用于显示新邮件列表，另一个活动用来编写邮件，再一个活动来阅读邮件。当应用程序拥有多于一个活动，其中的一个会被标记为当应用程序启动的时候显示。
	一个活动是**Activity**类的一个子类，如下所示：
```Java
public class MainActivity extends Activity {

}
```
- ### ***Services***
	服务是运行在后台，执行长时间操作的组件。==举个例子==，服务可以是用户在使用不同的程序时在后台播放音乐，或者在活动中通过网络获取数据但不阻塞用户交互。
	一个服务是**Service**类的子类，如下所示：
```Java 
public class MyService extends Service {

}
```
- ### ***Broadcast Receivers***
	广播接收器简单地响应从其他应用程序或者系统发来的广播消息。==举个例子==，应用程序可以发起广播来让其他应用程序知道一些数据已经被下载到设备，并且可以供他们使用。因此广播接收器会拦截这些通信并采取适当的行动。
	广播接收器是**BroadcastReceiver**类的一个子类，每个消息以**Intent**对象的形式来广播。
```Java 
public class MyReceiver  extends  BroadcastReceiver {

}	
```
- ### ***Content Providers***
	内容提供者组件通过请求从一个应用程序到另一个应用程序提供数据。这些请求由**ContentResolver**类的方法来处理。这些数据可以是存储在文件系统、数据库或者其他其他地方。内容提供者是**ContentProvider**类的子类，并实现一套标准的API，以便其他应用程序来执行事务。
```Java
public class MyContentProvider extends  ContentProvider {

}
```
---
## 附件组件

- 有一些附件的组件用于以上提到的实体、他们之间逻辑、及他们之间连线的构造。这些组件如下：
![[Pasted image 20250303210541.png]]

---