# LPKRender (LPKR)

> 🔓 LPK 解密 + 🎨 Web 渲染，极简的 Live2D 模型渲染器

[English](#english) | [中文](#中文)

---

## 中文

### 核心功能

| 功能 | 说明 |
|------|------|
| **🔓 LPK 解密** | 支持 STD2_0 和 STM_1_0 格式，自动解密加密的 LPK 模型文件 |
| **🎨 Web 渲染** | 基于 PixiJS + Live2D SDK，在浏览器中流畅渲染 |
| **📦 Steam Workshop** | 支持 Steam Workshop 的 LPKR 格式模型 |

### 快速开始

```html
<script src="https://cdn.jsdelivr.net/gh/cheezhi/LPKRender/lpkr.min.js"></script>
<script>
  LPKRender.init({
    lpkFile: '/model.lpk'  // 支持加密/未加密的 LPK 文件
  });
</script>
```

### 配置选项

```javascript
LPKRender.init({
  // ========== LPK 解密 ==========
  lpkFile: '/model.lpk',        // LPK 文件路径（必需）
  configFile: '/config.json',   // Steam Workshop 类型需要此配置文件

  // ========== Web 渲染 ==========
  width: 300,                   // 画布宽度（像素）
  height: 400,                  // 画布高度（像素）
  position: 'right',            // 位置：'left' 或 'right'
  bottom: 0,                    // 距离底部距离（像素）
  right: 0,                     // 距离右侧距离（像素，position为right时有效）
  left: 'auto',                 // 距离左侧距离（像素，position为left时有效）
  scale: 0.15,                  // 模型缩放比例（默认统一使用）
  // 模型在画布中的位置（0-1，0.5为居中）
  modelX: 0.5,                  // 水平位置
  modelY: 0.5,                  // 垂直位置
  modelYOffset: 50,             // 垂直偏移量（像素，正值向下）
  // 移动端专属配置（可选，设置后启用响应式）
  mobileScale: null,            // 移动端缩放比例（如 0.1）
  mobileWidth: null,            // 移动端画布宽度（如 250）
  mobileHeight: null,           // 移动端画布高度（如 350）
  mobilePosition: null,         // 移动端位置（如 'left'）
  mobileBottom: null,           // 移动端距离底部距离（如 20）
  mobileModelX: null,           // 移动端模型水平位置
  mobileModelY: null,           // 移动端模型垂直位置
  mobileModelYOffset: null      // 移动端模型垂直偏移

  // ========== 交互控制 ==========
  draggable: true,              // 是否可用鼠标/手指拖拽
  clickable: true,              // 是否启用点击交互
  tapMotion: true,              // 点击时是否播放动作
  randomMotion: false,          // 是否忽略 hit 区域，随机播放动作

  // ========== 音效控制 ==========
  soundEnabled: false,          // 是否播放动作音效（默认关闭）

  // ========== 动作控制 ==========
  idleMotion: null,             // 初始循环播放的动作组名称，如 '恢复'
  excludeMotions: [],           // 要删除的动作组名称列表，如 ['Idle']
  hitAreaMapping: {             // 点击区域到动作组的映射
    '头': '打招呼',
    '左手': '书'
  },

  // ========== 自定义 CDN ==========
  libUrls: {                    // 自定义第三方库 URL（可选）
    // cubismCore: 'https://your-cdn.com/cubismcore.min.js',
    // live2d: 'https://your-cdn.com/live2d.min.js',
    // pixi: 'https://your-cdn.com/pixi.min.js',
    // pixiLive2d: 'https://your-cdn.com/pixi-live2d-display.min.js',
    // jszip: 'https://your-cdn.com/jszip.min.js'
  }
});
```

### 参数详解

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| **LPK 解密** ||||
| `lpkFile` | `string` | `'/model.lpk'` | **必需** LPK 模型文件路径 |
| `configFile` | `string` | `null` | Steam Workshop 类型的 LPK 需要额外的 config.json 文件 |
| **Web 渲染** ||||
| `width` | `number` | `300` | 画布宽度（像素） |
| `height` | `number` | `400` | 画布高度（像素） |
| `position` | `string` | `'right'` | 位置：`'left'` 或 `'right'` |
| `bottom` | `number` | `0` | 距离页面底部距离（像素） |
| `right` | `number` | `0` | 距离右侧像素（position为right时有效） |
| `left` | `string` | `'auto'` | 距离左侧像素（position为left时有效） |
| `scale` | `number` | `0.15` | 模型缩放比例（默认统一使用） |
| `mobileScale` | `number` | `null` | 移动端缩放比例（设置后启用响应式） |
| `mobileWidth` | `number` | `null` | 移动端画布宽度（设置后启用响应式） |
| `mobileHeight` | `number` | `null` | 移动端画布高度（设置后启用响应式） |
| `mobilePosition` | `string` | `null` | 移动端位置：`'left'` 或 `'right'`（设置后启用响应式） |
| `mobileBottom` | `number` | `null` | 移动端距离底部距离（设置后启用响应式） |
| `modelX` | `number` | `0.5` | 模型在画布中的水平位置（0-1，0.5 为居中） |
| `modelY` | `number` | `0.5` | 模型在画布中的垂直位置（0-1，0.5 为居中） |
| `modelYOffset` | `number` | `50` | 模型垂直偏移量（像素，正值向下） |
| `mobileModelX` | `number` | `null` | 移动端模型水平位置（设置后启用响应式） |
| `mobileModelY` | `number` | `null` | 移动端模型垂直位置（设置后启用响应式） |
| `mobileModelYOffset` | `number` | `null` | 移动端模型垂直偏移（设置后启用响应式） |
| **交互控制** ||||
| `draggable` | `boolean` | `true` | 是否可以用鼠标/手指拖拽 |
| `clickable` | `boolean` | `true` | 是否启用点击交互 |
| `tapMotion` | `boolean` | `true` | 点击时是否播放动作 |
| `randomMotion` | `boolean` | `false` | 是否忽略 hit 区域随机播放动作 |
| **音效控制** ||||
| `soundEnabled` | `boolean` | `false` | 是否播放动作音效 |
| **动作控制** ||||
| `idleMotion` | `string` | `null` | 初始循环播放的动作组名称 |
| `excludeMotions` | `array` | `[]` | 要删除的动作组名称列表 |
| `hitAreaMapping` | `object` | `null` | 点击区域到动作组的映射 |
| **自定义 CDN** ||||
| `libUrls` | `object` | `{}` | 自定义第三方 JS 库的 URL |

### libUrls 配置项

| 属性 | 说明 | 默认 URL |
|------|------|----------|
| `cubismCore` | Live2D Cubism Core | `https://cubism.live2d.com/sdk-web/cubismcore/live2dcubismcore.min.js` |
| `live2d` | Live2D Framework | `https://cdn.jsdelivr.net/gh/dylanNew/live2d/webgl/Live2D/lib/live2d.min.js` |
| `pixi` | PixiJS | `https://cdn.jsdelivr.net/npm/pixi.js@7.3.2/dist/pixi.min.js` |
| `pixiLive2d` | Pixi Live2D Display | `https://cdn.jsdelivr.net/npm/pixi-live2d-display@0.4.0/dist/index.min.js` |
| `jszip` | JSZip | `https://cdn.jsdelivr.net/npm/jszip@3.10.1/dist/jszip.min.js` |

---

## English

### Core Features

| Feature | Description |
|---------|-------------|
| **🔓 LPK Decryption** | Supports STD2_0 & STM_1_0 formats, auto-decrypt encrypted LPK files |
| **🎨 Web Rendering** | Based on PixiJS + Live2D SDK, smooth rendering in browser |
| **📦 Steam Workshop** | Supports Steam Workshop LPKR format models |

### Quick Start

```html
<script src="lpkrender.min.js"></script>
<script>
  LPKRender.init({
    lpkFile: '/model.lpk'  // Supports encrypted/unencrypted LPK
  });
</script>
```

---

## 📄 License
本项目采用 **MIT License + 非商用附加条款** 开源（完整文本见 [LICENSE](LICENSE) 文件）：
- ✅ 允许：个人学习、研究、修改、开源分享衍生版本（需保留相同约束）；
- ❌ 禁止：商用、制作Live2DViewerEX竞品牟利、滥用LPK解密功能侵权；
- 📝 免责：开发者不对滥用本项目导致的法律纠纷承担责任。
© 2026 LPKRender
