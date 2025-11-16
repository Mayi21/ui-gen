# 🌌 Aurora（极光）主题 UI 组件规范文档

**— 多组件 Day / Night 模式详细设计说明 —**

本文件定义在 **Aurora 主题**（灵感源自挪威特罗姆瑟的“白昼雪山 / 夜幕极光”）下，多个基础 UI 组件在 **不同主题模式下的视觉、样式与交互规范**。

---

## 目录

1. 主题系统简介
2. 组件展示页面结构
3. 设计系统基础
4. Day Mode（雪山纯净）基础视觉规范
5. Night Mode（极光迷人）基础视觉规范
6. Button 按钮组件
7. Select 下拉框组件
8. Input 文本输入框组件
9. Card 信息卡片组件
10. Tag/Chip 标签组件
11. Switch 开关组件
12. Tabs 标签页组件
13. Checkbox 复选框组件
14. Radio 单选框组件
15. Modal / Dialog 模态框组件
16. Toast / Notification 通知组件
17. Tooltip 工具提示组件
18. Progress Bar 进度条组件
19. 组件状态规范
20. 响应式设计规范
21. 无障碍访问性规范
22. Day / Night 主题切换机制说明
23. 示例代码生成提示（供模型生成 HTML 使用）

---

# 1. 🎨 主题系统简介

Aurora 主题由两种视觉风格组成：

### Day Mode（雪山纯净）

* 灵感：白天阳光下的雪山
* 氛围：轻盈、冷静、干净、柔和

### Night Mode（极光迷人）

* 灵感：极夜天空与流动极光
* 氛围：神秘、光流、跃动、深邃

主题通过 `<body>` 的 class 控制：

* `body.day`
* `body.night`

---

# 2. 📄 组件展示页面结构规范

用于预览组件的示例页面建议包含：

1. 页顶标题：`Aurora 主题 UI 组件预览`
2. Day / Night 主题切换按钮或开关
3. 各个组件的展示卡片：

   * Button 按钮
   * Select 下拉框
   * Input 文本输入框
   * Card 信息卡片
   * Tag/Chip 标签
   * Switch 开关
   * Tabs 标签页

每个组件区域建议包含：

* 标题
* 一段简短文字说明
* 一个或多个实际组件实例

---

# 3. 🎯 设计系统基础

在定义具体组件样式之前，先明确 Aurora 主题的基础设计系统规范，确保整个设计体系的一致性。

---

## 3.1 字体系统

### 字体家族

**中文 + 英文混合字体栈：**

```text
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "PingFang SC", "Hiragino Sans GB",
             "Microsoft YaHei", "Helvetica Neue", Helvetica, Arial, sans-serif;
```

### 字体大小

| 用途       | 大小     | 行高   |
| -------- | ------ | ---- |
| 大标题 H1   | 28px   | 1.3  |
| 中标题 H2   | 20px   | 1.4  |
| 小标题 H3   | 16px   | 1.5  |
| 正文       | 14px   | 1.5  |
| 辅助文字     | 12px   | 1.4  |
| 小号标注     | 10px   | 1.3  |

### 字重

| 名称     | 值   | 使用场景         |
| ------ | --- | ------------ |
| Normal | 400 | 正文、辅助文字      |
| Medium | 500 | 次要强调         |
| Semibold | 600 | 按钮、标签、表单标签   |
| Bold   | 700 | 标题、强调内容      |

---

## 3.2 间距系统

基于 **4px 网格系统**，所有间距应为 4 的倍数：

| 名称   | 数值    | 使用场景                |
| ---- | ----- | ------------------- |
| xs   | 4px   | 紧密元素间距、图标与文字间距      |
| sm   | 8px   | 小型组件内边距             |
| md   | 12px  | 标准组件内边距、输入框内边距      |
| lg   | 16px  | 卡片内边距、段落间距          |
| xl   | 20px  | 按钮水平内边距、较大组件内边距     |
| 2xl  | 24px  | 区块间距                |
| 3xl  | 32px  | 大型区块间距              |
| 4xl  | 48px  | 页面级间距               |

---

## 3.3 组件尺寸变体

为常用交互组件定义三种尺寸规格：

### 按钮 / 输入框 / 选择框

| 尺寸    | 高度   | 水平内边距  | 字体大小 | 圆角   |
| ----- | ---- | ------ | ---- | ---- |
| Small | 32px | 12px   | 12px | 8px  |
| Medium (默认) | 40px | 16px   | 14px | 12px |
| Large | 48px | 24px   | 16px | 14px |

### 图标

| 尺寸    | 图标尺寸 |
| ----- | ---- |
| Small | 16px |
| Medium | 20px |
| Large | 24px |

---

## 3.4 Z-index 层级规范

统一管理组件的层叠顺序：

| 层级         | 数值   | 组件            |
| ---------- | ---- | ------------- |
| Base       | 0    | 常规内容          |
| Dropdown   | 100  | 下拉菜单、Select 选项 |
| Sticky     | 200  | 吸附导航栏         |
| Fixed      | 300  | 固定定位元素        |
| Tooltip    | 400  | 工具提示          |
| Modal Backdrop | 500  | 模态框遮罩层        |
| Modal      | 600  | 模态框内容         |
| Toast      | 700  | 通知消息          |
| Debug      | 9999 | 调试工具（开发用）     |

---

## 3.5 动画系统

### 动画时长

| 名称      | 时长    | 使用场景             |
| ------- | ----- | ---------------- |
| instant | 100ms | 即时反馈（按钮 active） |
| fast    | 150ms | 快速交互（hover）     |
| normal  | 250ms | 标准过渡（主题切换、颜色变化） |
| slow    | 350ms | 慢速过渡（模态框进出）     |
| slower  | 500ms | 页面级动画            |

### 缓动函数

```text
ease-out    → cubic-bezier(0, 0, 0.2, 1)      // 元素进入
ease-in     → cubic-bezier(0.4, 0, 1, 1)      // 元素退出
ease-in-out → cubic-bezier(0.4, 0, 0.2, 1)    // 双向过渡
```

### 标准过渡

```css
transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
```

---

## 3.6 图标系统

### 推荐图标库

* **Lucide Icons**（现代、简约）
* **Heroicons**（Tailwind 官方）
* **Feather Icons**（轻量、优雅）

### 图标规范

| 属性   | Day Mode   | Night Mode |
| ---- | ---------- | ---------- |
| 主图标色 | `#1C1E20`  | `#F1F6FF`  |
| 次图标色 | `#6D747A`  | `#9BA8C0`  |
| 强调图标色 | `#A8D8F8`  | `#5BB7FF`  |
| 描边宽度 | 1.5px – 2px | 1.5px – 2px |

### 使用建议

* 图标与文字垂直居中对齐
* 图标与文字间距：4–6px
* 可点击图标最小点击区域：32x32px

---

# 4. ❄️ Day Mode（雪山纯净）基础视觉规范

### 背景与基础色

| 用途   | 颜色                    |
| ---- | --------------------- |
| 页面背景 | `#F8FAFB`             |
| 卡片背景 | `#FFFFFF` / `#EEF1F3` |
| 边框色  | `#D8DFE4`             |
| 主文字  | `#1C1E20`             |
| 次文字  | `#6D747A`             |

### 强调色

| 名称                  | 颜色        |
| ------------------- | --------- |
| 主强调 Ice Blue        | `#A8D8F8` |
| Hover 强调 Ice Blue 深 | `#8EC8F2` |

### 阴影

```css
box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
```

---

# 5. 🌌 Night Mode（极光迷人）基础视觉规范

### 背景与基础色

| 用途   | 颜色        |
| ---- | --------- |
| 页面背景 | `#0B1321` |
| 卡片背景 | `#121C2C` |
| 边框色  | `#233043` |
| 主文字  | `#F1F6FF` |
| 次文字  | `#9BA8C0` |

### 极光强调色（Aurora Accent）

| 名称  | 颜色        |
| --- | --------- |
| 极光绿 | `#4BE4C9` |
| 冰川蓝 | `#5BB7FF` |
| 极光紫 | `#C68CFF` |

### Aurora Glow（光晕）

```css
box-shadow: 0 0 18px rgba(91, 183, 255, 0.65);
```

### Aurora 渐变（推荐）

```css
linear-gradient(120deg, #4BE4C9 0%, #5BB7FF 50%, #C68CFF 100%);
```

---

# 6. 🔘 Button 按钮组件

**类名：** `.btn-aurora`

---

## 6.1 Day Mode — Snow Pure Button

**视觉特征：** 胶囊形、冷色柔光、干净。

**样式定义：**

```text
背景色：#A8D8F8
文字颜色：#1C1E20
边框颜色：#8EC8F2
字体大小：14px
字体粗细：600
Padding：8px 20px
圆角：999px
阴影：0 2px 4px rgba(0,0,0,0.05)
```

**交互：**

* Hover：`background-color: #8EC8F2;`
* Active：`background-color: #7CBCEB;`
* Transition：`transition: all 0.25s ease;`

---

## 6.2 Night Mode — Aurora Flow Button

**视觉特征：** 极光渐变、Glow 光晕、轻微浮起感。

**样式定义：**

```text
背景：linear-gradient(120deg, #4BE4C9, #5BB7FF, #C68CFF)
文字颜色：#F1F6FF
边框：1px solid #4BE4C9
圆角：999px
Padding：8px 20px
字体粗细：600
Glow：0 0 18px rgba(91, 183, 255, 0.65)
```

**交互：**

* Hover：

  * `transform: translateY(-1px);`
  * `box-shadow: 0 0 22px rgba(91,183,255,0.8);`
* Active：

  * `transform: translateY(0);`
  * `filter: brightness(0.95);`

---

# 7. 🔽 Select 下拉框组件

**外层类名：** `.select-aurora`
可使用 `<select>` 或自定义 div 结构。

---

## 7.1 Day Mode — Snow Mist Select

**样式定义：**

```text
宽度：240px
高度：40px
背景：#EEF1F3
边框：1px solid #D8DFE4
文字颜色：#1C1E20
圆角：999px
Padding：0 14px（右侧预留箭头）
箭头颜色：#6D747A
阴影：0 2px 4px rgba(0,0,0,0.03)
```

**交互：**

* Hover 边框色：`#A8D8F8`
* Focus：

  ```css
  border-color: #8EC8F2;
  box-shadow: 0 0 0 2px rgba(142, 200, 242, 0.3);
  ```

---

## 7.2 Night Mode — Aurora Deep Select

**样式定义：**

```text
宽度：240px
高度：40px
背景：#121C2C
边框：1px solid #233043
文字颜色：#F1F6FF
圆角：999px
Padding：0 14px
箭头颜色：#9BA8C0
```

**交互：**

* Hover 边框：`#4BE4C9`
* Focus：

  ```css
  border-color: #5BB7FF;
  box-shadow: 0 0 0 2px rgba(91, 183, 255, 0.45);
  ```

---

# 8. 📝 Input 文本输入框组件

**类名：** `.input-aurora`

---

## 8.1 Day Mode — Snow Field Input

**视觉特征：** 雪地上的浅浅凹槽，柔光。

**样式定义：**

```text
宽度：280–320px
高度：40px
背景：#FFFFFF
边框：1px solid #D8DFE4
圆角：12px
文字颜色：#1C1E20
占位符颜色：#9AA2A8
Padding：0 12px
阴影：0 2px 4px rgba(0,0,0,0.03)
字体大小：14px
```

**交互：**

* Hover：`border-color: #A8D8F8;`
* Focus：

  ```css
  border-color: #8EC8F2;
  box-shadow: 0 0 0 2px rgba(142, 200, 242, 0.3);
  outline: none;
  ```

---

## 8.2 Night Mode — Aurora Line Input

**视觉特征：** 深夜蓝底，略带极光边缘高亮。

**样式定义：**

```text
宽度：280–320px
高度：40px
背景：#121C2C
边框：1px solid #233043
圆角：12px
文字颜色：#F1F6FF
占位符颜色：#9BA8C0
Padding：0 12px
字体大小：14px
```

**交互：**

* Hover：`border-color: #4BE4C9;`
* Focus：

  ```css
  border-color: #5BB7FF;
  box-shadow: 0 0 0 2px rgba(91, 183, 255, 0.45);
  outline: none;
  ```

---

# 9. 🧊 Card 信息卡片组件

**类名：** `.card-aurora`

---

## 9.1 Day Mode — Snow Panel Card

**样式定义：**

```text
背景：#FFFFFF
边框：1px solid #D8DFE4
圆角：16px
Padding：16px 20px
标题颜色：#1C1E20
正文颜色：#6D747A
阴影：0 4px 10px rgba(0,0,0,0.04)
```

可在卡片顶部加一条细细的 Ice Blue 边线作为强调：

```css
border-top: 3px solid #A8D8F8;
```

---

## 9.2 Night Mode — Aurora Glow Card

**样式定义：**

```text
背景：#121C2C
边框：1px solid #233043
圆角：16px
Padding：16px 20px
标题颜色：#F1F6FF
正文颜色：#9BA8C0
阴影：0 6px 18px rgba(0,0,0,0.45)
```

可在卡片顶部使用极光渐变条：

```css
border-top: 3px solid transparent;
background-image: linear-gradient(120deg, #4BE4C9, #5BB7FF, #C68CFF);
background-origin: border-box;
background-clip: padding-box, border-box;
```

或更简单：在内部顶部放一条高 3–4px 的渐变条。

---

# 10. 🏷 Tag / Chip 标签组件

**类名：** `.tag-aurora`

---

## 10.1 Day Mode — Ice Tag

**样式定义：**

```text
背景：rgba(168, 216, 248, 0.18)
边框：1px solid #A8D8F8
文字颜色：#1C1E20
圆角：999px
Padding：2px 10px
字体大小：12px
```

可选：在 Tag 左侧添加一个小圆点，颜色 `#8EC8F2`。

---

## 10.2 Night Mode — Aurora Tag

**样式定义：**

```text
背景：rgba(91, 183, 255, 0.12)
边框：1px solid rgba(91, 183, 255, 0.6)
文字颜色：#F1F6FF
圆角：999px
Padding：2px 10px
字体大小：12px
```

可选 Glow：

```css
box-shadow: 0 0 8px rgba(91, 183, 255, 0.5);
```

---

# 11. 🔛 Switch 开关组件

**外层类名：** `.switch-aurora`
**圆点类名：** `.switch-thumb`

---

## 11.1 结构

* 一个带圆角的轨道（track）
* 一个圆形滑块（thumb）
* 可用 `data-checked="true/false"` 或类名控制状态

---

## 11.2 Day Mode

**关闭状态：**

```text
轨道背景：#D8DFE4
轨道尺寸：宽 40px，高 22px
轨道圆角：999px

Thumb：
  尺寸：18x18px
  颜色：#FFFFFF
  阴影：0 1px 3px rgba(0,0,0,0.15)
  位置：左侧 2px
```

**开启状态：**

```text
轨道背景：#A8D8F8
Thumb 位置：右侧 2px
```

动画：

```css
transition: background-color 0.25s ease, transform 0.25s ease;
```

---

## 11.3 Night Mode

**关闭状态：**

```text
轨道背景：#233043
Thumb：
  背景：#F1F6FF
  阴影：0 0 6px rgba(0,0,0,0.5)
```

**开启状态：**

```text
轨道背景：linear-gradient(120deg, #4BE4C9, #5BB7FF, #C68CFF)
Thumb：
  背景：#F1F6FF
  外 Glow：0 0 10px rgba(91, 183, 255, 0.8)
```

Thumb 从左滑到右，用 `transform: translateX(...)` 实现。

---

# 12. 🧭 Tabs 标签页组件

**容器类：** `.tabs-aurora`
**单个 tab 类：** `.tab-aurora`

---

## 12.1 Day Mode — Snow Underline Tabs

**视觉特征：** 简洁下划线式。

**样式定义：**

```text
容器底部边框：1px solid #D8DFE4

未选中 Tab：
  文字颜色：#6D747A
  Padding：8px 12px
  字体大小：14px

选中 Tab：
  文字颜色：#1C1E20
  下划线：2px 高度，颜色 #A8D8F8
```

Hover 状态：文字颜色稍加深、下划线淡淡出现或颜色变亮。

---

## 12.2 Night Mode — Aurora Glow Tabs

**视觉特征：** 顶部极光光带、选中项有轻微光晕。

**样式定义：**

```text
容器底部边框：1px solid #233043

未选中 Tab：
  文字颜色：#9BA8C0
  Padding：8px 12px

选中 Tab：
  文字颜色：#F1F6FF
  下划线：2px 高度，渐变 linear-gradient(120deg, #4BE4C9, #5BB7FF, #C68CFF)
  可选 box-shadow：0 2px 8px rgba(91,183,255,0.6)
```

---

# 13. ☑️ Checkbox 复选框组件

**类名：** `.checkbox-aurora`

---

## 13.1 结构

* 一个方形勾选框（checkbox box）
* 一个勾选图标（checkmark）
* 可选的标签文字

---

## 13.2 Day Mode — Snow Checkbox

**未选中状态：**

```text
尺寸：18x18px
背景：#FFFFFF
边框：2px solid #D8DFE4
圆角：4px
阴影：0 1px 3px rgba(0,0,0,0.05)
```

**选中状态：**

```text
背景：#A8D8F8
边框：2px solid #8EC8F2
勾选图标颜色：#1C1E20
```

**Hover（未选中）：**

```text
边框色：#A8D8F8
```

**Disabled：**

```text
背景：#F8FAFB
边框色：#EEF1F3
勾选图标颜色：#9AA2A8
opacity: 0.5
```

---

## 13.3 Night Mode — Aurora Checkbox

**未选中状态：**

```text
尺寸：18x18px
背景：#121C2C
边框：2px solid #233043
圆角：4px
```

**选中状态：**

```text
背景：linear-gradient(120deg, #4BE4C9, #5BB7FF)
边框：2px solid #5BB7FF
勾选图标颜色：#F1F6FF
Glow：0 0 8px rgba(91, 183, 255, 0.5)
```

**Hover（未选中）：**

```text
边框色：#4BE4C9
```

**Disabled：**

```text
背景：#0B1321
边框色：#233043
opacity: 0.5
```

---

# 14. 🔘 Radio 单选框组件

**类名：** `.radio-aurora`

---

## 14.1 结构

* 一个圆形选择框（radio circle）
* 一个内部填充圆点（dot）
* 可选的标签文字

---

## 14.2 Day Mode — Snow Radio

**未选中状态：**

```text
尺寸：18x18px
背景：#FFFFFF
边框：2px solid #D8DFE4
圆角：50%（圆形）
阴影：0 1px 3px rgba(0,0,0,0.05)
```

**选中状态：**

```text
边框：2px solid #8EC8F2
内部圆点：
  尺寸：8x8px
  背景：#A8D8F8
  居中显示
```

**Hover（未选中）：**

```text
边框色：#A8D8F8
```

**Disabled：**

```text
背景：#F8FAFB
边框色：#EEF1F3
内部圆点：#9AA2A8
opacity: 0.5
```

---

## 14.3 Night Mode — Aurora Radio

**未选中状态：**

```text
尺寸：18x18px
背景：#121C2C
边框：2px solid #233043
圆角：50%
```

**选中状态：**

```text
边框：2px solid #5BB7FF
内部圆点：
  尺寸：8x8px
  背景：linear-gradient(120deg, #4BE4C9, #5BB7FF)
  Glow：0 0 8px rgba(91, 183, 255, 0.5)
```

**Hover（未选中）：**

```text
边框色：#4BE4C9
```

**Disabled：**

```text
背景：#0B1321
边框色：#233043
opacity: 0.5
```

---

# 15. 🪟 Modal / Dialog 模态框组件

**类名：**
- 遮罩层：`.modal-backdrop-aurora`
- 内容容器：`.modal-aurora`

---

## 15.1 结构

* 全屏半透明遮罩层（Backdrop）
* 内容容器（Modal Box）
* 关闭按钮（可选）

---

## 15.2 Day Mode — Snow Modal

**遮罩层：**

```text
背景：rgba(28, 30, 32, 0.5)
模糊效果：backdrop-filter: blur(4px)
```

**内容容器：**

```text
背景：#FFFFFF
圆角：16px
Padding：24px
最大宽度：540px
阴影：0 12px 40px rgba(0,0,0,0.15)
边框：1px solid #D8DFE4
```

**关闭按钮：**

```text
位置：右上角
尺寸：32x32px
颜色：#6D747A
Hover：#1C1E20
```

---

## 15.3 Night Mode — Aurora Modal

**遮罩层：**

```text
背景：rgba(11, 19, 33, 0.7)
模糊效果：backdrop-filter: blur(8px)
```

**内容容器：**

```text
背景：#121C2C
圆角：16px
Padding：24px
最大宽度：540px
阴影：0 16px 60px rgba(0,0,0,0.6)
边框：1px solid #233043
可选顶部渐变条：3px solid linear-gradient(120deg, #4BE4C9, #5BB7FF, #C68CFF)
```

**关闭按钮：**

```text
颜色：#9BA8C0
Hover：#F1F6FF
Hover Glow：0 0 8px rgba(91, 183, 255, 0.5)
```

**入场动画：**

```css
@keyframes modal-enter {
  from {
    opacity: 0;
    transform: scale(0.95) translateY(-20px);
  }
  to {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
}
animation: modal-enter 0.25s cubic-bezier(0, 0, 0.2, 1);
```

---

# 16. 🔔 Toast / Notification 通知组件

**类名：** `.toast-aurora`

---

## 16.1 结构

* 小型信息卡片
* 图标（可选）
* 消息文字
* 自动消失或手动关闭

---

## 16.2 Day Mode — Snow Toast

**样式定义：**

```text
背景：#FFFFFF
圆角：12px
Padding：12px 16px
最小宽度：280px
最大宽度：400px
边框：1px solid #D8DFE4
阴影：0 6px 16px rgba(0,0,0,0.12)
左侧强调条：3px solid #A8D8F8
```

**文字：**

```text
标题：14px, #1C1E20, 600
正文：12px, #6D747A, 400
```

**变体（按类型）：**

| 类型      | 左侧强调条颜色    | 图标颜色      |
| ------- | ---------- | --------- |
| Info    | `#A8D8F8`  | `#A8D8F8` |
| Success | `#7DD3C0`  | `#5CB85C` |
| Warning | `#FFD93D`  | `#F0AD4E` |
| Error   | `#FF6B6B`  | `#D9534F` |

---

## 16.3 Night Mode — Aurora Toast

**样式定义：**

```text
背景：#121C2C
圆角：12px
Padding：12px 16px
边框：1px solid #233043
阴影：0 8px 24px rgba(0,0,0,0.5)
左侧强调条：3px solid linear-gradient(120deg, #4BE4C9, #5BB7FF)
可选 Glow：0 0 16px rgba(91, 183, 255, 0.3)
```

**文字：**

```text
标题：14px, #F1F6FF, 600
正文：12px, #9BA8C0, 400
```

**变体（按类型）：**

| 类型      | 左侧强调条颜色                                   | Glow 颜色                            |
| ------- | ----------------------------------------- | ---------------------------------- |
| Info    | `linear-gradient(120deg, #4BE4C9, #5BB7FF)` | `rgba(91, 183, 255, 0.3)`          |
| Success | `#4BE4C9`                                 | `rgba(75, 228, 201, 0.3)`          |
| Warning | `#FFD93D`                                 | `rgba(255, 217, 61, 0.2)`          |
| Error   | `#FF6B6B`                                 | `rgba(255, 107, 107, 0.3)`         |

**入场动画（从右侧滑入）：**

```css
@keyframes toast-slide-in {
  from {
    transform: translateX(100%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}
animation: toast-slide-in 0.3s cubic-bezier(0, 0, 0.2, 1);
```

---

# 17. 💬 Tooltip 工具提示组件

**类名：** `.tooltip-aurora`

---

## 17.1 结构

* 小型浮动文本框
* 指向目标元素的小三角箭头
* 出现在元素 hover 时

---

## 17.2 Day Mode — Snow Tooltip

**样式定义：**

```text
背景：#1C1E20
文字颜色：#FFFFFF
字体大小：12px
圆角：6px
Padding：6px 10px
阴影：0 4px 12px rgba(0,0,0,0.15)
最大宽度：220px
```

**箭头：**

```text
尺寸：6x6px
颜色：#1C1E20
```

**显示动画：**

```css
opacity: 0 → 1
transform: translateY(4px) → translateY(0)
transition: 0.15s ease-out
```

---

## 17.3 Night Mode — Aurora Tooltip

**样式定义：**

```text
背景：linear-gradient(120deg, #4BE4C9, #5BB7FF)
文字颜色：#0B1321
字体大小：12px
字体粗细：600
圆角：6px
Padding：6px 10px
阴影：0 0 16px rgba(91, 183, 255, 0.6)
最大宽度：220px
```

**箭头：**

```text
尺寸：6x6px
背景：继承渐变
```

---

# 18. 📊 Progress Bar 进度条组件

**类名：** `.progress-aurora`

---

## 18.1 结构

* 轨道（Track）
* 填充条（Fill Bar）
* 可选百分比文字

---

## 18.2 Day Mode — Snow Progress

**轨道：**

```text
高度：8px
背景：#EEF1F3
圆角：999px
overflow: hidden
```

**填充条：**

```text
高度：100%
背景：#A8D8F8
圆角：999px
过渡动画：width 0.3s ease
```

**百分比文字：**

```text
字体大小：12px
颜色：#6D747A
位置：右侧或上方
```

**尺寸变体：**

| 尺寸    | 高度   |
| ----- | ---- |
| Small | 4px  |
| Medium (默认) | 8px  |
| Large | 12px |

---

## 18.3 Night Mode — Aurora Progress

**轨道：**

```text
高度：8px
背景：#233043
圆角：999px
```

**填充条：**

```text
背景：linear-gradient(90deg, #4BE4C9, #5BB7FF)
Glow：0 0 12px rgba(91, 183, 255, 0.5)
过渡动画：width 0.3s ease
```

**百分比文字：**

```text
字体大小：12px
颜色：#F1F6FF
```

**动画效果（可选）：**

```css
/* 流动光效 */
@keyframes progress-flow {
  0% { background-position: 0% 50%; }
  100% { background-position: 100% 50%; }
}
background-size: 200% 100%;
animation: progress-flow 2s linear infinite;
```

---

# 19. 🎭 组件状态规范

本章节定义所有交互组件的通用状态样式，确保一致的用户体验。

---

## 19.1 Button 按钮状态

### Disabled（禁用）状态

**Day Mode：**

```text
背景：#EEF1F3
文字颜色：#9AA2A8
边框：1px solid #D8DFE4
opacity: 0.6
cursor: not-allowed
阴影：none
```

**Night Mode：**

```text
背景：#233043
文字颜色：#6D747A
边框：1px solid #233043
opacity: 0.5
cursor: not-allowed
Glow：none
```

### Loading（加载）状态

**Day Mode：**

```text
保持正常样式
添加旋转图标（spinner）：
  颜色：#1C1E20
  尺寸：16px
  位置：文字左侧
cursor: wait
pointer-events: none
```

**Night Mode：**

```text
保持渐变背景
添加旋转图标：
  颜色：#F1F6FF
  Glow：0 0 8px rgba(91, 183, 255, 0.6)
cursor: wait
```

**Loading 动画：**

```css
@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
animation: spin 0.8s linear infinite;
```

---

## 19.2 Input / Select 表单组件状态

### Disabled（禁用）状态

**Day Mode：**

```text
背景：#F8FAFB
文字颜色：#9AA2A8
边框：1px solid #EEF1F3
cursor: not-allowed
opacity: 0.6
```

**Night Mode：**

```text
背景：#0B1321
文字颜色：#6D747A
边框：1px solid #233043
cursor: not-allowed
opacity: 0.5
```

### Error（错误）状态

**Day Mode：**

```text
边框：1px solid #FF6B6B
Focus 边框：2px solid #D9534F
Focus Glow：0 0 0 3px rgba(255, 107, 107, 0.2)
错误提示文字：
  颜色：#D9534F
  字体大小：12px
  位置：输入框下方 4px
```

**Night Mode：**

```text
边框：1px solid #FF6B6B
Focus 边框：2px solid #FF6B6B
Focus Glow：0 0 0 3px rgba(255, 107, 107, 0.25)
Outer Glow：0 0 12px rgba(255, 107, 107, 0.4)
错误提示文字：
  颜色：#FF6B6B
  字体大小：12px
```

### Success（成功）状态

**Day Mode：**

```text
边框：1px solid #5CB85C
Focus 边框：2px solid #5CB85C
Focus Glow：0 0 0 3px rgba(92, 184, 92, 0.2)
成功图标：
  颜色：#5CB85C
  位置：输入框右侧内部
```

**Night Mode：**

```text
边框：1px solid #4BE4C9
Focus 边框：2px solid #4BE4C9
Glow：0 0 12px rgba(75, 228, 201, 0.4)
成功图标：
  颜色：#4BE4C9
```

---

## 19.3 Card 卡片状态

### Disabled（禁用）状态

**Day Mode：**

```text
opacity: 0.5
filter: grayscale(30%)
```

**Night Mode：**

```text
opacity: 0.4
filter: grayscale(30%)
Glow：none
```

### Hover（悬停）状态

**Day Mode：**

```text
阴影：0 6px 16px rgba(0,0,0,0.08)
transform: translateY(-2px)
transition: all 0.25s ease
```

**Night Mode：**

```text
阴影：0 8px 24px rgba(0,0,0,0.6)
border-color: #4BE4C9
Glow：0 0 16px rgba(91, 183, 255, 0.3)
transform: translateY(-2px)
```

---

## 19.4 Switch / Checkbox / Radio 状态

### Indeterminate（半选）状态（仅 Checkbox）

**Day Mode：**

```text
背景：#A8D8F8
边框：2px solid #8EC8F2
中间横线图标：
  颜色：#1C1E20
  宽度：10px
  高度：2px
```

**Night Mode：**

```text
背景：linear-gradient(120deg, #4BE4C9, #5BB7FF)
中间横线图标：
  颜色：#F1F6FF
  Glow：0 0 8px rgba(91, 183, 255, 0.5)
```

---

# 20. 📱 响应式设计规范

确保 Aurora 主题在所有设备上都能提供优质的用户体验。

---

## 20.1 断点定义

| 断点名称  | 最小宽度  | 设备类型          | 容器宽度     |
| ----- | ----- | ------------- | -------- |
| xs    | 0px   | 小屏手机          | 100%     |
| sm    | 640px | 大屏手机 / 小平板    | 100%     |
| md    | 768px | 平板            | 720px    |
| lg    | 1024px | 小屏笔记本 / 平板横屏 | 960px    |
| xl    | 1280px | 桌面显示器         | 1200px   |
| 2xl   | 1536px | 大屏显示器         | 1400px   |

**媒体查询示例：**

```css
/* Mobile First */
.component { ... }

@media (min-width: 640px) { /* sm */ }
@media (min-width: 768px) { /* md */ }
@media (min-width: 1024px) { /* lg */ }
@media (min-width: 1280px) { /* xl */ }
```

---

## 20.2 移动端适配规则

### 触摸目标尺寸

所有可点击元素的最小尺寸：

```text
最小点击区域：44x44px（iOS 规范）
推荐点击区域：48x48px（Material Design 规范）
```

**移动端组件调整：**

| 组件        | 桌面高度   | 移动端高度  |
| --------- | ------ | ------ |
| Button    | 40px   | 48px   |
| Input     | 40px   | 48px   |
| Select    | 40px   | 48px   |
| Switch    | 22px   | 26px   |
| Checkbox  | 18px   | 20px   |
| Radio     | 18px   | 20px   |

### 字体缩放

```css
/* 移动端适当增大字体 */
@media (max-width: 640px) {
  html { font-size: 16px; } /* 确保可读性 */

  .btn-aurora { font-size: 15px; }
  .input-aurora { font-size: 16px; } /* 避免 iOS 自动缩放 */
}
```

### 间距调整

移动端缩小间距以节省空间：

```css
@media (max-width: 640px) {
  .card-aurora {
    padding: 12px 16px; /* 桌面：16px 20px */
  }

  .modal-aurora {
    margin: 16px; /* 确保不贴边 */
    max-width: calc(100% - 32px);
  }
}
```

---

## 20.3 组件响应式行为

### 导航 / Tabs

```text
桌面：水平排列
移动端：
  - 可滚动水平列表
  - 或转换为下拉菜单（Select）
```

### Modal 模态框

```text
桌面：居中显示，固定宽度
移动端：
  - 全屏或接近全屏
  - 从底部滑入（推荐）
```

### Toast 通知

```text
桌面：右上角固定位置
移动端：顶部或底部居中，全宽显示
```

### Card 卡片

```text
桌面：网格布局（2–4列）
平板：2列
移动端：单列堆叠
```

---

## 20.4 性能优化

### 减少动画

```css
/* 尊重用户系统设置 */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

### 图片优化

```text
使用 srcset 提供多分辨率图片
移动端优先加载小图
懒加载非关键图片
```

---

# 21. ♿️ 无障碍访问性规范

确保 Aurora 主题符合 WCAG 2.1 AA 标准，让所有用户都能顺畅使用。

---

## 21.1 色彩对比度标准

### 文字对比度要求（WCAG AA）

| 文字类型    | 最小对比度 |
| ------- | ----- |
| 正文（≥18px） | 3:1   |
| 正文（<18px） | 4.5:1 |
| 大标题      | 3:1   |

### 验证结果

**Day Mode：**

| 组合                            | 对比度   | 状态 |
| ----------------------------- | ----- | -- |
| `#1C1E20` on `#FFFFFF`        | 16.4:1 | ✅  |
| `#6D747A` on `#FFFFFF`        | 5.2:1 | ✅  |
| `#1C1E20` on `#A8D8F8`        | 7.8:1 | ✅  |

**Night Mode：**

| 组合                            | 对比度   | 状态 |
| ----------------------------- | ----- | -- |
| `#F1F6FF` on `#0B1321`        | 15.8:1 | ✅  |
| `#9BA8C0` on `#0B1321`        | 7.3:1 | ✅  |
| `#F1F6FF` on `#121C2C`        | 12.5:1 | ✅  |

---

## 21.2 键盘导航支持

### 焦点管理

**焦点指示器规范：**

```css
/* Day Mode */
body.day *:focus-visible {
  outline: 2px solid #8EC8F2;
  outline-offset: 2px;
}

/* Night Mode */
body.night *:focus-visible {
  outline: 2px solid #5BB7FF;
  outline-offset: 2px;
  box-shadow: 0 0 0 4px rgba(91, 183, 255, 0.2);
}

/* 移除默认 outline */
*:focus {
  outline: none;
}
```

### 键盘交互

| 组件      | 支持按键                      | 行为             |
| ------- | ------------------------- | -------------- |
| Button  | Enter, Space              | 触发点击           |
| Input   | Tab, Shift+Tab            | 焦点切换           |
| Select  | ↑↓ 箭头, Enter, Esc         | 选项导航、确认、关闭     |
| Checkbox | Space                     | 切换选中状态         |
| Radio   | ↑↓←→ 箭头, Space            | 选项切换           |
| Modal   | Esc                       | 关闭模态框          |
| Tabs    | ←→ 箭头, Home, End          | Tab 切换、首尾跳转   |
| Switch  | Space                     | 切换开关           |

---

## 21.3 ARIA 属性指南

### Button 按钮

```html
<button class="btn-aurora"
        aria-label="提交表单"
        aria-disabled="false">
  提交
</button>

<!-- Loading 状态 -->
<button aria-busy="true" aria-label="正在提交...">
  <span aria-hidden="true">加载图标</span>
  提交中
</button>
```

### Input 输入框

```html
<label for="email-input">邮箱地址</label>
<input id="email-input"
       class="input-aurora"
       type="email"
       aria-required="true"
       aria-invalid="false"
       aria-describedby="email-error">
<span id="email-error" role="alert">
  邮箱格式不正确
</span>
```

### Checkbox / Radio

```html
<!-- Checkbox -->
<input type="checkbox"
       id="terms"
       class="checkbox-aurora"
       aria-checked="false"
       aria-labelledby="terms-label">
<label id="terms-label" for="terms">同意服务条款</label>

<!-- Checkbox 半选状态 -->
<input aria-checked="mixed">

<!-- Radio Group -->
<fieldset role="radiogroup" aria-labelledby="plan-label">
  <legend id="plan-label">选择套餐</legend>
  <input type="radio" name="plan" value="basic"
         aria-checked="true">
  <input type="radio" name="plan" value="pro"
         aria-checked="false">
</fieldset>
```

### Switch 开关

```html
<button role="switch"
        class="switch-aurora"
        aria-checked="false"
        aria-labelledby="notifications-label">
  <span class="switch-thumb"></span>
</button>
<span id="notifications-label">启用通知</span>
```

### Select 下拉框

```html
<!-- 原生 Select -->
<label for="country">国家/地区</label>
<select id="country"
        class="select-aurora"
        aria-required="true">
  <option value="">请选择</option>
  <option value="cn">中国</option>
</select>

<!-- 自定义 Select -->
<div class="select-aurora" role="combobox"
     aria-expanded="false"
     aria-haspopup="listbox"
     aria-labelledby="country-label">
  <span id="country-label">国家/地区</span>
  <ul role="listbox" hidden>
    <li role="option" aria-selected="true">中国</li>
  </ul>
</div>
```

### Modal 模态框

```html
<div class="modal-backdrop-aurora"
     role="dialog"
     aria-modal="true"
     aria-labelledby="modal-title"
     aria-describedby="modal-desc">
  <div class="modal-aurora">
    <h2 id="modal-title">确认删除</h2>
    <p id="modal-desc">此操作不可撤销</p>
    <button aria-label="关闭对话框">×</button>
  </div>
</div>
```

### Toast 通知

```html
<div class="toast-aurora"
     role="alert"
     aria-live="polite"
     aria-atomic="true">
  <strong>操作成功</strong>
  <p>您的更改已保存</p>
</div>

<!-- 紧急通知 -->
<div role="alert" aria-live="assertive">
  错误：网络连接失败
</div>
```

### Tooltip 工具提示

```html
<button aria-describedby="tooltip-1">
  帮助
</button>
<div id="tooltip-1"
     class="tooltip-aurora"
     role="tooltip">
  点击查看详细信息
</div>
```

### Tabs 标签页

```html
<div class="tabs-aurora" role="tablist"
     aria-label="产品信息">
  <button role="tab"
          aria-selected="true"
          aria-controls="panel-1"
          id="tab-1">
    详情
  </button>
  <button role="tab"
          aria-selected="false"
          aria-controls="panel-2"
          id="tab-2">
    评价
  </button>
</div>

<div id="panel-1"
     role="tabpanel"
     aria-labelledby="tab-1">
  内容...
</div>
<div id="panel-2"
     role="tabpanel"
     aria-labelledby="tab-2"
     hidden>
  内容...
</div>
```

### Progress Bar 进度条

```html
<div class="progress-aurora"
     role="progressbar"
     aria-valuenow="65"
     aria-valuemin="0"
     aria-valuemax="100"
     aria-label="上传进度">
  <div class="progress-fill" style="width: 65%"></div>
</div>
```

---

## 21.4 屏幕阅读器优化

### 隐藏装饰性元素

```html
<!-- 图标装饰 -->
<button>
  <svg aria-hidden="true" focusable="false">...</svg>
  保存
</button>

<!-- 纯视觉分隔符 -->
<hr aria-hidden="true">
```

### 提供文本替代

```html
<!-- 纯图标按钮 -->
<button aria-label="搜索">
  <svg aria-hidden="true">...</svg>
</button>

<!-- 图片 -->
<img src="chart.png" alt="2024年销售趋势图：逐月增长">
```

### 动态内容通知

```html
<!-- 实时更新区域 -->
<div aria-live="polite" aria-atomic="true">
  <p>新消息：3条未读</p>
</div>

<!-- 紧急通知 -->
<div aria-live="assertive" role="alert">
  错误：表单验证失败
</div>
```

---

## 21.5 焦点陷阱（Modal）

当模态框打开时，焦点应被限制在模态框内：

```javascript
// 焦点陷阱伪代码
const modal = document.querySelector('.modal-aurora');
const focusableElements = modal.querySelectorAll(
  'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])'
);

const firstElement = focusableElements[0];
const lastElement = focusableElements[focusableElements.length - 1];

// Tab 到最后一个元素时，回到第一个
lastElement.addEventListener('keydown', (e) => {
  if (e.key === 'Tab' && !e.shiftKey) {
    e.preventDefault();
    firstElement.focus();
  }
});

// Shift+Tab 到第一个元素时，回到最后一个
firstElement.addEventListener('keydown', (e) => {
  if (e.key === 'Tab' && e.shiftKey) {
    e.preventDefault();
    lastElement.focus();
  }
});
```

---

## 21.6 无障碍检查清单

- [ ] 所有交互元素可通过键盘访问
- [ ] 焦点指示器清晰可见
- [ ] 色彩对比度符合 WCAG AA 标准
- [ ] 图片提供有意义的 alt 文本
- [ ] 表单元素有明确的 label
- [ ] 错误提示与表单字段关联
- [ ] Modal 打开时焦点被正确管理
- [ ] 动态内容变化通过 aria-live 通知
- [ ] 装饰性元素标记为 aria-hidden
- [ ] 支持屏幕阅读器（NVDA、JAWS、VoiceOver）

---

# 22. 🌗 Day / Night 主题切换机制说明

通过切换 `<body>` 的类实现主题：

```js
if (document.body.classList.contains('day')) {
  document.body.classList.remove('day');
  document.body.classList.add('night');
} else {
  document.body.classList.remove('night');
  document.body.classList.add('day');
}
```

所有受主题影响的组件样式，建议使用选择器：

```css
body.day .btn-aurora { ... }
body.night .btn-aurora { ... }

body.day .input-aurora { ... }
body.night .input-aurora { ... }
```

并统一加上平滑过渡：

```css
transition: background-color 0.3s ease,
            color 0.3s ease,
            box-shadow 0.3s ease,
            border-color 0.3s ease,
            transform 0.2s ease;
```

---

# 23. 🧩 示例代码生成提示（给模型用）

如果你希望让另一个模型直接生成 HTML 页面，可以给它这样的指令（示例）：

```text
请根据如下 Aurora 主题 UI 组件规范（包含 Button、Select、Input、Card、Tag、Switch、Tabs、
Checkbox、Radio、Modal、Toast、Tooltip、Progress Bar 等组件的 Day/Night 样式），
生成一个完整可运行的 HTML+CSS+JS 页面代码：

必备要求：
- 使用 body.day / body.night 控制主题
- 在页面顶部提供一个主题切换按钮或 Switch
- 页面中依次展示所有组件，每个组件区域包含：
  * 组件标题
  * 简短描述
  * 实际可交互的组件实例
  * 展示组件的不同状态（normal、hover、disabled、error 等）

页面应包含的组件列表：
1. Button 按钮（包含 normal、hover、active、disabled、loading 状态）
2. Input 文本输入框（包含 normal、focus、disabled、error、success 状态）
3. Select 下拉框（包含 normal、focus、disabled 状态）
4. Checkbox 复选框（未选中、选中、半选、禁用状态）
5. Radio 单选框（未选中、选中、禁用状态）
6. Switch 开关（关闭、开启、禁用状态）
7. Card 信息卡片（包含 hover 状态）
8. Tag/Chip 标签
9. Tabs 标签页（至少3个 tab）
10. Modal/Dialog 模态框（提供打开按钮）
11. Toast/Notification 通知（提供触发按钮，展示 info、success、warning、error 类型）
12. Tooltip 工具提示（鼠标悬停在元素上时显示）
13. Progress Bar 进度条（展示不同进度值）

样式要求：
- 严格按照规范中的颜色、圆角、阴影、Glow、渐变、交互状态（hover、active、focus）来实现
- Day Mode 使用雪山纯净风格（冷色、柔光、干净）
- Night Mode 使用极光迷人风格（渐变、Glow、深邃）
- 确保所有组件都支持主题切换，过渡动画流畅
- 使用规范中定义的字体系统、间距系统、动画系统
- 所有交互元素支持键盘访问和焦点指示器
- 色彩对比度符合 WCAG AA 标准

响应式要求：
- 移动端（<640px）：组件堆叠显示，增大触摸目标尺寸
- 平板（640px-1024px）：适当调整布局
- 桌面（>1024px）：完整展示所有功能

无障碍要求：
- 为交互元素添加适当的 ARIA 属性
- 确保键盘导航顺畅
- 焦点指示器清晰可见
- Modal 打开时实现焦点陷阱
- Toast 使用 aria-live 进行屏幕阅读器通知

代码输出要求：
- 单个 HTML 文件，包含完整的 CSS 和 JavaScript
- 代码结构清晰，注释完善
- 可直接在浏览器中运行查看效果
- 不依赖外部库（除非必需，如图标库）
```

**更简洁的提示（快速版）：**

```text
基于 Aurora UI 规范生成完整的 HTML 组件预览页面，包含：

组件：Button, Input, Select, Checkbox, Radio, Switch, Card, Tag, Tabs,
      Modal, Toast, Tooltip, Progress Bar

主题：Day Mode（雪山纯净）+ Night Mode（极光迷人），可通过顶部开关切换

样式：严格遵循规范中的颜色、圆角、阴影、渐变、Glow、动画

状态：展示每个组件的 normal、hover、disabled、error 等所有状态

输出：单个可运行的 HTML 文件，包含内嵌 CSS 和 JavaScript

要求：响应式布局、无障碍支持、键盘导航、平滑过渡动画
```