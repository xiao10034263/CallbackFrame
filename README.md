# CallbackFrame

## 1. 思路和功能

    1. 一个针对Callback的封装框架，可以用于fragment直接进行通讯，
    2. 是一个万能接口，通过此接口可以体会到接口封装的艺术，讲一个方法当做一个对象来使用。
``
     * 抽象出回调接口的通用模型，总共有四种类型
     * 然后根据参数和返回值组合，有四种：
     1）无参数无返回值
     2）有参数有返回值
     3）有参数无返回值
     4）无参数有返回值

    3. 可以通过这个通用接口实现Fragment之间的通讯
    4. EventBus 的实现也是类似这样的，EventBus真正的核心也是 将方法提取出来进行管理， 采用反射的原理
## 2. 使用方法
 
* gradle 引用

在根gradle中添加
```
allprojects {
    repositories {
        jcenter()
        maven {
            url 'https://dl.bintray.com/baichuang/maven/'
        }
    }
}
```
在module 中添加依赖
`compile 'com.baichuang:callbackframe:1.0.0'`
   

* 代码示例
```
/**
 * 回调处，
 *  将方法添加保存起来
 */

FunctionManager.getInstance().addFunction(new FunctionWithParamWithResult<String,String>("functionName") {
    @Override
    protected String function(String result) {
        System.out.println("callback-回调处理");
        return "callback:"+result;
    }
});
/**
 * 执行调用
 */
String result = FunctionManager.getInstance().invokeFunction("functionName","Hello World");
System.out.println("调用处"+result);
```
   