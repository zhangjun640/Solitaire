# 🃏 Solitaire (Java Swing 克朗代克纸牌)

A full-featured **Klondike Solitaire** game implemented in **Java Swing**, supporting complete gameplay logic, card dragging, auto-turning, auto-collection, and a multi-step **Undo system**.  
本项目提供一个经典、流畅且高度可维护的桌面纸牌游戏实现。

---

## ✨ Features

### 🎮 经典克朗代克规则
- **发牌堆 DeckPile**：点击发一张牌到弃牌堆  
- **弃牌堆 DiscardPile**：可拖拽堆顶牌  
- **场面牌堆 TablePile（7堆）**  
  - 红黑交替  
  - 牌点递减  
  - 可一次移动多张牌  
- **目的牌堆 SuitPile（4堆）**  
  - 同一花色  
  - A → K 顺序收集  

### 🖱️ 完整交互系统
- 实现 `MouseListener` & `MouseMotionListener`
- 支持：
  - 单张或多张牌拖拽
  - 点击发牌
  - 自动从弃牌堆回收至发牌堆
  - 右键菜单操作

### 📌 核心亮点：多步撤销 Undo
基于 `UsedPile` 和 `usedPile` 栈结构：

- 记录每一步移动  
- 包含：来源堆、目标堆、翻开牌状态、移动的牌列表  
- 支持 **无限撤销** 所有动作，包括翻牌、发牌、移牌等  
- 由右键菜单触发

### 🏆 自动胜利检测
当 4 个 SuitPile 全部到达 13 张牌：
```

You win !

```
自动弹窗提示获胜。

---

## 🧰 Tech Stack

| 类别 | 技术 |
|------|------|
| Language | Java |
| UI Framework | Java Swing (JFrame, JPanel, PopupMenu) |
| Data Structure | `Stack`, `ArrayList` |
| Event Handling | MouseListener, MouseMotionListener, ActionListener |
| Image Loading | `ImageIO.read()` |
| Resource Folder | `/poker/` (卡牌图片) |

---

## 🚀 Running the Game

### 1. 安装 Java 环境
- JDK 8 或更高版本

### 2. 下载项目
确保下载的内容包括：
```

src/
poker/

```

### 3. 保证图片路径正确
游戏使用 **相对路径**：
```

poker/0-0.jpg
poker/back.png

````
因此：  
**你必须从项目根目录运行程序。**

---

## 🔧 Compile (Command Line)

```bash
# 创建 out 目录
mkdir out

# 编译所有 Java 源码（递归包含 card/pile/game）
javac -d out -cp src \
    src/solitaire/card/*.java \
    src/solitaire/pile/*.java \
    src/solitaire/game/*.java
````

---

## ▶️ Run (Command Line)

```bash
# 必须在项目根目录执行（以确保能找到 poker/ 图片资源）
java -cp out solitaire.game.Main
```

---

## 💡 Run in IntelliJ IDEA / Eclipse

* 打开项目
* 确保 IDE 识别 `src/` 目录
* 运行主类：

```
solitaire.game.Main
```

### ⚠ 必须检查：

**Run/Debug Configurations → Working Directory = 项目根目录**
否则程序无法加载 poker/ 中的图片资源。

---

## 📂 Project Structure

```
.
├── src/
│   ├── solitaire/
│   │   ├── card/
│   │   │   └── Card.java             # 卡牌类：花色、点数、正反面、绘制方法
│   │   │
│   │   ├── game/
│   │   │   ├── Main.java             # 启动入口：创建窗口
│   │   │   ├── Game.java             # 游戏核心逻辑：洗牌、发牌、规则、撤销
│   │   │   └── Solitaire.java        # 游戏界面：渲染牌面 + 鼠标事件处理
│   │   │
│   │   └── pile/
│   │       ├── CardPile.java         # 牌堆基类（Stack 实现）
│   │       ├── DeckPile.java         # 发牌堆
│   │       ├── DiscardPile.java      # 弃牌堆
│   │       ├── SuitPile.java         # 目的堆（4个）
│   │       ├── TablePile.java        # 场面堆（7个）
│   │       ├── MoveCardPile.java     # 正在被拖拽的临时牌堆
│   │       └── UsedPile.java         # 撤销系统的数据结构
│
├── poker/                            # 卡牌图片资源
│   ├── 0-0.jpg
│   ├── 1-0.jpg
│   ├── ...
│   ├── back.png
│   └── 0.png
│
└── README.md
```

---

## 🖼️ Screenshots (可自行添加)

示例：

```
![Game Screenshot](poker/back.png)
```

---

## 🤝 Contributing

欢迎提交 Issue 或 Pull Request！

---

## 📄 License

本项目为开源项目，可自由学习、修改和扩展。

