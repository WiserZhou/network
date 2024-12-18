### **多路访问链路与协议**

在计算机网络中，**多路访问**（Multiple Access）技术允许多个节点共享同一个通信信道（例如无线电频谱或有线链路），并确保它们能够有效地访问该信道而不会互相干扰。为了解决节点之间的冲突和提高资源的利用率，网络中采用了不同的 **媒体接入控制（MAC）协议**。这些协议规定了如何管理多个节点对共享信道的访问。

### **信道划分 MAC 协议**

**信道划分 MAC 协议**通过将共享的信道划分成多个独立的子信道（时隙、频段或码字），每个节点都被分配到某些子信道以避免冲突。常见的信道划分协议包括：

1. **时分多址（TDMA, Time Division Multiple Access）**  
   - **原理**：信道被划分为多个时隙，每个节点在分配给它的时隙内进行数据发送。
   - **优点**：时隙的分配可以确保每个节点拥有固定的时间窗口进行数据传输，避免了不同节点之间的冲突。
   - **缺点**：如果某个节点没有数据要发送，仍然占用时隙，导致信道的资源浪费。

2. **频分多址（FDMA, Frequency Division Multiple Access）**  
   - **原理**：信道被划分为多个不同的频带，每个节点在不同的频带上发送数据。
   - **优点**：各个节点之间的数据传输互不干扰，可以同时进行数据传输。
   - **缺点**：频带资源有限，且不同频带的带宽可能不均衡，导致资源浪费。

3. **码分多址（CDMA, Code Division Multiple Access）**  
   - **原理**：每个节点使用不同的编码方式（称为扩频码）来区分自己的信号，即使在同一频率上同时发送数据，信号也能被区分。
   - **优点**：可以高效利用频谱资源，不同节点之间互不干扰。
   - **缺点**：需要强大的编码和解码技术，且容易受到信号干扰。

### **随机接入协议**

当没有明确的信道划分时，使用 **随机接入协议**，允许多个节点随机地访问共享信道。随机接入协议的设计目标是使得节点能够尽可能高效地传输数据，同时尽量减少冲突和冲突带来的重发延迟。常见的随机接入协议包括：

#### **1. 时隙 ALOHA (Slotted ALOHA)**
- **原理**：节点在 **下一个时隙** 内发送数据。当节点有数据要发送时，它会等待到下一个时隙的开始，开始发送数据。如果在发送过程中发生了冲突，节点会在下一个时隙重新随机选择时间再次发送数据，直到成功为止。
- **优点**：较纯 ALOHA 的效率更高，因为它减少了冲突的概率。
- **缺点**：仍然存在一定的冲突概率，且时隙的划分要求严格同步。

#### **2. 纯 ALOHA (Pure ALOHA)**
- **原理**：节点 **立即发送数据**，没有等待任何时隙。发送后，节点监听信道，如果没有收到确认（acknowledgment），则会认为发生了冲突并重新发送数据。
- **优点**：简单，节点无需考虑时隙。
- **缺点**：由于没有时隙，容易产生冲突，效率较低。

#### **3. 1-坚持型 CSMA (Carrier Sense Multiple Access, 1-persistent CSMA)**
- **原理**：当节点有数据要发送时，它首先 **监听信道**。如果信道空闲，节点立刻发送数据；如果信道忙，节点会继续监听，直到信道空闲后发送数据。
- **优点**：简单，能有效利用空闲信道。
- **缺点**：如果多个节点同时开始发送数据，容易发生冲突，导致效率低下。

#### **4. 非坚持型 CSMA (Non-persistent CSMA)**
- **原理**：节点有数据要发送时，首先监听信道。如果信道空闲，节点就发送数据；如果信道忙，节点 **随机等待一段时间** 后重新尝试发送。
- **优点**：减少了多个节点同时发送的概率，从而降低了冲突。
- **缺点**：可能需要较长的等待时间。

#### **5. p-坚持型 CSMA (p-persistent CSMA)**
- **原理**：节点有数据要发送时，首先监听信道。如果信道空闲，节点会以 **概率 p** 发送数据，剩余的 **1-p** 概率则等待下一个时隙再尝试发送。
- **优点**：比 1-坚持型 CSMA 更加灵活，避免了大量冲突的情况。
- **缺点**：选择概率 p 的合适值需要根据网络负载调整，且可能会引入一些延迟。

#### **6. CSMA/CD (Carrier Sense Multiple Access with Collision Detection)**
- **原理**：在 CSMA 基础上，节点不仅监听信道的空闲情况，还可以在发送过程中检测是否发生冲突。如果发生冲突，节点会立即停止发送，并且随机等待一段时间后重新发送数据。
- **优点**：能有效减少冲突并提高信道利用率。
- **缺点**：仅适用于有线网络，因为在无线网络中，节点无法同时发送和接收信号，冲突检测较困难。

### **轮流协议**

当多个节点共享信道时，可以通过轮流的方式来控制信道访问。常见的轮流协议包括：

#### **1. 轮询 (Polling)**
- **原理**：由一个 **主节点** 定期轮询 **从节点**，询问它们是否有数据要发送。如果从节点有数据要发送，主节点允许它发送数据。
- **优点**：避免了节点间的冲突，确保信道有序利用。
- **缺点**：增加了主节点的负担，且在从节点没有数据时浪费了时间。

#### **2. 令牌传递 (Token Passing)**
- **原理**：在环形网络中，传递一个 **令牌** 给每个节点，只有持有令牌的节点才可以发送数据。令牌会在节点间依次传递，保证每个节点有机会发送数据。
- **优点**：可以避免冲突，确保每个节点有公平的发送机会。
- **缺点**：需要额外的机制来管理令牌的传递，一旦令牌丢失，会导致通信中断。

### **有限争用协议**

有限争用协议将所有的节点分为若干组，每组节点在各自的时间片内进行竞争。这种方式适用于需要严格控制冲突的情况，通常用于高流量的网络环境。

### **总结**

在多路访问链路中，选择合适的 **媒体接入控制（MAC）协议** 依据网络规模、节点数目、带宽需求、延迟容忍度等因素。**信道划分协议**（如 TDMA、FDMA、CDMA）适用于较为严格的资源划分，而 **随机接入协议**（如 ALOHA、CSMA）则适用于资源较为宽松的共享环境。对于有冲突或竞争的网络环境，可以通过 **轮流协议** 和 **有限争用协议** 来确保公平和有效的资源利用。