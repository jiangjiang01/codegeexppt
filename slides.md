---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides, markdown enabled
title: AI编程工具
info: AI编程工具，CodeGeex
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# CodeGeeX 智能编程助手

<div class="user">
  <div>分享人：姜姜</div>
  <div>职位：前端开发</div>
</div>

<style>
.user {
  position: absolute;
  bottom: 100px;
  right: 50px;
  text-align: right;
  line-height: 2;
}
</style>

---

# 简介

## 1. AI 编程工具的作用和重要性

## 2. CodeGeex 的背景介绍和开发目的

---

# AI 编程工具的作用和重要性

- 提高编码效率
- 优化代码质量
- 加速原型设计和开发周期
- 改善开发者工作体验
- 推动技术创新和产业发展
- ...

---

# CodeGeeX是什么？

- CodeGeeX是一款基于大模型的全能的智能编程助手
- 它可以实现代码的生成与补全、自动添加注释、代码翻译以及智能问答等功能，能够帮助开发者显著提高工作效率
- CodeGeeX支持主流的编程语言，并适配多种主流IDE
- 针对个人开发者完全免费

---

# CodeGeex 功能详解

- 代码自动生成和补全
- 自动添加注释
- 修正代码的bug
- 解释选中的代码
- `command` + `i` 自动生成功能
- 代码翻译
- 智能问答

---

# 代码自动生成和补全

twoSum 示例

```ts twoslash
// 两数之和
function twoSum(nums: number[], target: number): number[] {
  const map = new Map<number, number>();
  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];
    if (map.has(complement)) {
      return [map.get(complement)!, i];
    }
  }
}
```

---

# 自动添加注释

````md magic-move
```ts
// 两数之和
function twoSum(nums: number[], target: number): number[] {
  const map = new Map<number, number>();
  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];
    if (map.has(complement)) {
      return [map.get(complement)!, i];
    }
  }
}
```

```ts {all|3|5|7|9|13|all}
// 两数之和
function twoSum(nums: number[], target: number): number[] {
  // 创建一个Map，用于存储数组中的数字及其索引
  const map = new Map<number, number>();
  // 遍历数组
  for (let i = 0; i < nums.length; i++) {
    // 计算目标值与当前元素的差值
    const complement = target - nums[i];
    // 如果Map中存在该差值，则返回差值的索引和当前元素的索引
    if (map.has(complement)) {
      return [map.get(complement)!, i];
    }
    // 将当前元素及其索引存入Map
    map.set(nums[i], i);
  }
}
```
````

---

# 修正代码的bug

- 方式一：直接使用 `/fixbug`，会发现生成的代码和之前一模一样

- 方式二：换种方式修复 `修复未找到时的返回值问题`

````md magic-move
```ts
// 两数之和
function twoSum(nums: number[], target: number): number[] {
  // 创建一个Map，用于存储数组中的数字及其索引
  const map = new Map<number, number>();
  // 遍历数组
  for (let i = 0; i < nums.length; i++) {
    // 计算目标值与当前元素的差值
    const complement = target - nums[i];
    // 如果Map中存在该差值，则返回差值的索引和当前元素的索引
    if (map.has(complement)) {
      return [map.get(complement)!, i];
    }
    // 将当前元素及其索引存入Map
    map.set(nums[i], i);
  }
}
```

```ts{all|16-17|all}
// 两数之和
function twoSum(nums: number[], target: number): number[] {
  // 创建一个Map，用于存储数组中的数字及其索引
  const map = new Map<number, number>();
  // 遍历数组
  for (let i = 0; i < nums.length; i++) {
    // 计算目标值与当前元素的差值
    const complement = target - nums[i];
    // 如果Map中存在该差值，则返回差值的索引和当前元素的索引
    if (map.has(complement)) {
      return [map.get(complement)!, i];
    }
    // 将当前元素及其索引存入Map
    map.set(nums[i], i);
  }
  // 如果没有找到元素，则返回空数组
  return [];
}
```
````

---

# 解释选中的代码

<div class="text-center text-3xl mt-20">功能演示</div>

---

# `command` + `i` 自动生成功能

创建 `utils.ts` 文件，输入以下内容

```md
生成以下函数：浅拷贝、校验手机号，判断当前时间是否为周末，判断当前时间是否为工作日
```

自动生成文件内容

```ts {all}{maxHeight: '200px'}
function shallowCopy<T extends any>(obj: T): T {
  return Object.assign({}, obj);
}

function isValidPhoneNumber(phoneNumber: string): boolean {
  // 验证手机号的正则表达式
  const regex = /^1[3-9]\d{9}$/;
  return regex.test(phoneNumber);
}

function isWeekend(): boolean {
  const now = new Date();
  const dayOfWeek = now.getDay();
  return dayOfWeek === 0 || dayOfWeek === 6;
}

function isWeekday(): boolean {
  const now = new Date();
  const dayOfWeek = now.getDay();
  return dayOfWeek !== 0 && dayOfWeek !== 6;
}
```

---

# 代码翻译

`ts` 代码转为 `java` 代码

```java {all}{maxHeight: '300px'}
import java.util.HashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        int[] nums = {2, 7, 11, 15};
        int target = 9;
        int[] result = twoSum(nums, target);
        System.out.println("[" + result[0] + ", " + result[1] + "]");
    }

    public static int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        return new int[0];
    }
}
```

---

# 优势与局限性

## 优势

- 高准确性的代码生成
- 丰富的编程语言支持
- 提高编码效率和质量

## 局限性

- 部分特定领域的代码理解能力有限
- 代码质量检查准确性有待提升

---

# 问答&讨论

<style>
  h1 {
    padding-top: 25vh;
    text-align: center;
  }
</style>

---

# 结束，谢谢！

<style>
  h1 {
    padding-top: 25vh;
    text-align: center;
  }
</style>
