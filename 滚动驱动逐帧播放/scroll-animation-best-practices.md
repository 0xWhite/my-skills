我需要将一个 MP4 动画集成到网页中，实现滚动驱动的逐帧播放效果（类似 Apple 官网产品页）。

请帮我完成以下两件事：

---

## 一、FFmpeg 提取帧命令

根据我的 MP4 文件，给出最优的 FFmpeg 提取命令，将视频切成 WebP 图片序列。

要求：
- 帧率建议：24fps（可根据视频时长调整，最终帧数控制在 120~200 帧之间）
- 输出分辨率：桌面端 1920px 宽，如需移动端适配请额外给出 960px 宽的命令
- 输出格式：WebP，quality 75~80
- 输出路径：frames/frame-%04d.webp
- 如视频较长，请给出裁剪命令

### 正确的 FFmpeg 命令模板

```bash
# 创建输出目录
mkdir -p frames

# 提取帧（桌面端 1920px）
ffmpeg -i your-video.mp4 \
  -vf "fps=24,scale=1920:-1" \
  -c:v libwebp \
  -quality 80 \
  frames/frame-%04d.webp \
  -y

# 移动端适配（960px）
ffmpeg -i your-video.mp4 \
  -vf "fps=24,scale=960:-1" \
  -c:v libwebp \
  -quality 80 \
  frames-mobile/frame-%04d.webp \
  -y
```

**关键参数说明：**
- `-c:v libwebp`：指定 WebP 编码器，默认为动画 WebP（只输出 1 帧），必须显式指定
- `-quality 80`：质量 75~80 区间
- `scale=1920:-1`：宽度 1920px，高度按比例自动计算

---

## 二、完整的网页集成代码

请输出一个可直接使用的单文件 HTML（所有 CSS 和 JS 内联），实现以下功能：

### 核心功能
- 使用 `position: sticky` 固定 Canvas，滚动区域高度为 `500vh`（可调整）
- 预加载所有 WebP 帧，显示加载进度条（百分比 + 进度条动画）
- 加载完成后，根据滚动进度（0~1）映射到帧索引，在 Canvas 上逐帧绘制
- 使用 `requestAnimationFrame` + 脏检查（lastFrame 对比）优化渲染性能
- Canvas 尺寸自适应窗口，保持视频原始宽高比，居中显示

### 代码结构要求
```javascript
// 关键变量需可配置，统一放在文件顶部：
const CONFIG = {
  totalFrames: 150,       // 总帧数（根据 FFmpeg 提取结果填写）
  frameDir: 'frames/',    // 帧图片目录
  frameName: 'frame-',    // 文件名前缀
  frameExt: '.webp',      // 文件扩展名
  scrollHeight: '500vh',  // 滚动区域高度
  videoWidth: 1920,       // 视频原始宽度
  videoHeight: 1080,      // 视频原始高度
};
```

### 集成方式
- 代码中保留清晰注释，标明哪里需要替换为我的实际参数
- 在 Canvas 区域上下预留内容插槽（注释标记），方便我添加文字、标题等覆盖层
- 滚动进度（0~1）暴露为全局变量 `window.scrollProgress`，方便我在其他地方联动使用

### 性能要求
- 图片预加载使用并发加载（Promise.all），不要串行
- 帧索引变化时才调用 `ctx.drawImage`，避免无效绘制
- Canvas 使用 `will-change: transform` 提示 GPU 加速

---

## 我的网站信息

[在此描述你的网站风格和需求，例如：
- 网站整体风格：深色/浅色、科技感/自然风/商务风
- Canvas 区域的背景色
- 是否需要在视频上方叠加文字或 UI 元素
- 是否需要移动端适配
- 是否需要与页面其他部分（如导航栏）协调样式]

---

请先输出 FFmpeg 命令，然后输出完整 HTML 代码。代码中的 `CONFIG.totalFrames` 请根据 FFmpeg 命令的预期帧数填写一个合理的默认值，并在注释中说明如何根据实际提取结果调整。