# json-to-ts

一个极其精简的 JSON 到 TypeScript 接口转换工具。

## 功能特性

- 🔄 **智能类型推断** - 自动识别 JSON 中的字符串、数字、布尔值、数组等类型
- 🏗️ **嵌套对象支持** - 自动为嵌套对象创建独立的接口定义
- 📋 **数组类型处理** - 支持单维和多维数组的类型推断
- 🔧 **命名规范化** - 自动将属性名转换为驼峰命名，类型名转换为帕斯卡命名
- 🎯 **可选属性处理** - 对 null 值自动标记为可选属性
- 📦 **零依赖** - 仅使用 underscore 库进行辅助函数处理

## 安装

```bash
npm install @gausszhou/json-to-ts
```

## 快速开始

```typescript
import { Json2Ts } from '@gausszhou/json-to-ts';

const json2ts = new Json2Ts();

// 基本用法
const json = `{
  "name": "张三",
  "age": 30,
  "isActive": true
}`;

const result = json2ts.convert(json);
console.log(result);
```

输出结果：
```typescript
export interface RootObject {
  name: string;
  age: number;
  isActive: boolean;
}
```

## 支持的类型

- ✅ 基本类型: `string`, `number`, `boolean`
- ✅ 数组类型: `string[]`, `number[]`, `boolean[]`, `any[]`
- ✅ 多维数组: `string[][]`, `number[][][]` 等
- ✅ 嵌套对象: 自动创建子接口
- ✅ 可选属性: 对 null 值自动标记为 `?`
- ✅ 日期类型: 自动识别为 `Date` 类型

## 注意事项

- 确保输入的 JSON 字符串是有效的
- 对于空数组，默认类型为 `any[]`
- 属性名会自动转换为小驼峰命名
- 类型名会自动转换为帕斯卡命名并移除复数形式