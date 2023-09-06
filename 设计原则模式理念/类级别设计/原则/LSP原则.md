> 里氏替换原则（Liskov Substitution Principle，LSP）要求子类能够替代其父类而不引发不良行为。以下是一个遵守和不遵守LSP原则的示例，以及它们的优缺点和使用场景。

**遵守LSP原则的代码示例：**

```java
// 父类
class Bird {
    void fly() {
        System.out.println("Bird is flying");
    }
}

// 子类
class Sparrow extends Bird {
    // Sparrow类继承自Bird类，不重写fly方法
}

class Ostrich extends Bird {
    @Override
    void fly() {
        // 鸵鸟无法飞行，所以覆盖父类的fly方法并提供适当的实现
        System.out.println("Ostrich cannot fly");
    }
}

public class Main {
    public static void main(String[] args) {
        Bird sparrow = new Sparrow();
        Bird ostrich = new Ostrich();

        sparrow.fly(); // 输出 "Bird is flying"
        ostrich.fly(); // 输出 "Ostrich cannot fly"
    }
}
//在上面的代码中，Sparrow和Ostrich类继承自Bird类，而Ostrich类覆盖了fly方法，提供了合适的实现。这遵守了LSP原则，因为Sparrow和Ostrich都可以替代其父类Bird而不引发不良行为。

```

**不遵守LSP原则的代码示例：**



```java
// 父类
class Bird {
    void fly() {
        System.out.println("Bird is flying");
    }
}

// 子类
class Penguin extends Bird {
    @Override
    void fly() {
        // 企鹅无法飞行，但不重写父类的fly方法
    }
}

public class Main {
    public static void main(String[] args) {
        Bird bird = new Penguin();
        bird.fly(); // 输出 "Bird is flying"，但实际上企鹅无法飞行
    }
}
//在上述代码中，Penguin类继承自Bird类，但不重写fly方法。尽管企鹅无法飞行，但通过使用多态，我们仍然可以调用fly方法。这违反了LSP原则，因为子类不提供合适的行为，导致不一致的行为。
```

**优点：**

- 遵守LSP原则可以确保代码的一致性和可预测性。
- 可以轻松地添加新的子类，而不必担心破坏现有代码的行为。

**缺点：**

- 遵守LSP原则可能需要在子类中进行额外的工作，以确保它们能够正确地替代父类。
- 有时为了遵守LSP原则，可能需要引入更多的抽象层次，增加代码的复杂性。

**使用场景：**

- LSP原则适用于任何需要多态性的情况，如使用继承的面向对象设计。
- 当你希望子类能够替代父类，并且在行为上保持一致时，LSP原则非常有用。
- 遵守LSP原则有助于编写可维护和可扩展的代码，特别是在大型项目中。



违反此原则的参考：

- 代码中使用了`isinstance`之类的之类判定类型，然后强制转换后使用里面的方法。

- 类里面存在接口或者其继承的抽象类的方法的空实现,类似下面这样的

  ```
  @Override
  public void laiDaYiMa() {
      //老子不来大姨妈，所以方法置空，或者抛出不支持操作的异常
  }
  ```

