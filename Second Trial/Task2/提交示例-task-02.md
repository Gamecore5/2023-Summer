<!-- title: Gamecore 2023夏季考核 -->   
# 第二次考核任务提交例子
## C#初级编程笔记
* 利用GetComponent<>()函数可以调用其他脚本的变量和函数，或者调用Unity中组件。   
    ``` C# 
    private YetAnotherScript yetAnotherScript;
    yetAnotherScript = otherGameObject.GetComponent<YetAnotherScript>();
    Debug.Log("The player has died " + yetAnotherScript.numberOfPlayerDeaths + " times");
    ```
    ``` C#
    public class YetAnotherScript : MonoBehaviour
    {
        public int numberOfPlayerDeaths = 3;
    }
    ```   
## MonoBehavior生命周期笔记
> Start - 在游戏对象开始存在时（加载场景或实例化游戏对象时）调用。   
> Update - 每帧都会被调用。    
> FixedUpdate - 每个物理时间步进调用。    
## 思考题：
``` C#
    public class HpBuff: Buff
    {
        //思考HpBuff类该怎么写，可以参考上方的SpeedBuff，自己尝试写写并是否能在游戏中运行
        //....Your Answer....
    }
```
## 几个回答
1. 你的自我介绍
   > 大家好!我是来自计算机2201的XXX，很高兴来到Gamecore游戏工作室，与大家共同学习游戏开发，期待与大家共同进步，携手做出一款属于自己的好游戏<(￣︶￣)↗[GO!]    
2. 你最喜欢的游戏类型和一款游戏，以及原因    
   > 我最喜欢的游戏就是XXX,喜欢这款游戏的原因很简单，因为这游戏很好玩
3. 回答Unity中有哪些生命周期函数，它们各自在什么时候调用
   > 见上方MonoBehavior生命周期笔记   
4. 你本周的基础知识学习笔记
   > 见上方笔记
## 附加内容：此md文档的源码(参考学习，提交时不需要附带源码)
``` Markdown
<!-- title: Gamecore 2022秋季考核 -->   
# 第二次考核任务提交例子
## C#初级编程笔记
* 利用GetComponent<>()函数可以调用其他脚本的变量和函数，或者调用Unity中组件。   
    ``` C# 
    private YetAnotherScript yetAnotherScript;
    yetAnotherScript = otherGameObject.GetComponent<YetAnotherScript>();
    Debug.Log("The player has died " + yetAnotherScript.numberOfPlayerDeaths + " times");
    ```
    ``` C#
    public class YetAnotherScript : MonoBehaviour
    {
        public int numberOfPlayerDeaths = 3;
    }
    ```   
## MonoBehavior生命周期笔记
> Start - 在游戏对象开始存在时（加载场景或实例化游戏对象时）调用。   
> Update - 每帧都会被调用。    
> FixedUpdate - 每个物理时间步进调用。         
## 思考题：
    ``` C#
    public class HpBuff: Buff
    {
        //思考HpBuff类该怎么写，可以参考上方的SpeedBuff，自己尝试写写并是否能在游戏中运行
        //....Your Answer....
    }
    ```
## 几个回答
1. 你的自我介绍
   > 大家好!我是来自计算机2201的XXX，很高兴来到Gamecore游戏工作室，与大家共同学习游戏开发，期待与大家共同进步，携手做出一款属于自己的好游戏<(￣︶￣)↗[GO!]    
2. 你最喜欢的游戏类型和一款游戏，以及原因    
   > 我最喜欢的游戏就是XXX,喜欢这款游戏的原因很简单，因为这游戏很好玩
3. 回答Unity中有哪些生命周期函数，它们各自在什么时候调用
   > 见上方MonoBehavior生命周期笔记   
4. 你本周的基础知识学习笔记
   > 见上方笔记
```