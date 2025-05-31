# 样式自定义指南

## 主要样式文件位置
所有自定义样式都在 `assets/css/custom.css` 文件中

## 如何调整样式

### 1. 调整内容区域上边距
```css
.microblog-container {
  padding-top: 2rem; /* 调整内容区域与顶部导航的距离 */
}
```

### 2. 调整微博之间的间距
在 `assets/css/custom.css` 中找到 `.microblog-post` 类：
```css
.microblog-post {
  /* 调整间距 - 修改这个值来控制每个微博之间的距离 */
  margin-bottom: 1.5rem; /* 当前是 1.5rem，可以改为 1rem, 2rem, 3rem 等 */
}
```

### 3. 调整虚线边框样式
```css
.microblog-post {
  /* 虚线边框 - 可以修改颜色、粗细、样式 */
  border: 1px dashed #d1d5db; /* 1px 是粗细，dashed 是虚线，#d1d5db 是颜色 */
  
  /* 其他边框样式选项：
     border: 2px dotted #94a3b8;  // 点线
     border: 1px solid #e5e7eb;   // 实线
     border: 3px dashed #3b82f6;  // 更粗的蓝色虚线
  */
}
```

### 4. 调整内边距（内容与边框的距离）
```css
.microblog-post {
  padding: 1.5rem; /* 可以改为 1rem, 2rem, 2.5rem 等 */
}
```

### 5. 调整圆角
```css
.microblog-post {
  border-radius: 0.5rem; /* 0 表示直角，数值越大越圆 */
}
```

### 6. 调整日期和标签的位置
```css
.microblog-post .post-meta {
  margin-top: 1.5rem; /* 调整与内容的间距 */
  padding-top: 1rem; /* 调整内边距 */
  border-top: 1px dashed #e5e7eb; /* 分隔线样式，可以删除这行去掉分隔线 */
}
```

### 7. 调整暗色模式下的样式
```css
/* 虚线边框颜色 */
.dark .microblog-post {
  border-color: #4b5563;
}

/* 日期分隔线颜色 */
.dark .microblog-post .post-meta {
  border-top-color: #374151;
}
```

### 8. 显示模式切换按钮
显示模式切换按钮已通过 JavaScript 自动添加到顶部导航栏。样式定义在 `layouts/partials/extend-head.html` 中：
```css
.appearance-toggle {
  width: 2.5rem;
  height: 2.5rem;
  /* 可以调整按钮大小 */
}
```

## 常用的间距单位

- `0.5rem` = 8px
- `1rem` = 16px
- `1.5rem` = 24px
- `2rem` = 32px
- `2.5rem` = 40px
- `3rem` = 48px

## 颜色建议

亮色模式虚线边框：
- `#e5e7eb` - 很浅的灰色
- `#d1d5db` - 浅灰色（当前使用）
- `#9ca3af` - 中灰色
- `#6b7280` - 深灰色

暗色模式虚线边框：
- `#374151` - 深灰色
- `#4b5563` - 中深灰色（当前使用）
- `#6b7280` - 中灰色
- `#9ca3af` - 浅灰色

## 调试技巧

1. 修改 CSS 文件后，浏览器会自动刷新看到效果
2. 使用浏览器的开发者工具（F12）可以实时调试样式
3. 在开发者工具中可以临时修改样式值，满意后再写入文件
4. 如果样式没有生效，可以尝试清除浏览器缓存或重启 Hugo 服务器 