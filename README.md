# networkNotify
网络状态实时监听

使用方法
1、在BaseApplication中初始化  NetworkManager.getInstance().init(this);
2、在需要监听网络的activity或者fragment中调用方法 ，注册进去 NetworkManager.getInstance().registerObserval(this);当网络有变化时需要在该类中添加一个注解方法
举个例子：
@NetAnnotation(netType = NetType.WIFI)
    public void netChange(NetType str){
        if(NetType.WIFI == str){
            Log.e("wifi2222---->",str.toString());
            Toast.makeText(this,"链接wifi成功",Toast.LENGTH_SHORT).show();
        }
    }
方法名称和接受的网络类型可以自己控制。
3、当我们把app销毁的时候需要调用 NetworkManager.getInstance().removeAllObserval();移除掉所有的监听，对于7.0以下手机进行取消广播的操作
4、当前activity不需要监听的时候需要调用 NetworkManager.getInstance().registerObserval(this);
