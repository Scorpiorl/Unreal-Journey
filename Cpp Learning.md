# C++
## The C++ build process
1. Source Code
2. C++ Compiler
3. Object Code
4. Linker
   链接多个cpp文件构成可执行exe文件，当compiler没问题，Run有问题时，有可能是Linker中缺少东西导致程序无法执行。

### Preprocessor Directives
    C++预处理器不理解C++，它只是遵循预处理指令，并为编译器准备好源文件。

### 注释快捷键
      shift+ctrl+/

### Declaring and Initializing Variables

```C++
int age = 21; // C-like initialization
int age (21); // Constructor initialization
int age {21}; // C++11 list initialization syntax
```
推荐使用C++11初始化语法
### Vector

**vector<value_type> vector_name**

**vector_name [element_index]** Accessing vector elements - array syntax

**vector_name.at(element_index)** Accessing vector elements - vector syntax

**vector_name.push_back(element)**

Explicit Type Casting - ```static_cast<type>``` //转换数据类型

### switch
```C++
switch (integer_control_expr){
    case expression_1 : 
        statement_1;
        break;
    case expression_2 : 
        statement_2;
        break;
    case expression_3 : 
        statement_3;
        break;
    ...
    case expression_n : 
        statement_n;
        break;
    default : statement_default;
}
```

### ? :
```C++
(cond_expr) ? expr1 : expr2 
// if cond_expr is true then the value of expr1 is returned
// if cond_expr is false then the value of expr2 is returned
```
### for Loop
```C++
for ( initialization; codition; increment)
    statement; 
    // or statement(s)
```
### Range-based for Loop
```C++
for (var_type var_name: sequence)
    statement; // can use var_name 循环遍历元素集合
    // or statements
```
### auto 根据声明计算出类型
### while Loop
```C++
while(expression)
    statement; 
    // or statement(s)
```
### size_t
```size_t``` is commonly used for array indexing and loop counting. Programs that use other types, such as ```unsigned int```, for array indexing may fail on, e.g. 64-bit systems when the index exceeds UINT_MAX or if it relies on 32-bit modular arithmetic.
### do while Loop 
```C++
do{
    statement;
    //or statement(s);    
}while(expression); // at least do once
```
### C-style String
```C++
char my_name[] {"Name"}; // N a m e \0
char my_name[8] {"Name"}; // N a m e \0 \0 \0 \0 
```
### C++ Strings
```C++
#include <string>
using namespace std;

string s1; 
stirng s2 {"Name"};
...

object.substr(start_index, length)
object.find(search_string)
object.erase(start_index, length)
object.clear()
```
### seed the random number ganerator
```C++
srand(time(nullptr));
```
---
# Function

1.function prototype

2.function（）

3.function（）{
    body
}

Default values must appear at tail end of the parameter list.

### static
**static** 修饰符，将函数中此变量的值保存至下一次调用。

---
# Pointer
Declaring Pointers
``` C++
variable_type *pointer_name{nullptr};

int *int_ptr{};
char *char_ptr{nullptr};
...
```
### Dynamic Memory Allocation
using ```new``` to allocate storage

using ```delete``` to deallocate storage
```C++
int *int_ptr {nullptr};
int_ptr = new int; // allocate an integer on the heap
...
delete int_ptr; // frees the allocated storage
```
using ```new[]``` to allocate storage

using ```delete[] ``` to deallocate storage
```C++
int *array_ptr {nullptr};
int size{};
array_ptr = new int[size]; // allocate array on the heap
...
delete [] array_ptr; // frees allocated storage
```
### Relationship Between Arrays and Pointers
```C++
int scores[]{100, 95, 89};
cout << scores << endl; // 0x61fec8 - address
cout << *scores << endl; // 100

int *score_ptr {scores};
cout << score_ptr << endl; // 0x61fec8 - the same address
cout << *score_ptr << endl; // 100

cout << score_ptr[0] << endl; // 100
cout << score_ptr[1] << endl; // 95
cout << score_ptr[2] << endl; // 89
```
### Subscript and Offset notation equivalence
```C++
int array_name[]{1, 2, 3, 4, 5};
int *pointer_name{array_name};
```
|Subscript Notation | Offset Notation|
|----|----|
|```array_name[index]```|```*(array_name + index)```|
|```pointer_name[index]```|```*(pointer_name + index)```|

**++ and --**
```int_ptr++``` and ```int_ptr--```

**+ and -**
```int_ptr += n;``` and ```int_ptr -= n;```

**Subtracting two pointers**
```int n = int_prt2 - int_ptr1;```
 
1. **Pointers to constants**
   
    The date pointed to by the pointers is constant and cannot be changed.

    The pointer itself can change and point somewhere else.

    指针可变，指针指向内部数据不可变。
    ```C++
    int high_score{100};
    int low_score{65};
    const int *score_ptr{&high_score};

    *score_ptr = 86; // ERROR
    score_ptr = &low_score; // OK
    ```
2. **Constant pointers**
   
   The date pointed to by the pointers can be changed.

   The pointer itself cannot change and point somewhere else.

   指针不可变，指针内部数据可变。
   ```C++
    int high_score{100};
    int low_score{65};
    int *const score_ptr{&high_score};

    *score_ptr = 86; // OK
    score_ptr = &low_score; // ERROR
    ```
3. **Constant pointers to constants**
   
   The date pointed to by the pointers is constant and cannot be changed.

   The pointer itself cannot change and point somewhere else.

   指针不可变，指针内部数据不可变。
   ```C++
    int high_score{100};
    int low_score{65};
    const int *const score_ptr{&high_score};

    *score_ptr = 86; // ERROR
    score_ptr = &low_score; // ERROR
    ```

### Returning a Pointer from a Function
```C++
type *function();
```
---
# OOP
## Classes and Objects

### 1. Declaring a Class
```C++
class Class_Name
{
    // declaration(s);
};
```

e.g.
```C++
// Player
class Player
{
    //attributes
    std::string name;
    int health;
    int xp;

    //methods
    void talk(std::string text_to_say);
    bool is_dead();
};

//Creating object
Player frank;
Player hero;

Player *enemy = new Player();
delete enemy;
```

### 2. Accessing Class Members

If we hace an object(dot operator)
* Using the dot operator
```C++
Account frank_account;

frank_account.balance;
frank_account.deposit(1000.00);
```
If we hace a pointer to an object(member of pointer operator)
* Dereference the pointer then use the dot operator.
```C++
Account *frank_account = new Account();

(*frank_account).balance;
(*frank_account).deposit(1000.00);
```
* Or use the member of pointer operator(arrow operator)
```C++
Account *frank_account = new Account();

frank_account->balance;
frank_account->deposit(1000.00);
```

### 3. Constructors and Destructors
```C++
class Player
{
private:
    std::string name;
    int health;
    int xp;
public:
    //Constructors
    Player();
    Player(std::string name_val);
    Player(std::string name_val, int health_val, int xp_val);
    //Destructor
    ~Player();
}
```
#### Overloaded Constructors
```C++
Player::Player()
{
    name = "None";
    health = 0;
    xp = 0
}

Player::Player(std::string name_val)
{
    name = name_val;
    health = 0;
    xp = 0;
}

Player::Player(std::string name_val, int health_val, int xp_val)
{
    name = name_val;
    health = health_val;
    xp = xp_val;
}
```
#### Constructor Initialization Lists
```C++
Player()

Player::Player()
    : name{"None"}, health{0}, xp{0} {

    }

Player::Player(std::string name_val)
    : name{name_val}, health{0}, xp{0} {

    }

Player::Player(std::string name_val, int health_val, int xp_val)
    : name{name_val}, health{health_val}, xp{xp_val} {

    }
```
#### delegating Constructors
```C++
//委托构造函数：可以在构造函数初始化列表中调用同一类的另一个构造函数
Player::Player(std::string name_val, int health_val, int xp_val)
    : name{name_val}, health{health_val}, xp{xp_val} {

    }

Player::Player()
    : Player {"None", 0, 0} {

    }

Player::Player(std::string name_val)
    : Player {name_val, 0, 0} {

    }
```

#### Default Constructor Paramenters
```C++
class Player
{
private:
    std::string name;
    int health;
    int xp;
public:
    //Constructor with defalt parameter values
    Player(std::string name_val = "None", int health = 0, int xp = 0);
}

Player::Player(std::string name_val, int health_val, int xp_val)
    : name{name_val}, health{health_val}, xp{xp_val} {

    }
```

#### Copy Constructor 拷贝构造
1. 
```C++
// Pass object by-value
// 将一个对象作为参数通过值传递给函数或方法
Player hero {"Hero", 100, 20};

void display_player(Player p){
    // p is a COPY of hero in this example
    // use p
    // Destructor for p will be called 
}

display_player(hero);

```
2. 
```C++
// Return object by-value
// 从函数或方法中按值返回对象
Player enemy;

Player create_super_enemy(){
    Player an_enemy{"Super Enemy", 1000, 1000};
    return an_enemy; // A COPY of an_enemy is returned
}

enemy = create_super_enemy();
``` 
3. 
```C++
// Construct one object based on another
// 基于同一类的现有对象构造一个新对象
Player hero {"Hero", 100, 100};

Player another_hero {hero}; //A COPY of hero is made
```


```C++
//Implementing the Copy Constructor
Type::Type(const Type &source)
    : name{source.name}, health{source.health}, xp{source.xp} {

    }

//Implementing the Copy Constructor by Delegating Constructor
Type::Type(const Type &source)
    : Type{source.name, source.health, source.xp} {

    }

```








## 游戏编程模式
### 架构，性能和游戏tips

1. 抽象和解耦让扩展代码更快更容易，但除非确信需要灵活性，否则不要在这上面浪费时间。
2. 在整个开发周期中为性能考虑并做好设计，但是尽可能推迟那些底层的，基于假设的优化，那会锁死代码。
3. 快速地探索游戏的设计空间，但不要跑得太快，在身后留下烂摊子。毕竟你总得回来打扫。
4. 如果打算抛弃这段代码，就不要尝试将其写完美。摇滚明星将旅店房间弄得一团糟，因为他们知道明天就走人了。
5. 但最重要的是，**如果你想要做出让人享受的东西，那就享受做它的过程**。

### 设计模式
1. 命令模式
2. 享元模式
3. 观察者模式
4. 原型模式
5. 单例模式
6. 状态模式