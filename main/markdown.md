[toc]
# MarkDown语法整理

日期：2023.08.18

---

## 1. 标题

标题使用#
包含6个级别
# 一级标题 {ignore=true}
## 二级标题 {ignore=true}
### 三级标题 {ignore=true}
#### 四级标题 {ignore=true}
##### 五级标题 {ignore=true}
###### 六级标题 {ignore=true}

## 2. 强调

### 斜体
斜体使用*或者_
*斜体*
_斜体_

### 粗体
粗体使用**或__
**粗体**
__粗体__

### 删除
被划线删除的字使用~~
~~已删除~~

---

## 3. 排序

### 无序排序
无序列表使用-
- a
    - a1 
- b
    - b1
        - b1a
- c

### 有序排序
有序列表使用1.
1. a
   1. a1
   2. a2
2. b
   1. b1
      1. b1a 
      2. b1b
3. c

---

## 4. 引用内容

### 图片
图片格式
```markdown
![Alt Text](url)
```
![GitHub Logo](../img/github_logo.png)

### 链接
链接格式[Name](url)支持自动生成
[GitHub.com](http://github.com)

---
### 引用
引用使用>
> 引用的一段话

### 行内代码
使用反引号
`code`

### 代码块

```html
<p id="id1" class="demo">这是代码块</p>
```

## 5. 任务列表
- [x] todo1
- [x] todo2
- [ ] todo3

## 6. 表格
表头|表头|表头
---|---|---
内容|内容|内容
内容|内容|内容