# Basic 模块

## 模块简介

Basic模块是学途应用的基础功能模块，提供通用的工具类、常量定义和路由管理功能，为其他模块提供基础支持。

## 模块结构

```
common/basic/
├── src/main/ets/
│   ├── constants/             # 常量定义
│   │   └── CommonEnums.ets   # 枚举类型定义
│   ├── utils/                # 工具类
│   │   ├── Logger.ets        # 日志工具
│   │   ├── PreferenceUtil.ets # 偏好设置工具
│   │   └── RouterModule.ets  # 路由管理
│   └── components/           # 通用组件
│       └── MainPage.ets      # 主页面组件
└── src/main/resources/       # 资源文件
```

## 功能特性

### 1. 路由管理 (RouterModule)
- **页面跳转**：支持push、replace、back等路由操作
- **参数传递**：支持页面间参数传递和获取
- **堆栈管理**：管理页面导航堆栈

### 2. 日志工具 (Logger)
- **分级日志**：支持INFO、WARN、ERROR等日志级别
- **格式化输出**：统一的日志格式和标签管理

### 3. 偏好设置 (PreferenceUtil)
- **数据存储**：本地轻量级数据存储
- **键值管理**：统一的键值对存储管理

### 4. 常量定义 (CommonEnums)
- **路由枚举**：定义所有页面路由标识
- **存储键值**：定义应用存储的键名

## 核心类说明

### CommonEnums.ets
```typescript
export enum RouterMap {
  LAUNCH_PAGE = 'LaunchPage',
  HOME_PAGE = 'HomePage',
  MESSAGE_PAGE = 'MessagePage',
  // ... 其他路由定义
}

export enum AppStorageMap {
  USER_INFO = 'userInfo',
  TOKEN = 'token',
  PRIVACY_POLICY_KEY = '0'
}
```

### RouterModule.ets
```typescript
public static push(url: RouterMap | string, param?: object): void
public static replace(url: RouterMap | string, param?: object): void
public static back(): void
public static getNavParam<T>(url: RouterMap | string): T | undefined
```

### Logger.ets
```typescript
public static info(tag: string, message: string): void
public static warn(tag: string, message: string): void
public static error(tag: string, message: string): void
```

### PreferenceUtil.ets
```typescript
public static getInstance(): PreferenceUtil
public get(key: string, defaultValue: string): string
public set(key: string, value: string): void
```

## 使用指南

### 路由跳转
```typescript
import { RouterMap, RouterModule } from 'basic';

// 跳转到消息页面
RouterModule.push(RouterMap.MESSAGE_PAGE);

// 带参数跳转
RouterModule.push(RouterMap.COURSE_DETAIL_PAGE, {
  courseId: 1,
  courseTitle: 'Java编程入门'
});
```

### 日志记录
```typescript
import { Logger } from 'basic';

Logger.info('HomePage', '页面加载完成');
Logger.error('Network', '网络请求失败');
```

### 数据存储
```typescript
import { PreferenceUtil, AppStorageMap } from 'basic';

// 存储数据
PreferenceUtil.getInstance().set(AppStorageMap.TOKEN, 'user-token');

// 读取数据
const token = PreferenceUtil.getInstance().get(AppStorageMap.TOKEN, '');
```

## 依赖关系

- 本模块为其他功能模块提供基础支持
- 不依赖其他业务模块
- 使用HarmonyOS基础API

## 开发规范

### 代码规范
- 使用TypeScript严格模式
- 类和方法命名采用PascalCase
- 常量和枚举命名采用UPPER_CASE

### 接口设计
- 提供清晰的API文档
- 保持向后兼容性
- 统一的错误处理机制

## 版本信息

- 模块名称：Basic
- 模块类型：基础功能模块
- 维护状态：稳定维护中