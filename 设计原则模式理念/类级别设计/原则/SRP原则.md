> 单一职责原则（Single Responsibility Principle，SRP）要求一个类只有一个单一的责任。这意味着一个类应该只有一个引起它变化的原因。下面我将分别演示一个遵守SRP原则的代码例子和一个不遵守的例子。



**遵守SRP原则的代码例子：**

```java
// 一个遵守SRP原则的Logger类，负责记录日志
public class Logger {
    public void logMessage(String message) {
        // 记录日志的逻辑
        System.out.println("Log: " + message);
    }
}

// 一个遵守SRP原则的UserService类，负责用户管理
public class UserService {
    public void createUser(String username) {
        // 创建用户的逻辑
        System.out.println("User created: " + username);
    }

    public void deleteUser(String username) {
        // 删除用户的逻辑
        System.out.println("User deleted: " + username);
    }
}
//上面的代码中，有两个类：Logger和UserService。Logger类负责记录日志，而UserService类负责用户管理。每个类都只有一个单一的责任，遵守了SRP原则。

```

**不遵守SRP原则的代码例子：**

```java
// 一个不遵守SRP原则的User类，负责用户管理和记录日志
public class User {
    public void createUser(String username) {
        // 创建用户的逻辑
        System.out.println("User created: " + username);
        // 记录创建用户的日志
        System.out.println("Log: User created: " + username);
    }

    public void deleteUser(String username) {
        // 删除用户的逻辑
        System.out.println("User deleted: " + username);
        // 记录删除用户的日志
        System.out.println("Log: User deleted: " + username);
    }
}
//在上面的代码中，User类既负责用户管理，又负责记录日志，违反了SRP原则，因为它有多个责任。

```

**优点：**

- 遵守SRP原则的代码更容易理解和维护，因为每个类都有明确定义的责任。
- 当需要修改某一方面的功能时，不会影响到其他部分的代码。

**缺点：**

- 为了遵守SRP原则，可能需要创建更多的类，增加代码的复杂性。
- 过度拆分类可能导致类的数量过多，使得代码库变得难以管理。

**使用场景：**

- 使用SRP原则适合任何需要清晰的单一职责的情况。例如，日志记录、数据存储、业务逻辑等都可以分别放在不同的类中，以提高代码的可维护性。
- 当一个类的功能变得复杂，难以维护时，考虑将其拆分为多个单一职责的类。
- 遵守SRP原则特别重要的领域之一是日志记录，因为它可以使日志记录代码与其他代码分离，提高了系统的可维护性和可扩展性。



其实单一职责不仅在类中遵循，在方法中也应该遵循，下面是几个判断是否违反原则的参考：

- 一个方法中if else等条件语句特别多
- 一个类中依赖了很多其他的类
- 一个类根据外部出入的值执行不同的任务