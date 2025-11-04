# @oranges06/basic

## 简介

这是一个鸿蒙开发学习的基础工具包，提供通用的工具类、常量定义和路由管理功能，为HarmonyOS应用开发提供基础支持。

## 安装

```bash
ohpm install @oranges06/basic
```

## 使用

### 基本使用示例

#### 路由管理
```typescript
import { RouterMap, RouterModule } from '@oranges06/basic';

// 跳转到消息页面
RouterModule.push(RouterMap.MESSAGE_PAGE);

// 带参数跳转
RouterModule.push(RouterMap.COURSE_DETAIL_PAGE, {
  courseId: 1,
  courseTitle: 'Java编程入门'
});
```

#### 日志记录
```typescript
import { Logger } from '@oranges06/basic';

Logger.info('HomePage', '页面加载完成');
Logger.error('Network', '网络请求失败');
```

#### 数据存储
```typescript
import { PreferenceUtil, AppStorageMap } from '@oranges06/basic';

// 存储数据
PreferenceUtil.getInstance().set(AppStorageMap.TOKEN, 'user-token');

// 读取数据
const token = PreferenceUtil.getInstance().get(AppStorageMap.TOKEN, '');
```

### 核心功能

#### 路由管理 (RouterModule)
- **页面跳转**：支持push、replace、back等路由操作
- **参数传递**：支持页面间参数传递和获取
- **堆栈管理**：管理页面导航堆栈

#### 日志工具 (Logger)
- **分级日志**：支持INFO、WARN、ERROR等日志级别
- **格式化输出**：统一的日志格式和标签管理

#### 偏好设置 (PreferenceUtil)
- **数据存储**：本地轻量级数据存储
- **键值管理**：统一的键值对存储管理

#### 常量定义 (CommonEnums)
- **路由枚举**：定义所有页面路由标识
- **存储键值**：定义应用存储的键名

### API 参考

#### RouterModule
```typescript
public static push(url: RouterMap | string, param?: object): void
public static replace(url: RouterMap | string, param?: object): void
public static back(): void
public static getNavParam<T>(url: RouterMap | string): T | undefined
```

#### Logger
```typescript
public static info(tag: string, message: string): void
public static warn(tag: string, message: string): void
public static error(tag: string, message: string): void
```

#### PreferenceUtil
```typescript
public static getInstance(): PreferenceUtil
public get(key: string, defaultValue: string): string
public set(key: string, value: string): void
```

## 开发环境

- HarmonyOS SDK: >= 5.0.0
- TypeScript: 支持严格模式

## 许可证

Apache-2.0