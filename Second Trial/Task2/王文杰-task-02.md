<!-- title: Gamecore 2023夏季考核 -->      
# 第二次考核任务
## C#初级编程笔记
* 定义变量/函数的方式、语法、if语句、switch语句、(do)while循环、for循环 基本等同于C/C++ 。
* C#中定义数组的方式为 数据类型[] 数组名 = new 数据类型 [数组长度]，在定义的同时可以初始化。
   * 实例
      ``` C#
          int[] myIntArray1 = new int [5];
          myIntArray[1] = 10; //定义后给元素赋值
          int[] myIntArray2 = {12,76,8,937,903}; //定义并初始化
      ```
   * 使用 GameObject.FindGameObjectsWithTag() 得到所有为指定 Tag 的游戏对象组成的数组。
* foreach是C#中新的循环，语法为foreach(数据类型  变量名  in  集合名) （常用于数组）。
   * 该循环的运行过程如下：每一次循环时，从集合中取出一个新的元素值。放到只读变量中去，如果括号中的整个表达式返回值为 true，foreach 块中的语句就能够执行。
   * 一旦集合中的元素都已经被访问到，整个表达式的值为 false，控制流程就转入到 foreach 块后面的执行语句。
   * 实例
      ``` C#
          string[] strings = new string [3];
          strings[0] = "First string";
          strings[1] = "Second string";
          strings[2] = "Third string";
          foreach(string item in strings)    // 输出strings数组中的三个元素
          {
              print (item);
          }
      ```
* Debug.Log() 函数可以在控制台处显示()内的内容（字符串，变量的值等）。
* 句号运算符( . )用于分隔或访问Unity中复合项（包含多个元素的项）的各个元素。
* 访问修饰符是在声明变量时放在数据类型前的关键词，用途是定义能够看到变量或函数的位置。
   * public（公开变量）表示此变量可从类外部访问，也意味着可在Inspector中的组件上显示和编辑。（注：Inspector中的值会覆盖初始化的值）。
   * private（私有变量）表示此变量只能在类内编辑，所有未指定访问修饰符的变量默认使用它。
* Awake函数即使脚本组件未启用也会执行，Start函数只有在脚本组件启用也会执行。两者都只调用一次。
* FixedUpdate() 函数在调用之后会立即进行任何必要的物理计算，因此任何影响刚体（即物理对象）的动作应使用它执行。
   * 使用FixedUpdate() 定义移动时最好使用力来实现。
* Vector3.Dot(VectorA,VectorB) 函数用于求两个三维向量（Vector3）的点积（两向量的x,y,z分别两两相乘后相加的值）。
* Vector3.Cross(VectorA,VectorB) 函数用于求两个三维向量（Vector3）的叉积（即法向量，与两向量垂直）。
* Enabled标记（组件名.enabled）用于启用/禁用组件。
   * 例如
     ``` C#
         myLight.enabled = true;
     ```
* gameObject.SetActive() 函数用于启用（True）/停用（False）游戏对象。
   * 当父对象停用时，子对象无论是否启用，都不会激活。
* Translate() 函数用于平移，参数为三维矢量（Vector3），沿x,y,z轴移动相应距离。
* Rotate() 函数用于旋转，参数为三维矢量（Vector3），以x,y,z轴为轴旋转相应角度。
* Input.GetKey(KeyCode.键位) 用于判断是否按下某个键（返回 Bool 值）。
   * GetKey 按下的那一帧为True，剩下时间为False。
   * GetKeyDown 按住的时候为True（包括按下的第一帧），剩下时间为False。
   * GetKeyUp 按键松开的那一帧为True，剩下时间为False。
   * 可用 Button 替换 Key 来使用 Unity 定义的按键而非键盘按键。
   * [键位一览](https://zhuanlan.zhihu.com/p/593749605?utm_id=0)
* OnMouseDown() （生命周期）函数用于检测对 碰撞体（collider）或 GUI 文本的点击。
* Input.GetAxis() 用于在按下键后返回一个-1到1的 float 值（按一定速度变化，类似于滑尺），以下为一些设置作用。
   * Gravity 影响松开按钮后数值归0的速度。
   * Sensitivity 与 Gravity 相反，影响到达-1或1的速度。
   * Dead 影响盲区，一般用于操纵杆，使其在一定移动幅度下才改变值。
   * Snap 勾选后可使正负按钮同时按下后归0。
   * 使用 Input.GetAxisRaw() 将仅返回整数。
* Time.deltaTime的值为1帧的间隔时间。
   * 故在 Update() 函数使用 Time.deltaTime 会让变化改为每秒一次。
* transform.LookAt()用于让对象看向目标对象。
* 线性插值Lerp
   * Mathf.Lerp(float a,float b,float c)函数输出位于a到b之间的c处（c为百分比）。
   * Color.Lerp()函数和Vector3.Lerp()函数原理相同，也需要3个参数。
* Destroy()函数用于摧毁游戏对象或组件，并可添加第二个参数作为延迟时间（单位秒）。
* 利用GetComponent<>()函数可以调用其他脚本的变量和函数，或者调用Unity中组件。
   * 注意：在对其他脚本引用时，若要定义变量存储，则其类型应为为被定义的脚本名称（因为实际上应用的是这个脚本中被定义的类）。
      * 例如
       ``` C#
           private AnotherScript a; //AnotherScript为另一脚本名（仍是此对象的组件）
           void Start()
           {
                a = GetComponent<AnotherScript>(); //调用此游戏对象的其他脚本
           }
       ```
      * 若改为a = otherGameObject.GetComponent< YetAnotherScript >(); 可指定其他游戏对象中的此脚本组件。
* 变量的数据类型主要分为值类型（Value）和引用类型（Reference）两大类。
   * 值类型：包含 int float double char bool 等。还包括复杂的 Structs （包含一个或多个其他变量），它们只包含某个值（影响此变量只会影响它自己）。
      * 常用的 Structs 有 Vector3 Quaternion。
   * 引用类型：属于类对象（Class）的变量基本都属于此类型，包含值存储位置的地址（影响此变量会影响对应地址内的内容 *类似于C的指针？*）。
      * 常用的引用类型有Transform Gameobject。
* 类（Class）是一个容器，用来存储变量在和函数。创建脚本时会自动输入一个类，与脚本名同名（修改其一个的名称则另一个也需修改）。
   * 定义存储类的变量时类型应与类名称相同。
   * 可以使用构造函数改变类中的变量的值。
      * 构造函数的名称始终是类的名称，构造函数一定没有返回的数据类型（包括void）。
      * 一个类可以有多个不同的构造函数，但对象初始化时只会调用其中一个构造函数。
* Instantiate() 函数用于克隆游戏对象，其可包含3个参数，分别为克隆对象，生成位置和旋转。
* Invoke() 函数用于将函数调用安排在指定延迟后执行一次，包含2个参数（字符串和浮点数），被调用的函数和字符串的内容一致，第二个参数作为延迟时间（单位秒）。
   * 可以使用 InvokeReapting() 函数以重复执行被指定函数，需要第三个参数作为每次重复的间隔时间（单位秒）。
   * 可以使用 CancelInvoke() 函数终止所有 Invoke 相关函数或以字符串作为参数来停止某个被调用函数的 Invoke 相关函数。 
* 枚举（enum）可用于创建相关常量的集合，这是一种特殊的数据类型。
   * 默认情况下，枚举中的第一个变量被赋值为0，其他的变量的值按顺序递增（1,2,3...）。
   * 实例
      ``` C#
      enum Direction {North, East, South, West}; //North为0，East为1，以此类推
        void Start () 
    {
        Direction myDirection;
        myDirection = Direction.North; //myDirection值为0
    }
      ```
## MonoBehavior生命周期笔记
### 生命周期相关：
> Awake - 始终在任何 Start 函数之前并在实例化预制件之后调用此函数，只调用一次。
> OnEnable - 当对象已启用并处于活动状态时调用此函数。
> OnDisable - 当行为被禁用或处于非活动状态时调用此函数。
> OnDestroy - 当 MonoBehaviour 将被销毁时调用此函数。
### 帧更新相关：
> Start - 在游戏对象开始存在时（加载场景或实例化游戏对象时），在首次帧更新之前调用，只调用一次。   
> Update - 仅在激活时，每帧都会被调用。    
> LateUpdate - 仅在激活时，每一帧都将调用。保证晚于所有Update后。
> FixedUpdate - 仅在激活时，每个物理时间步进调用，时间间隔相同（默认0.02秒）。    
> OnGUI -  渲染和处理 GUI 事件时调用 OnGUI（每帧调用两次）。
### 触发器碰撞相关：
> OnTriggerEnter(Collider other) - 如果另一个碰撞器进入了触发器，则调用。
> OnTriggerExit(Collider other) - 如果另一个碰撞器停止接触触发器，则调用。
### 刚体碰撞相关：
> OnCollisionEnter(Collision collision) - 当此碰撞器/刚体开始接触另一个刚体/碰撞器时，调用。
> OnCollisionExit(Collision collision)	// 当此碰撞器/刚体停止接触另一刚体/碰撞器时，调用。  
## 几个回答
1. 你的自我介绍
   > 大家好!我是来自物联网2302的王文杰，很高兴来到Gamecore游戏工作室。本人Unity基础为零，编程也是近期才开始学习(._.`)。尽管能力有限，对游戏的热爱会支持我不断学习进步:D。希望在将来与大家共同学习游戏开发，与大家共同进步，努力提升编程水平，做出一款属于自己的好游戏（⌒▽⌒）
2. 你最喜欢的游戏类型和一款游戏，以及原因    
   > 我最喜欢的游戏类型以2D游戏为主，有平台跳跃、Rougelike、沙盒等。
   > 我最喜欢的一款游戏是Celeste。其优秀的操作手感，引人入胜的剧情，独特的像素风格和精心设计的游戏地图是它最大的亮点。虽然其操作机制简单，却能拓展出许多特别的技巧，并与优秀的地图设计完美配合。游戏的难度不低，但犯错的代价同时也很小，这使玩家有信心攻克难关，并能在过关时获得很大的成就感。以上便是我喜欢它的原因。
3. 回答Unity中有哪些生命周期函数，它们各自在什么时候调用
   > 见上方MonoBehavior生命周期笔记   
4. 你本周的基础知识学习笔记
   > 见上方笔记
5.思考问题答案
``` C#
    public class HpBuff : Buff //继承于Buff类 而不是默认的 MonoBehaviour 类
    {
        public float DeltaHp = 10f; //增加的血量
        public HpBuff(Player player, BuffKind buffKind, float length) : base(player, buffKind, length) { } //构造函数传参
        public override void OnAdd() //重写父类OnAdd()函数
        {
            base.OnAdd();
            m_Player.Hp += DeltaHp; //增加玩家对象的血量
        }
    }
```
