---
title: "Lua常用API"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/ixshnxvb8issspxa"
slug: "ixshnxvb8issspxa"
doc_id: "188045733"
updated: "2024-09-25T12:13:22.000Z"
tags:
  - yuque
---

# Lua常用API

Lua 是一种轻量级、高效且易于嵌入的脚本语言，广泛应用于游戏开发、嵌入式系统以及各种自动化脚本中。Lua 提供了丰富的标准库（API），帮助开发者处理字符串、表（表相当于其他语言中的数组和字典）、数学运算、文件操作等。以下是 Lua 中常用的 API 分类及其常用函数介绍：

## 1. 基本函数（Basic Functions）

### 常用函数

- `print(...)`

- **用途**：用于在控制台输出信息，常用于调试。

- **示例**：

```lua
print("Hello, Lua!")
```

- `type(value)`

- **用途**：返回变量的类型，如 `"nil"`、`"number"`、`"string"`、`"table"`、`"function"` 等。

- **示例**：

```lua
print(type(123))       -- 输出: number
print(type("Lua"))     -- 输出: string
```

- `pairs(table)`

- **用途**：遍历表中的所有键值对，适用于遍历非数组部分。

- **示例**：

```lua
local t = {a = 1, b = 2}
for key, value in pairs(t) do
    print(key, value)
end
```

- `ipairs(table)`

- **用途**：遍历表中的整数键（数组部分），按序号从小到大遍历。

- **示例**：

```lua
local t = {10, 20, 30}
for index, value in ipairs(t) do
    print(index, value)
end
```

- `next(table, index)`

- **用途**：获取表中下一个键值对，常用于自定义遍历。

- **示例**：

```lua
local t = {a = 1, b = 2}
local key, value = next(t, nil)
print(key, value)  -- 输出: a 1
```

- `pcall(func, ...)`

- **用途**：调用函数并捕获任何运行时错误，返回状态和结果。

- **示例**：

```lua
local status, err = pcall(function() error("An error") end)
print(status, err)  -- 输出: false  An error
```

- `assert(condition, message)`

- **用途**：检查条件是否为真，若为假则抛出错误。

- **示例**：

```lua
assert(1 == 1, "This will not fail")
assert(1 == 2, "This will fail")  -- 抛出错误: This will fail
```

## 2. 字符串库（string）

Lua 的字符串库提供了多种处理字符串的函数。

### 常用函数

- `string.len(s)`** 或 **`#s`

- **用途**：返回字符串 `s` 的长度。

- **示例**：

```lua
local s = "Hello"
print(string.len(s))  -- 输出: 5
print(#s)             -- 输出: 5
```

- `string.sub(s, i, j)`

- **用途**：返回字符串 `s` 从第 `i` 个字符到第 `j` 个字符的子串。

- **示例**：

```lua
local s = "Hello, Lua!"
print(string.sub(s, 1, 5))  -- 输出: Hello
```

- `string.find(s, pattern, init, plain)`

- **用途**：在字符串 `s` 中查找模式 `pattern`，返回开始和结束位置。

- **示例**：

```lua
local s = "Hello, Lua!"
local start_pos, end_pos = string.find(s, "Lua")
print(start_pos, end_pos)  -- 输出: 8  10
```

- `string.gsub(s, pattern, repl, n)`

- **用途**：将字符串 `s` 中的模式 `pattern` 替换为 `repl`，最多替换 `n` 次。

- **示例**：

```lua
local s = "Hello, Lua!"
local new_s, count = string.gsub(s, "Lua", "World")
print(new_s, count)  -- 输出: Hello, World!  1
```

- `string.lower(s)`** 和 **`string.upper(s)`

- **用途**：将字符串 `s` 转为小写或大写。

- **示例**：

```lua
local s = "Hello, Lua!"
print(string.lower(s))  -- 输出: hello, lua!
print(string.upper(s))  -- 输出: HELLO, LUA!
```

- `string.format(formatstring, ...)`

- **用途**：格式化字符串，类似于 C 语言的 `printf`。

- **示例**：

```lua
local name = "Lua"
local version = 5.4
local s = string.format("Welcome to %s version %.1f!", name, version)
print(s)  -- 输出: Welcome to Lua version 5.4!
```

- `string.match(s, pattern, init)`

- **用途**：在字符串 `s` 中查找符合模式 `pattern` 的子串。

- **示例**：

```lua
local s = "Lua 5.4"
local version = string.match(s, "%d+%.%d")
print(version)  -- 输出: 5.4
```

## 3. 表库（table）

表是 Lua 中最重要的数据结构，既可以用作数组，也可以用作字典。

### 常用函数

- `table.insert(table, [pos,] value)`

- **用途**：在表 `table` 的指定位置 `pos` 插入 `value`，若未指定 `pos` 则插入到末尾。

- **示例**：

```lua
local t = {1, 2, 3}
table.insert(t, 2, 1.5)  -- 在位置2插入1.5
-- t = {1, 1.5, 2, 3}
```

- `table.remove(table, [pos])`

- **用途**：移除表 `table` 中指定位置 `pos` 的元素，若未指定则移除最后一个元素。

- **示例**：

```lua
local t = {1, 1.5, 2, 3}
table.remove(t, 2)  -- 移除位置2的元素
-- t = {1, 2, 3}
```

- `table.sort(table, comp)`

- **用途**：对表 `table` 进行排序，可以指定比较函数 `comp`。

- **示例**：

```lua
local t = {3, 1, 4, 2}
table.sort(t)
-- t = {1, 2, 3, 4}

table.sort(t, function(a, b) return a > b end)
-- t = {4, 3, 2, 1}
```

- `table.concat(table, sep, i, j)`

- **用途**：将表 `table` 中的元素连接成一个字符串，使用 `sep` 作为分隔符，范围从 `i` 到 `j`。

- **示例**：

```lua
local t = {"Hello", "Lua", "World"}
local s = table.concat(t, ", ")
print(s)  -- 输出: Hello, Lua, World
```

- `table.unpack(table, i, j)`

- **用途**：将表 `table` 中的元素作为多个返回值返回，从索引 `i` 到 `j`。

- **示例**：

```lua
local t = {1, 2, 3}
local a, b, c = table.unpack(t)
print(a, b, c)  -- 输出: 1  2  3
```

- `table.foreach(table, func)`（Lua 5.0-5.1，已废弃）

- **用途**：遍历表中的每一个键值对，调用函数 `func`。

- **示例**：

```lua
local t = {a = 1, b = 2}
table.foreach(t, print)
```

## 4. 数学库（math）

Lua 的数学库提供了基本的数学函数和常量。

### 常用函数

- `math.abs(x)`

- **用途**：返回 `x` 的绝对值。

- **示例**：

```lua
print(math.abs(-10))  -- 输出: 10
```

- `math.sqrt(x)`

- **用途**：返回 `x` 的平方根。

- **示例**：

```lua
print(math.sqrt(16))  -- 输出: 4
```

- `math.pow(x, y)`

- **用途**：返回 `x` 的 `y` 次幂。

- **示例**：

```lua
print(math.pow(2, 3))  -- 输出: 8
```

- `math.floor(x)`** 和 **`math.ceil(x)`

- **用途**：返回 `x` 向下取整或向上取整的值。

- **示例**：

```lua
print(math.floor(3.7))  -- 输出: 3
print(math.ceil(3.3))   -- 输出: 4
```

- `math.random([m, n])`

- **用途**：返回一个随机数，若指定范围 `[m, n]`，则返回 `m` 到 `n` 之间的整数。

- **示例**：

```lua
math.randomseed(os.time())  -- 设置随机种子
print(math.random())        -- 输出: 0.123456789
print(math.random(1, 10))   -- 输出: 1 到 10 之间的随机整数
```

- `math.sin(x)`**, **`math.cos(x)`**, **`math.tan(x)`** 等三角函数**

- **用途**：返回角度 `x`（弧度）的正弦、余弦、正切值。

- **示例**：

```lua
print(math.sin(math.pi / 2))  -- 输出: 1
print(math.cos(0))            -- 输出: 1
```

### 常用常量

- `math.pi`

- **用途**：表示 π 的值。

- **示例**：

```lua
print(math.pi)  -- 输出: 3.1415926535898
```

- `math.huge`

- **用途**：表示正无穷大。

- **示例**：

```lua
print(math.huge > 1000000)  -- 输出: true
```

## 5. 输入输出库（io）

Lua 的 `io` 库用于文件的读取和写入操作。

### 常用函数

- `io.open(filename, mode)`

- **用途**：打开文件 `filename`，模式 `mode` 可以是 `"r"`（读取）、`"w"`（写入）、`"a"`（追加）等，返回文件句柄。

- **示例**：

```lua
local file = io.open("test.txt", "w")
file:write("Hello, Lua!")
file:close()
```

- `file:read(...)`

- **用途**：从文件句柄 `file` 中读取内容，参数可以指定读取模式，如 `"*line"`、`"*number"` 等。

- **示例**：

```lua
local file = io.open("test.txt", "r")
local content = file:read("*all")
print(content)
file:close()
```

- `file:write(...)`

- **用途**：向文件句柄 `file` 中写入内容。

- **示例**：

```lua
local file = io.open("test.txt", "a")
file:write("\nAppending a new line.")
file:close()
```

- `io.lines(filename)`

- **用途**：迭代器，逐行读取文件 `filename`。

- **示例**：

```lua
for line in io.lines("test.txt") do
    print(line)
end
```

- `io.close(file)`

- **用途**：关闭文件句柄 `file`，若未指定则关闭默认文件。

- **示例**：

```lua
local file = io.open("test.txt", "r")
-- 读取操作
io.close(file)
```

- `io.flush()`

- **用途**：刷新输出缓冲区，将缓冲区内容写入文件。

- **示例**：

```lua
io.write("Flushing buffer...")
io.flush()
```

### 文件模式说明

- `"r"`：以只读方式打开文件。

- `"w"`：以写入方式打开文件，如果文件存在则覆盖，不存在则创建。

- `"a"`：以追加方式打开文件，不覆盖现有内容。

- `"rb"`, `"wb"`, `"ab"`：以二进制模式打开文件，适用于非文本文件。

## 6. 操作系统库（os）

Lua 的 `os` 库提供了与操作系统交互的功能。

### 常用函数

- `os.time([table])`

- **用途**：返回当前时间的时间戳，或根据给定的表返回指定时间的时间戳。

- **示例**：

```lua
print(os.time())  -- 输出: 当前时间的时间戳
```

- `os.date([format,] time)`

- **用途**：格式化时间戳 `time`，返回字符串表示的日期和时间。`format` 支持与 C 语言 `strftime` 类似的格式。

- **示例**：

```lua
print(os.date("%Y-%m-%d %H:%M:%S"))  -- 输出: 当前日期和时间
```

- `os.execute(command)`

- **用途**：执行操作系统命令 `command`。

- **示例**：

```lua
os.execute("echo Hello from Lua!")
```

- `os.getenv(varname)`

- **用途**：获取环境变量 `varname` 的值。

- **示例**：

```lua
print(os.getenv("PATH"))
```

- `os.remove(filename)`

- **用途**：删除文件 `filename`。

- **示例**：

```lua
os.remove("test.txt")
```

- `os.rename(oldname, newname)`

- **用途**：重命名文件或目录，从 `oldname` 改为 `newname`。

- **示例**：

```lua
os.rename("old.txt", "new.txt")
```

- `os.tmpname()`

- **用途**：生成一个临时文件名。

- **示例**：

```lua
print(os.tmpname())  -- 输出: 临时文件名，如 /tmp/lua_1234
```

## 7. 协程库（coroutine）

Lua 的协程库用于实现协作式多任务，可以在函数之间切换执行。

### 常用函数

- `coroutine.create(function)`

- **用途**：创建一个新的协程，返回协程对象。

- **示例**：

```lua
local co = coroutine.create(function()
    for i = 1, 3 do
        print("Coroutine:", i)
        coroutine.yield()
    end
end)
```

- `coroutine.resume(co, ...)`

- **用途**：恢复执行协程 `co`，并传递参数。

- **示例**：

```lua
coroutine.resume(co)  -- 输出: Coroutine: 1
coroutine.resume(co)  -- 输出: Coroutine: 2
coroutine.resume(co)  -- 输出: Coroutine: 3
```

- `coroutine.yield(...)`

- **用途**：挂起协程的执行，返回参数给 `resume`。

- **示例**：

```lua
coroutine.yield("Yielded value")
```

- `coroutine.status(co)`

- **用途**：返回协程 `co` 的状态，如 `"running"`、`"suspended"`、`"dead"` 等。

- **示例**：

```lua
print(coroutine.status(co))  -- 输出: suspended
```

- `coroutine.wrap(function)`

- **用途**：创建一个包装后的协程函数，调用时自动 resume，返回结果。

- **示例**：

```lua
local wrapped = coroutine.wrap(function()
    for i = 1, 3 do
        print("Coroutine wrapped:", i)
        coroutine.yield()
    end
end)

wrapped()  -- 输出: Coroutine wrapped: 1
wrapped()  -- 输出: Coroutine wrapped: 2
wrapped()  -- 输出: Coroutine wrapped: 3
```

### 示例：简单协程

```lua
local co = coroutine.create(function(name)
    for i = 1, 3 do
        print(name, i)
        coroutine.yield()
    end
end)

coroutine.resume(co, "A")  -- 输出: A 1
coroutine.resume(co, "A")  -- 输出: A 2
coroutine.resume(co, "A")  -- 输出: A 3
```

## 8. 包管理库（package）

Lua 的 `package` 库用于管理模块和加载路径。

### 常用函数

- `package.path`** 和 **`package.cpath`

- **用途**：设置 Lua 模块和 C 库的搜索路径。

- **示例**：

```lua
package.path = package.path .. ";/my/custom/path/?.lua"
package.cpath = package.cpath .. ";/my/custom/path/?.so"
```

- `require(module)`

- **用途**：加载并返回模块 `module`，防止重复加载。

- **示例**：

```lua
local mymodule = require("mymodule")
```

- `package.loaded`

- **用途**：存储已加载的模块，防止重复加载。

- **示例**：

```lua
if not package.loaded["mymodule"] then
    require("mymodule")
end
```

### 示例：加载自定义模块

假设有一个模块 `math_utils.lua`：

```lua
-- math_utils.lua
local math_utils = {}

function math_utils.add(a, b)
    return a + b
end

return math_utils
```

在主程序中加载并使用：

```lua
local math_utils = require("math_utils")
print(math_utils.add(3, 4))  -- 输出: 7
```

## 9. 调试库（debug）

Lua 的 `debug` 库提供了调试和检查程序的功能，通常用于调试工具或高级功能。

### 常用函数

- `debug.traceback([thread,] [message, level])`

- **用途**：生成调用堆栈的字符串，可以用于错误报告。

- **示例**：

```lua
local function a()
    local function b()
        error("An error occurred")
    end
    b()
end

local status, err = pcall(a)
if not status then
    print(debug.traceback(err))
end
```

- `debug.getinfo([thread,] function, what)`

- **用途**：获取函数的信息，如名称、源文件、行号等。

- **示例**：

```lua
local function foo()
    -- do something
end
local info = debug.getinfo(foo, "nSl")
for k, v in pairs(info) do
    print(k, v)
end
```

- `debug.getlocal([thread,] level, index)`

- **用途**：获取指定堆栈层级 `level` 的局部变量 `index` 的名称和值。

- **示例**：

```lua
local function foo()
    local a = 10
    local b = 20
    print(debug.getlocal(2, 1))  -- 获取上一层函数的第一个局部变量
end

local function bar()
    foo()
end

bar()
```

### 注意事项

- **性能影响**：`debug` 库的函数可能会影响性能，建议仅在调试阶段使用。

- **安全性**：`debug` 库提供了访问和修改内部状态的功能，可能会带来安全隐患，生产环境中应谨慎使用。

## 10. 协程库（coroutine）详细介绍

虽然前面已经简要介绍了协程库，以下是更详细的说明和高级用法。

### 创建和使用协程

```lua
-- 创建协程
local co = coroutine.create(function(name)
    for i = 1, 3 do
        print(name, i)
        coroutine.yield()
    end
end)

-- 恢复协程
coroutine.resume(co, "Coroutine A")  -- 输出: Coroutine A 1
coroutine.resume(co, "Coroutine A")  -- 输出: Coroutine A 2
coroutine.resume(co, "Coroutine A")  -- 输出: Coroutine A 3
coroutine.resume(co, "Coroutine A")  -- 输出: false, "cannot resume dead coroutine"
```

### 协程状态

- `"running"`：当前正在运行的协程。

- `"suspended"`：挂起的协程，可以被恢复。

- `"dead"`：已经结束的协程，无法再恢复。

- `"normal"`：协程正在运行，但不是当前协程。

### 高级用法：协程与事件驱动

协程可以与事件驱动机制结合，实现复杂的异步流程控制。

```lua
local function eventLoop()
    while true do
        local event = coroutine.yield()
        print("Handling event:", event)
    end
end

local co = coroutine.create(eventLoop)

coroutine.resume(co)  -- 启动协程

-- 模拟事件触发
coroutine.resume(co, "Event 1")  -- 输出: Handling event: Event 1
coroutine.resume(co, "Event 2")  -- 输出: Handling event: Event 2
```

## 11. 模块与包管理

Lua 使用模块系统组织代码，通常通过 `require` 函数加载模块。以下是创建和使用模块的示例。

### 创建模块

```lua
-- math_utils.lua
local math_utils = {}

function math_utils.add(a, b)
    return a + b
end

function math_utils.subtract(a, b)
    return a - b
end

return math_utils
```

### 使用模块

```lua
-- main.lua
local math_utils = require("math_utils")

print(math_utils.add(5, 3))       -- 输出: 8
print(math_utils.subtract(5, 3))  -- 输出: 2
```

### 设置模块搜索路径

```lua
package.path = package.path .. ";/path/to/your/modules/?.lua"
local mymodule = require("mymodule")
```

## 12. 其他有用的 API

### string.gmatch(s, pattern)

- **用途**：返回一个迭代器，用于遍历字符串 `s` 中所有匹配模式 `pattern` 的子串。

- **示例**：

```lua
local s = "one two three"
for word in string.gmatch(s, "%a+") do
    print(word)
end
-- 输出:
-- one
-- two
-- three
```

### string.rep(s, n, sep)

- **用途**：重复字符串 `s` `n` 次，中间可以加上分隔符 `sep`。

- **示例**：

```lua
print(string.rep("Lua", 3, "-"))  -- 输出: Lua-Lua-Lua
```

### math.randomseed(seed)

- **用途**：设置随机数生成器的种子，确保随机数序列的可重复性。

- **示例**：

```lua
math.randomseed(os.time())
print(math.random())  -- 输出: 随机数
```

### io.popen(command, mode)

- **用途**：打开一个管道，执行操作系统命令并读取其输出。

- **示例**：

```lua
local handle = io.popen("ls", "r")
local result = handle:read("*all")
handle:close()
print(result)
```

## 总结

Lua 提供了丰富且强大的标准库，涵盖了从基本数据处理到文件操作、数学计算、协程管理等各个方面。掌握这些常用 API 不仅能提高编写 Lua 脚本的效率，还能帮助你更好地理解和利用 Lua 语言的特性。

**学习建议**：

- **实践练习**：通过编写实际的 Lua 脚本来熟悉这些 API，例如创建简单的游戏脚本或自动化工具。

- **参考文档**：查阅 [Lua 官方文档](https://www.lua.org/manual/5.4/) 了解更多详细信息和高级用法。

- **模块化编程**：学习如何创建和使用 Lua 模块，提高代码的可维护性和复用性。

- **协程与并发**：深入理解协程的工作机制，利用 Lua 的协程实现复杂的异步逻辑。

希望这些信息能帮助你更好地使用 Lua 进行开发！
