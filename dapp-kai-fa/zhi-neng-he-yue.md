# 智能合约

## 智能合约的逻辑

什么是智能合约？它们是存储在区块链上的计算机程序，让我们能够将传统合约转换成数字化合约。 智能合约完全符合逻辑 — 遵循 IFTTT （if this then that）逻辑结构。 它是开源的、可预测、被自动执行的程序代码。该代码被部署到以太坊上之后，在以太坊虚拟机的交易的上下文中，被执行（智能合约不能自动或者后台运行）。那么智能合约有什么特征呢：

1. 可执行的代码：智能合约只是计算机可执行代码，由高级的智能合约语言（Solidity）编译而来的，被编译成EVM（以太坊虚拟机）可执行的低级代码，类似java语言和JVM。
2. 法律意义：智能合约不具备法律意义，其最终执行是由去中心化的以太坊EVM在交易的上下文中，被执行调用。
3. 不变性：由于以太坊的去中心化，智能合约一旦被部署之后，不能再修改，修改智能合约的唯一方式发布新的智能合约实例，这里跟软件发布类似，如果老的版本有问题，必须发布新的版本。其中有些许差异：智能合约是无法下掉老版本的，但可以执行一个名为 SELFDESTRUCT（以前称为 SUICIDE）的 EVM 操作码来删除代码和内部状态，只留下一个空白账户。删除合约后发送到该帐户地址的任何交易都不会导致任何代码执行，因为那里不再有任何代码可执行。
4. 确定性：智能合约是IFTTT逻辑的可执行代码，除非是**编写BUG、被攻击**，不然在交易上下午中，其执行结果是确定的。
5. 不可抵赖性：EVM 在每个以太坊节点上作为本地实例运行，但由于 EVM 的所有实例都在相同的初始状态下运行并产生相同的最终状态，因此整个系统作为一个“世界计算机”运行。由于智能合约是分布式多节点执行，所以要具备幂等性、原子性，整个智能合约的幂等性、原子性由以太坊来保证。
6. 公开性：智能合约是部署在以太坊公链上，任何人都可以对合约条款进行审查，可以立即跟踪资产转移和其他相关信息。但公开性，不能说明不可违约。如果双方交易物都是以太坊上的物品，比如以太坊币和NFTs，那么确实是不可违约的。因为在交易之前可以审查去合约代码，确保条款是正确的，同时在审查代码是否有BUG，在条款和代码是正确的，按照合约的机制，在交易的上下文中，合约被EVM调用，而且这种调用是不受控制的，即整个以太坊系统在去中心化地调用。

智能合约可以理解为“承诺的程序化”，假如A与B进行交易，那如何确保A与B的交易不可违约呢？

| 交易方 | 传统方式                                     | 智能合约                           |
| --- | ---------------------------------------- | ------------------------------ |
| A   | 非赊账（一手交钱）                                | A通过EOA 向智能合约地址转账（数字货币）。        |
| B   | 履行承若，或者在法院等权威机构下履行承若。同时B也不能开空头支票（既要有现货）。 | EVM 调用履行合约的接口，进行现货履约（数字化的交付物）。 |

智能合约与传统合约履行，在违约方面其实没有本质的区别：

1. 双方都是现货交易，不能开空头支票（赊账）。
2. 背后都是需要第三方，现实中要么进行现货托管，智能合约其实是将承若的交付数字化，并由以太坊托管，所以在A通过EOA往智能合约地址转账时，由于该地址无法被B控制，是由合约本身控制（以太坊系统）的，只有在B履行交付之后，才转到B的EOA。这个跟现实世界的托管交易是类似的。
3. 如果B的交付物品不能被以太坊控制、托管。以太坊只是托管了该交付物品的通证(tokens)，由于智能合约不具备法律效应，其违约风险率反而高于传统的合约。

因此从这里我们可以总结出什么是智能合约：智能合约是一个具有地址（账户号）、余额、状态、代码的账户，称为合约账户。常规的用户账户（EOA）只有：地址、余额。常规用户账户是被用户控制，合约账户是被用户控制，因为用户掌握不了合约账户的私钥。合约账户是被合约本身拥有，最终**被以太坊EVM控制**。

智能合约可以很好解决数字化世界中的交易违约问题，但如果数字化交易物只是现实物品的一个token，那么智能合约反而没有传统合约那么有效。智能合约目前只是大家在数字化世界中，以太坊公链上的娱乐玩具。由于它的公开性、以及以太坊的公开性，智能合约很容易被攻击，有漏洞的智能合约很容易在瞬间犹豫攻击产生了致命的影响，有可能是巨大的损失。

所以，这里泼一下冷水：不要神化智能合约，智能合约目前只是以太坊上的娱乐工具，它替代不了什么。

现实世界的合约交易，合约的履行还是需要靠 交易机制（是否允许赊账、空头支票）、人品（诚信）、惩罚（强力机构介入），而这些机制数字化的难度和成本很高，尤其是数字化通证(token)与实物的兑换环节中还是有违约风险。&#x20;

判断智能合约是否是空头支票的原则：

1、交易机制：是否空头支票。

2、交付物是否只是真实物品的一个数字化标签(token)。

如果是这两点，那么还是有违约的风险，因为最终拿到真实交付物品还是要靠人品、强力机构介入。

## 智能合约语言

由于智能合约是EVM可执行的低级代码段。低级代码，对人的友好性低。因此智能合约也有其友好的高级语言。以太坊提供了对开发者友好的智能合约编程语言：

1. Solidity
2. Vyper

所以这里很容易理解智能合约语言和智能合约的关系：智能合约语言是智能合约的友好可视化形式，智能合约是语言在EVM中的编译物。这种关系跟Java语言与Jar包(class文件)、C++/C语言与.o文件（.exe）的关系是一样。

## 智能合约例子

这里采用solidity语言、对照Java语法来介绍智能合约的例子：

````solidity
```remix-solidity
pragma solidity ^0.8.3;
contract Primitives {
    bool public boo = true;
    /*
    uint stands for unsigned integer, meaning non negative integers
    different sizes are available
        uint8   ranges from 0 to 2 ** 8 - 1
        uint16  ranges from 0 to 2 ** 16 - 1
        ...
        uint256 ranges from 0 to 2 ** 256 - 1
    */
    uint8 public u8 = 1;
    uint public u256 = 456;
    uint public u = 123; // uint is an alias for uint256

    /*
    Negative numbers are allowed for int types.
    Like uint, different ranges are available from int8 to int256
    */
    int8 public i8 = -1;
    int public i256 = 456;
    int public i = -123; // int is same as int256

    address public addr = 0xCA35b7d915458EF540aDe6068dFe2F44E8fa733c;

    // Default values
    // Unassigned variables have a default value
    bool public defaultBoo; // false
    uint public defaultUint; // 0
    int public defaultInt; // 0
    address public defaultAddr; // 0x0000000000000000000000000000000000000000
    function f(uint a, uint b) public pure returns (uint) {
        return a * (b + 42);
    }
}
```
````

如果用Java语言来表示这段合约，则如下：

```java
package a.b.c; //
    public class Primitives{
    public boolean boo = true;
    public short u8 = 1;
    public long u256 = 456;
    public long u = 123;
    public byte i8 = -1;
    public int i256 = 456;
    public String addr = "0xCA35b7d915458EF540aDe6068dFe2F44E8fa733c";
    public boolean defaultBoo = false;
    public long defaultUint = 0;
    public int defaultInt = 0;
    public String defaultAddr = "0x0000000000000000000000000000000000000000";
    public long f(long a,long b){
        return a*(b + 42);
    }
}
```

通过两份代码对比，我们可以看出差异和共同点：

|         | Solidity                                   | C++/C                  | Java                            |
| ------- | ------------------------------------------ | ---------------------- | ------------------------------- |
| 版本声明    | pragma...                                  | 无                      | 无                               |
| 包名/名字空间 | 无                                          | 有                      | 有                               |
| 类型      | 有无符号之分，多了address基本类型                       | 有无符号类型                 | 无无符号类型                          |
| 类声明     | contract                                   | class                  | <p>class<br>类声名前可以加<br>访问控制</p> |
| 访问控制    | public\private\external\internal\view\pure | public\private\protect | public\private\protect          |
| 继承性     | 可继承                                        | 可继承                    | 可继承                             |
| 嵌套声明    | 嵌套结构体                                      | 嵌套类/结构体                | 嵌套类                             |

Solidity的关键字说明：

1. public：可以修饰变量和函数，其访问属性跟C++/C 、Java的public 一样。合约成员的默认属性是public。
2. private：可以修饰变量和函数，其访问属性跟C++/C 、Java的private 一样。
3. external：只能修饰函数，并且只能被外部调用，不能被合约自己或者其之类调用。
4. internal：可修饰函数和变量跟C++/C中的protected 一样。
5. view：只能修饰函数，函数内部能够对内部变量进行访问，但不能修改。该函数被外部调用之后，不会改变合约内部状态。该关键字稍微有别于C++的const 函数声明。
6. pure：只能修饰函数，函数内部不能对合约内部变量进行访问。pure的功能和view 一样，只是pure 做了编译时检查，view没有。这两个关键字是constant关键字演化过来，告诉编译器这里不需要修改状态、校验状态，因此执行不需要消耗gas。用来执行一些合约逻辑代码，该代码只跟入参有关。有点类似Java工具类的static 函数。

具体的合约语言规范，参考：[https://docs.soliditylang.org/en/latest/style-guide.html](https://docs.soliditylang.org/en/latest/style-guide.html)
