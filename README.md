<!-- TOC -->

- [代码整洁之道](#代码整洁之道)
    - [整洁代码](#整洁代码)
    - [有意义的命名](#有意义的命名)
    - [函数](#函数)
- [注释](#注释)
- [格式](#格式)
- [对象和数据结构](#对象和数据结构)
- [错误处理](#错误处理)
- [边界](#边界)
- [单元测试](#单元测试)
- [类](#类)
- [系统](#系统)
- [迭进](#迭进)
- [并发编程](#并发编程)

<!-- /TOC -->

# 代码整洁之道


---
## 整洁代码
- Leblanc ： Later equals never.
（勒布朗法则：稍后等于永不）

- 对代码的每次修改都影响到其他两三处代码。
- 修改无小事。
- 如同医生不能遵从病人的意愿，程序员遵从不了解混乱风险的经理的意愿，也是不专业的做法。
- 赶上期限的唯一方法，做的快的唯一方法，就是始终尽可能保持代码整洁。
- **破窗理论**：环境中的不良现象如果被放任存在，会诱使人们仿效，甚至变本加厉。==一幢有少许破窗的建筑为例，如果那些窗不被修理好，可能将会有破坏者破坏更多的窗户。最终他们甚至会闯入建筑内，如果发现无人居住，也许就在那里定居或者纵火。一面墙，如果出现一些涂鸦没有被清洗掉，很快的，墙上就布满了乱七八糟、不堪入目的东西；一条人行道有些许纸屑，不久后就会有更多垃圾，最终人们会视若理所当然地将垃圾顺手丢弃在地上==。这个现象，就是犯罪心理学中的破窗效应。结论：及时矫正和补救正在发生的问题。**启发**：影响的大小并不能改变行为错误的本质，别人的错误更不会是证明你无错的理由。
- 整洁的代码只做好一件事：整洁的代码力求集中。每个函数、每个类和每个模块都全神贯注于一事，完全不受四周细节的干扰和污染。
- 在意代码。
- 简单代码：能通过所有测试；没有重复代码；体现系统中的全部设计理念；包括尽量少的实体，比如类，方法，函数等。
- 不要重复代码，只做一件事，表达力，小规模抽象。
- 不读周边代码的话就没法写代码。编写代码的难度，取决于读周边代码的难度。
- 军规：让营地比你来时更干净。
- 练习，练习，练习
---

## 有意义的命名
- 名副其实：如果名称需要注释来补充，那就不算是名副其实。
- 避免误导：慎用-List；名称区分度要大；避免0,1,l,o,O。
- 做有意义的区分：以数字系列命名(a1,a2...aN)纯属误导。废话都是冗余，-Data,-Info等都属于冗余信息。
- 使用读得出来的名称
- 使用可搜索的名称：名称长短应与其作用域大小相对应。
- 避免使用编码：不必包含类型，不必使用前缀/后缀
- 避免思维映射：明确是王道。
- 类名应该是名词或名词短语
- 方法名应该是动词或动词短语（使用方法来初始化对象通常好于直接只用构造器，所以建议将构造器设置为private）
- 别扮可爱
- 言到意到。意到言到。
- 每个概念对应一个词：给每个抽象概念选一个词，并且一以贯之。
- 别用双关语：一词一意
- 使用解决方案领域名称
- 使用源自所涉问题领域的名称：优秀的程序员和设计师，其工作之一就是分离解决方案领域和问题领域的概念。
- 增加有意义的语境，如前缀
- 不要添加没用的语境：精确正是命名的要点
- 取好名字最难的地方在于需要良好的描述技巧和共有文化背景。
---

## 函数

- 短小：函数的第一规则。每行都不应该有150个字符那么长，函数也不该有100行那么长。函数的缩进层级不该多于一层。
- 只做一件事：如果函数只是做了该函数名下同一抽象层上的步骤，则函数还是只做了一件事。（判断函数是否不止做了一件事，还有就是看是否能再拆出一个函数，该函数不仅只是单纯地重新诠释其实现。只做一件事的函数无法被合理地切分为多个区段。）
- 每个函数一个抽象层级：我们想要让代码拥有自顶向下的阅读顺序。让代码读起来像是一系列自顶向下的TO起头段落是保持抽象层级协调一致的有效技巧。
- switch语句：多态--将switch语句埋到抽象工厂底下，不让任何人看大。
- 使用描述性名称
- 函数参数：参数越少越好，参数越少越便于理解
    - 一元函数的普遍形式：函数名称应能区分出来
        1. 问关于参数的问题，如boolean fileExist("myFile");
        2. 将参数转换为其他什么东西，在输出之：如InputStream fileOpen("myFile");
        3. 事件，有输入参数而无输出参数，程序将函数看做一个事件，使用该参数修改系统状态
    - 标识参数丑陋不堪，即如果标识为true将会这样做，标识为false将会这样做：向函数传入布尔值简直是骇人听闻的做法。
    - 二元函数：单个值的有序组成部分；可以把某个参数转换成当前类的成员变量，从而无需再传递它。
    - 三元函数：排序，琢磨，忽略的问题都会加倍体现，写三元函数之前一定要想清楚
    - 参数列表：一个数量可变的参数等同于一个参数
    - 函数命名应与参数形成动词/名词对，如writeField(name)
- 无副作用： 函数承诺只做一件事，但还是会做其他被藏起来的事，例如时序性耦合
- 输出参数：面向对象语言中对输出参数的大部分需求已经消失了。应避免使用输出参数，如果函数必须要修改某种状态，就修改所属对象的状态吧。
- 分隔指令与询问：函数要么做什么事(do)，要么回答什么事(boolean)，但二者不可兼得。
- 使用异常替代返回错误码：
    - 使用异常替代错误码返回错误码，错误处理代码就能从主路径代码中分离出来，得到简化；
        1. 抽离try/catch代码块：try/catch代码块丑陋不堪；最好把try和catch代码块的主体部分抽离出来，另外形成函数。
        2. 错误处理就是一件事：如果try在某个函数中存在，它就该是这个函数的第一个单词，而且在catch/finally代码块后面也不该有其他内容。
        3. Error.java依赖磁铁：返回错误码通常暗示某处有个类或是枚举定义了所有错误码。使用异常替代错误码，新异常就可以从异常类派生出来，无需重新编译或重新部署。
- 别重复自己：重复可能是软件中一切邪恶的根源。
- 结构化编程：每个函数、函数中的每个代码块都应该有一个入口，一个出口，遵循这些规则，意味着在每个函数中只该有一个return语句，循环中不能有break或continue语句，而且永永远远不能有任何goto语句。对于小函数，这些规则助益不大，只有在大函数中，这些规则才会有明显的好处。
- 如果写出这样的函数：先想什么就写什么，然后再打磨它。
- 小结：编程艺术是且一直就是语言设计的艺术。大师级程序员把系统当做故事来讲，而不是当做程序来写。如果你遵循这些规则，函数就会短小，有个好名字，而且被很好地归置。真正的目的在于讲述系统的故事，而你编写的函数必须干净利落的拼装到一起，形成一种精确而清晰的语言，帮助你讲故事。

---

# 注释

- 注释不能美化糟糕的代码
- 用代码来阐述
- 好注释：
    1. 法律信息：可指向一份标准许可或其他外部文档
    2.  提供信息的注释：
    3.  对意图的解释：
    4.  阐释：
    5.  警示：例如为什么用某种设计模式
    6.  TODO 注释
    7.  放大
    8.  公共API中的doc
- 坏注释：
    1. 喃喃自语
    2. 多余注释
    3. 误导性注释
    4. 循轨式注释
    5. 日志式废话
    6. 废话注释：用整理代码的决心替代创造废话的冲动吧
    7. 可怕的废话
    8. 能用函数或变量时就别用注释
    9. 位置标记：///////////////////(少用，只在有价值的地方用)
    10. 括号后面的注释
    11. 归属与命名
    12. 注释掉的代码
    13. html注释
    14. 非本地信息
    15. 信息过多
    16. 不明显的联系
    17. 函数头
    18. 非公共API中的javadoc
    19. 范例

----

# 格式

- 格式的目的：代码格式关乎沟通，而沟通是专业开发者的头等大事。
- 垂直格式：有可能用大多数为200行、最长500行的单个文件构造出色的系统(Fitness总长约为50000行)。（书中用到K线图）
    - 向报纸学习：名称应当简单一目了然，细节应该往下渐次展开，报纸由许多篇文章组成，多数短小精悍。
    - 概念间垂直方向上的区隔：空白行
    - 垂直方向上的靠近：
    - 垂直距离：关系密切的概念应该互相靠近，变量声明应尽可能靠近其使用位置，实体变量应该在类的顶部声明，若某个函数调用了另外一个，就应该把它们放到一起，而且调用者应该尽可能放在被调用者上面，概念相关的代码应该放到一起
    - 垂直顺序：自上向下，被调用的函数应该放在执行调用的函数下面
- 横向格式：应尽力保持代码行短小，遵循无需拖动滚动条到右边的原则，保持在80下最好，120最多。
    - 水平方向上的区隔与靠近：如=左右的空格字符，运算符号左右的空格
    - 水平对齐：
    - 缩进：源文件是一种继承结构，而不是一种大纲结构，要让这种范围式继承结构可见，依赖缩进。
    - 空范围：
- 团队规则：遵循团队规则，绝对不要用各种不同的风格来编写源代码
- 鲍勃大叔的格式规则：
- ---

# 对象和数据结构

- 数据抽象：隐藏实现关乎抽象，这并不只是用接口和/或赋值器、取值器就万事大吉。要以最好的方式呈现某个对象包含的数据，需要严肃思考。
- 数据、对象的反对称性：对象与数据结构之间的二分原理——过程式代码便于在不改动既有数据结构的前提下增加新函数。面向对象代码便于在不改动既有函数的前提下添加新类。过程式代码难以添加新数据结构，因为必须修改所有函数。面向对象代码难以添加新函数，因为必须修改所有类。
- 德墨忒尔律：模块不应了解它所操作对象的内部情形。
    - 该定律认为，类C的方法f只应该调用以下对象的方法：
        - C
        - 由f创建的对象
        - 作为参数传递给f的对象
        - 由C的实体变量持有的对象
        - 即方法不应调用由任何函数返回的对象的方法。（拒绝链式调用）
    - 火车失事：拒绝链式调用
    - 混杂：无论出于怎样的初衷，公共访问器及改值器都把私有变量公开化，诱导外部函数以过程式程序使用数据结构的方式使用这些变量。 这增加了增加新函数的难度，也增加了添加新数据结构的难度。
    - 隐藏结构
- 数据传送对象：DTO(Data Transfer Objects):是一个只有公共变量、没有函数的类；Active Record是一种特殊的DTO形式，拥有公共变量的数据结构，通常也会有类似save和find这样的可浏览方法。
- 小结：对象暴露行为，隐藏数据。数据结构暴露数据，没有明显的行为。
----

# 错误处理

- 错误处理很重要，但如果它搞乱了代码逻辑，就是错误的做法。
- 使用异常而非返回错误码：错误码搞乱了调用者代码
- 先写try-catch-finally语句:尝试编写强行抛出异常的测试，再往处理器中添加行为，使之满足测试要求。结果就是你要先构造try代码块的事务范围，而且也会帮助你维护好该范围的事务特征。
- 使用不可控异常：可控异常的代价就是违反开放/闭合原则
> 如果你在方法中抛出可控异常，而catch语句在三个层级之上，你就得在catch语句和抛出异常之间的每个方法签名中声明该异常
- 给出异常发生的环境说明：你抛出的每个异常，都应当提供足够的环境说明，以便判断错误的来源和处所。在java中，你可以从任何异常里得到堆栈踪迹，然而堆栈踪迹却无法告诉你该失败操作的初衷。如果你的应用程序有日志系统，传递足够的信息给catch块，并记录下来。
- 依调用者需要定义异常类：
- 定义常规流程：业务逻辑和错误处理代码之间就会有良好的间隔；你来处理特例，客户代码就不用应付异常行为了，异常行为被封装到特例对象中。
> 特例模式(Special Case Pattern)：创建一个类或配置一个对象，用来处理特例。
- 别返回null值：
- 别传递null值：
- 小结：将错误处理隔离对待，独立于主要逻辑之外，就能写出强固而整洁的代码

----

# 边界

- 保持软件边界整洁
- 使用第三方代码：如果你使用类似Map这样的边界接口，就把它保留在类或近亲类中。避免从公共API中返回边界接口，或将边界接口作为参数传递给公共API。（即进一步封装公共API，放置公共API改动时，需要系统做大范围修改）
- 浏览和学习边界：
- 8.3没有
- 学习性测试的好处不只是免费:
- 使用尚不存在的代码：编写我们想得到的接口，好处之一是它在我们控制之下。
- 整洁的边界：在使用我们控制不了的代码时，必须加倍小心投资，确保未来的修改不至于代价太大。应该避免我们的代码过多地了解第三方代码中的特定信息。依靠你能控制的东西，好过依靠你控制不了的东西，免得日后受他控制。我们通过代码中少数几处引用第三方接口的位置来管理第三方边界；也可以使用ADAPTER模式将我们的接口转换为第三方提供的接口。在边界两边推动内部一致的用法，当第三方代码有改动时，修改点也会更少。

-----

# 单元测试

- TDD三定律：
    - 在编写不能通过的单元测试前，不可编写生产代码。
    - 只可编写刚好无法通过的单元测试，不能编译也算不通过。
    - 只可编写刚好足以通过当前失败测试的生产代码
- 保持测试整洁：测试代码和生产代码一样重要。
- 整洁的测试：构造->操作->检验 (Build->Operate->check):
> 构造测试数据；操作测试数据；检验操作是否得到期望的结果
- 守规矩的开发者将它们的测试代码重构为更简洁和具有表达力的形式。
- 双重标准：测试代码应当**简单，精悍，足具表达力**。双重标准指的是在关乎内存或CPU效率的问题。
- 每个测试一个断言：每个测试函数都应该有且只有一个断言语句，或者说，单个测试中的断言数量应该最小化，每个测试函数只测试一个概念。
- F.I.R.S.T. : 快速（Fast）, 独立(Independent), 可重复(Repeatable), 自足验证(Self-Validating), 及时(Timely)。
> 测试应该够快：测试运行缓慢你就不会想要频繁的运行它；测试应该相互独立；测试应当可在任何环境中重复通过；测试应该有布尔值输出，你不应该查看日志来确认是否通过，不应该手工对比两个不同文本来确认测试是否通过；测试应及时编写：单元测试应该恰好在使其通过的生产代码之前编写。
- 小结：如果你坐视测试腐败，那么代码也会跟着腐坏。


------

# 类

- 类的组织：公共静态常量-> 私有静态常量 -> 私有实体变量 -> 最好没有公共变量 -> 公共函数
- 对于封装：测试说了算
- 类应该短小：类的第一条规则是类应该短小；第二条规则是还要更短小。对于函数，我们通过计算代码行数衡量大小。对于类，我们通过计算权责(Responsibility)来衡量。
    - 单一权责原则(SRP)：类或模块应有且只有一条加以修改的理由——类只应有一个权责，只有一条修改的理由。让软件能工作和让软件保持整洁，是两种截然不同的工作；SRP在编程行为中的重要程度等同于在程序中的重要程度。
    - 每个达到一定规模的系统都会包括大量逻辑和复杂性，管理这种复杂性的首要目标是加以组织，以便开发者知道到哪能找到东西，并且在某个特定时间只需要理解直接有关的复杂性。
    - 系统应该由许多短小的类而不是少量的巨大类组成。每个类封装一个权责，只有一个修改的原因，并与少数其他类一起协同达成期望的系统行为。
- 内聚：内聚性高，意味着类中的方法和变量互相依赖、互相结合成一个逻辑整体。
- 保持内聚性就会得到许多短小的类：当类失去了内聚性，就拆分它。
- 每改动一次，就执行一次，确保程序的行为没有发生变化。
- 为了修改而组织：在整洁的系统中，我们对类加以组织，以降低修改的风险。开放-闭合原则(OCP)：类应当对扩展开放，对修改封闭。我们希望将系统打造成在添加或修改特性时尽可能少惹麻烦的架子。在理想的系统中，我们通过扩展系统而非修改现有代码来添加新特性。
- 隔离修改：需求会改变，所以代码也会改变。具体类包含实现细节，而抽象类则只呈现概念。可以借助接口和抽象类来隔离这些细节带来的影响。
> 部件之间的解耦代表着系统中的元素相互隔离得很好。
- 降低连接度，我们的类就遵循了另一个类设计原则：依赖倒置原则
> 依赖倒置原则(Dependency Inversion Principle, DIP):类应当依赖于抽象而不是依赖于具体细节。程序要依赖于抽象接口，不要依赖于具体实现。简单的说就是要求对抽象进行编程，不要对实现进行编程，这样就降低了客户与实现模块间的耦合。

------

# 系统

    复杂要人命。它消磨开发者的生命，让产品难以规划、构建和测试。
        ---------------------(Ray Ozzie, 微软公司首席技术官)

- 如何建造一个城市：整洁的代码帮助我们在较低层的抽象层级上达成这一目标。本章将讨论如何在较高的抽象层级——系统层级——上保持整洁。
- 将系统的构造和使用分开：软件系统应将启动过程和启动过程之后的运行时逻辑分离开，在启动过程中构建应用对象，也会存在相互缠结的依赖关系。
- 分解main：将构造与使用分开的方法之一是将全部构造过程搬迁到main或被称之为main的模块中，设计系统的其余部分时，假设所有对象都已正确构造和设置。
- 工厂：抽象工厂模式让应用自行控制何时创建实体。
- 依赖注入，控制反转：分离构造和使用。控制反转将第二权责从对象中拿出来，转移到另一个专注于此的对象中，从而遵循了单一权责原则。***什么是依赖注入？***
- 扩容：“一开始就做对系统”纯属神话。反之，我们应该只去实现今天的用户故事，然后重构，明天再扩展系统，实现新的用户故事。这就是迭代和增量敏捷的精髓所在。测试驱动开发、重构以及他们打造出的整洁代码，在代码层面保证了这个过程的实现。
> 软件系统与物理系统可以类比。它们的架构都可以递增式地增长，只要我们持续将关注面恰当地切分。
    - 横贯式关注面：原则上，你可以从模块、封装的角度推理持久化策略。但在实践上，你却不得不将实现了持久化策略的代码铺展到许多对象中。
    
    Java中的三个“方面”：
        - Java代理：适用于简单的情况，例如在单独的对象或类中包装方法调用。
- 纯JAVA AOP框架：Spring AOP, JBoss AOP
- AspectJ的方面：AspectJ提供了一套用以切分关注面的丰富而强有力的工具。
- 测试驱动系统架构：通过方面式手段切分关注面的威力不可低估，假使你能用POJO编写应用程序的领域逻辑，在代码层面与架构关注面分离开，就有可能真正地***用测试来驱动架构***。采用一些新技术，就能将架构按需从简单演化到精细。没必要***先做大设计***（Big Design Up Front, BDUF）。实际上，BDUF甚至是有害的，它阻碍改进，因为心理上会抵制丢弃既成之事，也因为架构上的方案选择影响到后续的设计思路。
> 最佳的系统架构由模块化的关注面领域组成，每个关注面均用纯Java(或其他语言)对象实现。不同的领域之间用最不具有侵害性的方面或类方面工具整合起来。这种架构能测试驱动，就像代码一样。

- 优化决策：模块化和关注面切分成就了分散化管理和决策。最好是授权给最有资格的人，延迟决策至最后一刻也是好手段，让我们能够基于最有可能的信息作出选择。提前决策是一种预备知识不足的决策。如果决策太早，就会缺少太多客户反馈、关于项目的思考和实施经验。
> 拥有模块化关注面的POJO系统提供的敏捷能力，允许我们基于最新的知识做出优化的、时机刚好的决策。决策的复杂性也降低了。
- 明确使用添加了可论证价值的标准：有了标准，就更易复用想法和组件、雇用拥有相关经验的人才、封装好点子，以及将组件连接起来。不过，创立标准的过程有时却漫长到行业等不及的程度，有些标准没能与它要服务的采用者的真实需求相结合。
- 系统需要领域特定语言：领域特定语言允许所有抽象层级和应用程序中的所有领域，从高级策略到底层细节使用POJO来表达。
- 小结：系统应该是整洁的。侵害性架构会湮灭领域逻辑，冲击敏捷能力。在所有的抽象层级上，意图都应该更加清晰可辨。只有在编写POJO并使用类方面的机制来无损地组合其他关注面时，这种事情才会发生。
> 无论是设计系统或单独的模块，别忘了使用***大概可工作的最简单方案***。

-------

# 迭进

- 通过迭进设计达到整洁目的：根据Kent所述的***简单设计***的四条规则，只要遵循以下规则，设计就能变得“简单”：
    - 运行所有测试：设计必须制造出如预期一般工作的系统，这是首要因素。OO的目标是低耦合度，高内聚度。有了测试，就能保证代码和类的整洁，方法就是递增式地重构代码。***测试消除了对清理代码就会破坏代码的恐惧***。（提高内聚性，降低耦合度，切分关注面，模块化系统关注面，缩小函数和类的尺寸，选用更好的名称...）
    - 不可重复：重复是拥有良好设计系统的大敌。
    - 表达力：软件项目的主要成本在于长期维护。作者把代码写的越清晰，其他人花在理解代码上的时间也就越少，从而减少缺陷，缩减维护成本。做到有表达力的最重要的方式是***尝试***。
    - 尽可能减少类和方法的数量：运用以上三个规则可能导致过多的类和方法，此条规则优先级最低。尽管使类和函数的数量尽量少是很重要的，但更重要的却是测试、消除重复和表达力。
- 小结：不会有能替代经验的一套简单实践手段。

------

# 并发编程

> 对象是过程的抽象。线程是调度的抽象。

- 为什么要并发：并发是一种解耦策略。它帮助我们把做什么(目的)和何时(时机)做分解开。解耦目的与时机能明显地改进应用程序的吞吐量和结构。应用程序看起来更像是许多台协同工作的计算机，而不是一个大循环。例如Servlet，当有web请求时，servlet就会异步执行，每次Servlet是在自己的小世界中执行，与其他servlet的执行是分离的。
    - 并发会在性能和编写额外代码上增加一些开销；
    - 正确的并发是复杂的，即便对于简单的问题也是如此；
    - 并发缺陷并非总能重现，所以常被看做偶发事件而忽略，未被当做真的缺陷看待；
    - 并发常常需要对设计策略的根本性修改。
- 挑战：需要理解Just-In-Time编译器如何对待生成的字节码，理解Java内存模型认为什么东西具有原子性。
- 并发防御原则：
    1. 单一权责原则(SRP)：方法、类、组件应当只有一个修改的理由。并发设计自身足够复杂到成为修改的理由，所以也该从其他代码中分离出来。***建议：分离并发相关代码与其他代码***
        1. 并发相关代码有自己的开发、修改和调优生命周期；
        2. 并发相关代码有自己要对付的挑战，和非并发相关代码不同，而且往往更为困难；
        3. 即便没有周边应用程序增加的负担，写的不好的并发代码可能的出错方式数量也已经足具挑战性。
    2. 推论：限制数据作用域——采用synchronized关键字在代码中保护一块使用共享对象的***临界区***。限制临界区的数量很重要。***建议：谨记数据封装，严格限制对可能被共享的数据的访问。***
    3. 推论：使用数据复本：避免共享数据的好方法之一就是一开始就避免共享数据。如果有避免共享数据的简易手段，结果代码就会大大减少导致错误的可能。
    4. 推论：线程应尽可能地独立：让每个线程在自己的世界中存在，不与其他线程共享数据。***建议：尝试将数据分解到可被独立线程(可能在不同处理器上)操作的独立子集。***
- 了解Java库：
    - 使用类库提供的线程安全群集;
    - 使用executor框架执行无关任务;
    - 尽可能使用非锁定解决方案;
    - 有几个类并不是线程安全的。
    1. 线程安全群集：