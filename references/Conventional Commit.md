# Conventional Commits

> **Conventional Commits** 可以理解为一种给 commit message 加上统一格式的规范。

标准格式：

```text
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

最常见的形式其实就一行：

```text
feat: add user login API
fix: resolve null pointer exception
```

---

# 一、最常用的 type

## feat

新增功能

```text
feat: add user registration
feat(auth): support OAuth login
```

对应语义：

> 这个提交给用户带来了新功能。

---

## fix

修复 Bug

```text
fix: handle empty input
fix(api): correct pagination logic
```

对应语义：

> 修复了已有功能的问题。

---

## docs

只修改文档

```text
docs: update README
docs(api): add authentication examples
```

例如：

* README
* API 文档
* 注释说明

---

## style

代码格式调整，不影响逻辑

```text
style: format source code
style: fix indentation
```

例如：

* 调整空格
* 调整换行
* prettier 格式化

不包括逻辑修改。

---

## refactor

重构

```text
refactor: simplify tree traversal
refactor(service): extract validation logic
```

特点：

* 不是新功能
* 不是修 Bug
* 只是改进代码结构

例如：

```cpp
// 原来
if (...) {
    ...
}

// 重构后
validateUser();
```

行为不变。

---

## perf

性能优化

```text
perf: reduce memory allocation
perf(cache): improve lookup speed
```

例如：

* 优化算法复杂度
* 减少内存拷贝

---

## test

测试相关

```text
test: add SeqList unit tests
test(tree): improve coverage
```

例如：

* 新增 GTest
* 修改测试数据

---

## build

构建系统相关

```text
build: update CMake version
build: add SDL dependency
```

例如：

* CMake
* Gradle
* Maven
* npm

---

## ci

CI/CD 配置

```text
ci: add GitHub Actions workflow
ci: update Jenkins pipeline
```

例如：

* GitHub Actions
* GitLab CI
* Jenkins

---

## chore

杂项修改

```text
chore: update dependencies
chore: remove unused files
```

不属于上述任何分类。

很多团队把：

```text
chore: bump version
```

用于版本号更新。

---

## revert

回滚某次提交

```text
revert: feat(auth): support OAuth login
```

或者直接：

```text
Revert "feat(auth): support OAuth login"
```

---

# 二、scope（可选）

scope 用来说明影响范围。

格式：

```text
type(scope): description
```

例如：

```text
feat(auth): add login API
fix(database): handle connection timeout
docs(readme): update installation guide
feat(list): implement SeqList insert
feat(tree): add HuffmanTree
fix(test): repair failing unit tests
build(cmake): upgrade to CMake 4.1
```

scope 不是必须的。

---

# 三、description 规范

一般要求：

* 使用祈使句（imperative mood）
* 首字母小写
* 不加句号

推荐：

```text
feat: add binary tree traversal
fix: handle null pointer
```

不推荐：

```text
feat: Added binary tree traversal
fix: Fixed bug.
```

---

# 四、Breaking Change

如果提交会破坏兼容性，需要显式标记。

例如：

```text
feat!: remove legacy API
```

这里的 `!` 表示：

> Breaking Change

---

也可以写 Footer：

```text
feat: redesign user API

BREAKING CHANGE: user id is now UUID
```

---

# 五、与 Semantic Versioning 的关系

很多自动发布工具会根据 Commit 自动计算版本号：

| Commit          | Version |
| --------------- | ------- |
| feat            | Minor   |
| fix             | Patch   |
| BREAKING CHANGE | Major   |

例如：

```text
fix: repair memory leak
```

```text
1.2.3 → 1.2.4
```

---

```text
feat: add search feature
```

```text
1.2.3 → 1.3.0
```

---

```text
feat!: redesign API
```

```text
1.2.3 → 2.0.0
```

---

# 六、一个完整例子

```text
feat(tree): implement Huffman encoding

Add Huffman tree construction and encoding logic.

Closes #123
```

结构：

```text
feat(tree): implement Huffman encoding
│    │
│    └── scope
└─────── type
```

---

