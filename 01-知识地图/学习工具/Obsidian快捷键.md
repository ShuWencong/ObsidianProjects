# Obsidian快捷键

这篇笔记记录 Obsidian 里最常用的快捷键。先掌握高频操作，再根据自己的使用习惯到 `设置 → 快捷键` 里自定义。

> [!note]
> Obsidian 里有两类快捷键：一种是 Obsidian 命令快捷键，可以在 `设置 → 快捷键` 修改；另一种是系统/编辑器提供的文本编辑快捷键，通常不能在 Obsidian 里修改。

## 最应该先记住

| 操作 | Windows / Linux | macOS |
| --- | --- | --- |
| 打开命令面板 | `Ctrl+P` | `Cmd+P` |
| 快速切换/打开笔记 | `Ctrl+O` | `Cmd+O` |
| 新建笔记 | `Ctrl+N` | `Cmd+N` |
| 全库搜索 | `Ctrl+Shift+F` | `Cmd+Shift+F` |
| 复制 | `Ctrl+C` | `Cmd+C` |
| 粘贴 | `Ctrl+V` | `Cmd+V` |
| 不带格式粘贴 | `Ctrl+Shift+V` | `Cmd+Shift+V` |
| 撤销 | `Ctrl+Z` | `Cmd+Z` |
| 重做 | `Ctrl+Shift+Z` 或 `Ctrl+Y` | `Cmd+Shift+Z` |
| 全选 | `Ctrl+A` | `Cmd+A` |

## 常用编辑快捷键

| 操作     | Windows / Linux  | macOS              |
| ------ | ---------------- | ------------------ |
| 加粗     | `Ctrl+B`         | `Cmd+B`            |
| 斜体     | `Ctrl+I`         | `Cmd+I`            |
| 删除前一个词 | `Ctrl+Backspace` | `Option+Backspace` |
| 删除后一个词 | `Ctrl+Delete`    | `Option+Delete`    |
| 删除当前行  | `Ctrl+Shift+K`   | `Cmd+Shift+K`      |
| 插入新行   | `Enter`          | `Enter`            |

## 光标移动

| 操作         | Windows / Linux | macOS      |
| ---------- | --------------- | ---------- |
| 向左/右移动一个字符 | `←` / `→`       | `←` / `→`  |
| 移动到上一个词开头  | `Ctrl+←`        | `Option+←` |
| 移动到下一个词结尾  | `Ctrl+→`        | `Option+→` |
| 移动到行首      | `Home`          | `Cmd+←`    |
| 移动到行尾      | `End`           | `Cmd+→`    |
| 移动到笔记开头    | `Ctrl+Home`     | `Cmd+↑`    |
| 移动到笔记结尾    | `Ctrl+End`      | `Cmd+↓`    |

## 选择文本

| 操作 | Windows / Linux | macOS |
| --- | --- | --- |
| 扩展选择一个字符 | `Shift+←` / `Shift+→` | `Shift+←` / `Shift+→` |
| 选择到上一个词开头 | `Ctrl+Shift+←` | `Option+Shift+←` |
| 选择到下一个词结尾 | `Ctrl+Shift+→` | `Option+Shift+→` |
| 选择到行首 | `Shift+Home` | `Cmd+Shift+←` |
| 选择到行尾 | `Shift+End` | `Cmd+Shift+→` |
| 选择到笔记开头 | `Ctrl+Shift+Home` | `Cmd+Shift+↑` |
| 选择到笔记结尾 | `Ctrl+Shift+End` | `Cmd+Shift+↓` |

## 光标选中、跳转和返回

这里要区分三件事：

1. 光标选中：用 `Shift` 加上光标移动快捷键
2. 文本内跳转：只移动光标，不进入 Obsidian 的导航历史
3. Obsidian 返回：返回上一个打开过的位置或笔记

| 目标 | Windows / Linux | macOS | 说明 |
| --- | --- | --- | --- |
| 选中到下一个词 | `Ctrl+Shift+→` | `Option+Shift+→` | 适合快速选中一个词或一段英文 |
| 选中到行尾 | `Shift+End` | `Cmd+Shift+→` | 适合快速选中当前行后半段 |
| 跳到上一个词 | `Ctrl+←` | `Option+←` | 只移动光标 |
| 跳到下一个词 | `Ctrl+→` | `Option+→` | 只移动光标 |
| 跳到行首 | `Home` | `Cmd+←` | 只移动光标 |
| 跳到行尾 | `End` | `Cmd+→` | 只移动光标 |
| 跳到笔记开头 | `Ctrl+Home` | `Cmd+↑` | 只移动光标 |
| 跳到笔记结尾 | `Ctrl+End` | `Cmd+↓` | 只移动光标 |
| 返回上一个导航位置 | 常见默认是 `Ctrl+Alt+←` | 常见默认是 `Cmd+Option+←` | 命令名通常是 `Navigate back` / `后退` |
| 前进到下一个导航位置 | 常见默认是 `Ctrl+Alt+→` | 常见默认是 `Cmd+Option+→` | 命令名通常是 `Navigate forward` / `前进` |

> [!warning]
> `Navigate back` 返回的是 Obsidian 的导航历史，不是每一次光标移动的历史。也就是说，用 `Ctrl+←` 在同一篇笔记里移动光标后，通常不能靠 `Navigate back` 回到刚才的光标位置。

如果想从键盘跳转到链接，可以在 `设置 → 快捷键` 里搜索并绑定这些命令：

- `Open link under cursor` / `Follow link under cursor`
- `Navigate back`
- `Navigate forward`

如果 `Ctrl+Alt+←` 或 `Ctrl+Alt+→` 无效，通常是被 Windows 显卡快捷键或 Linux 桌面环境占用了。直接在 Obsidian 的 `设置 → 快捷键` 里改成自己顺手的组合键即可。

## 怎么查看和修改快捷键

1. 打开 `设置 → 快捷键`
2. 搜索命令名称
3. 点击命令旁边的 `+`
4. 按下想绑定的组合键
5. 点击保存

也可以先按 `Ctrl+P` 打开命令面板，搜索命令，看命令右侧是否已经有快捷键。

## 我的使用建议

- 先熟练 `Ctrl+P`：不会找功能时，直接打开命令面板搜索
- 先熟练 `Ctrl+O`：比在文件列表里找笔记更快
- 先熟练 `Ctrl+Shift+F`：全库搜索是维护知识库的基础能力
- 常用命令再自定义快捷键，不要一开始就绑定太多

## 资料来源

- [Obsidian Help - Hotkeys](https://obsidian.md/help/hotkeys)
- [Obsidian Help - Editing shortcuts](https://obsidian.md/help/editing-shortcuts)
- [Obsidian Help - Command palette](https://obsidian.md/help/Plugins/Command%2Bpalette)
- [Obsidian Help - Quick switcher](https://obsidian.md/help/plugins/quick-switcher)
- [Obsidian Help - Search](https://obsidian.md/help/Plugins/Search)
- [Obsidian Help - Create your first note](https://obsidian.md/help/create-note)

## 相关链接

- [[Obsidian]]
- [[学习工具]]
- [[笔记方法]]
