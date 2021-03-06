# 万能回调接口框架CallbackFrame
[ ![Download](https://api.bintray.com/packages/itxiaox/maven/callbackframe/images/download.svg) ](https://bintray.com/itxiaox/maven/callbackframe/_latestVersion)


## [官网](https://itxiaox.github.io/CallbackFrame)

## 1. 功能介绍

     一个针对Callback的封装框架，可以用于fragment之间的通讯，解决在Activity中有多个Fragment中相互通信的问题，
  
## 2. 使用方法
 
* gradle 引用

在根gradle中添加
```
allprojects {
    repositories {
        jcenter()
        maven {
            url 'https://dl.bintray.com/itxiaox/maven/'
        }
    }
}
```
在module 中添加依赖
```
compile 'com.itxiaox:callbackframe:1.0.1'
```

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

## 3. 实现思路原理

1. 它是一个万能接口，通过此接口可以体会到接口封装的艺术，它的核心思路是将回调接口当做对象来说使用，将方法提取出来进行管理，充分的运用OOP万物皆对象的思想。

2. 对于任何一个方法根据方法的参数和返回值进行组合有以下四种表现形式:
	* 无参数无返回值
	* 有参数有返回值
	* 有参数无返回值
	* 无参数有返回值

3. 对于通用方法的参数和类型是不固定的，所以通用的框架设计时候采用泛型
4. EventBus 的实现也是类似这样的，EventBus真正的核心也是 将方法提取出来进行管理， 采用反射的原理
    
[参考视频](https://study.163.com/course/courseLearn.htm?courseId=1209230809#/learn/live?lessonId=1278875538&courseId=1209230809) 


# LICENSE

	Copyright 2018 Xiaox




	Licensed under the Apache License, Version 2.0 (the "License");
	you may not use this file except in compliance with the License.
	You may obtain a copy of the License at

	   http://www.apache.org/licenses/LICENSE-2.0

	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS,
	WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
	See the License for the specific language governing permissions and
	limitations under the License.


