在 OSI 模型中，**服务（Service）** 和 **协议（Protocol）** 是两个不同的概念，理解它们的区别有助于我们准确回答这个问题。

### 服务（Service）和协议（Protocol）的区分

- **服务（Service）**：指的是 **网络层** 向 **上层** 提供的功能或者操作，通常通过 **原语** 进行定义。服务是一个 **接口**，它向上一层提供某种功能，不涉及具体的实现细节，而只是描述某种功能或操作。例如，网络层提供的“发送数据”的服务，它可以被上层（如传输层）调用，而不关心如何在网络上实际传输数据。服务的具体实现依赖于底层的协议。

- **协议（Protocol）**：协议是 **同一层** 内的对等实体之间为完成某项任务而约定的规则、格式和行为。协议定义了两个系统或两个网络实体之间如何通信，它包括具体的语法、语义和同步规则。例如，TCP 协议定义了如何在传输层保证数据的可靠传输。

### 各个选项的解析

我们根据这个背景知识来分析每个选项：

#### A. 各层向下层提供的一组原语操作

**解释**：
- **原语操作**（Primitive Operations）是指网络层向上层提供的接口操作，也就是网络服务的具体操作。原语操作定义了服务接口的基本动作，如“请求发送数据”或“接收数据”等。
- **这个选项的描述**有一定道理，但它更偏向描述 **服务的实现方式**，而非服务本身的定义。它讲述了各层向下层提供的服务操作，但我们想要的是各层提供给上层的服务功能。

**因此，A 选项并不是最佳答案**。

#### B. 各层间对等实体间通信的功能实现

**解释**：
- 这个描述更符合协议的定义，而不是服务。协议定义了同一层的两个对等实体（比如两个主机的同层协议栈）如何通信，如何实现具体功能。
- **服务** 是面向上层的，而这个选项描述的是对等实体之间的通信过程，偏向协议的定义。

**因此，B 选项不正确**。

#### C. 各层通过其 SAP 向上层提供的一组功能

**解释**：
- 在 OSI 模型中，**SAP**（Service Access Point，服务访问点）是上层通过下层服务来访问网络功能的接口。
- 每一层通过 SAP 向上层提供服务，提供的服务通常是一些抽象的功能，如“数据传输”、“数据接收”等。
- **这个选项正好描述了服务的本质**：各层通过 SAP 向上层提供的一组功能，即服务。

**因此，C 选项是正确答案**。

#### D. 与协议的含义是一样的

**解释**：
- 如上所述，服务和协议是不同的概念。服务是上层请求的功能接口，而协议是在同一层的对等实体之间沟通的规则。服务是功能的定义，协议是规则的实现，因此它们不是同一个概念。

**因此，D 选项是错误的**。

### 结论：

正确答案是 **C**：各层通过其 SAP 向上层提供的一组功能。

### 详细总结：

- **服务** 是指网络层向上一层提供的功能，通常通过 SAP 接口实现。
- **协议** 是同一层之间的对等实体所遵循的规则。
- OSI 模型中的服务是一个 **抽象的功能接口**，而协议是 **具体的通信规则**。

选项 C 准确地描述了服务的定义，即各层通过 SAP 向上层提供的一组功能。