# SAR 合成孔径雷达覆盖模拟

这是一个使用 Three.js 实现的 SAR (Synthetic Aperture Radar) 覆盖可视化工具，类似于 STK (Satellite Tool Kit) 的 SAR 功能。

## 功能特性

### 1. Track Parent Altitude (跟踪父对象高度)
- **启用时**: SAR 传感器会跟踪卫星的实时高度，随卫星轨道高度变化而变化
- **禁用时**: SAR 传感器使用固定高度，不随卫星高度变化

### 2. 可调节参数
- **SAR 覆盖角度 (Grazing Angle)**: 20° - 70°
  - 控制 SAR 扫描的角度范围
- **覆盖宽度 (Swath Width)**: 0.5 - 3.0
  - 控制 SAR 覆盖区域的宽度
- **固定高度 (Fixed Altitude)**: 1.5 - 4.0
  - 仅在未跟踪父对象高度时有效
- **覆盖透明度 (Opacity)**: 0.1 - 0.8
  - 调整 SAR 覆盖区域的透明度

### 3. 实时信息显示
- 卫星当前高度
- SAR 传感器当前高度
- 当前工作模式（跟踪模式/固定高度模式）

## 技术实现

### Three.js 组件
1. **地球模型**: 使用 `SphereGeometry` 创建，包含极坐标网格
2. **卫星模型**: 包含主体和太阳能板
3. **SAR 覆盖区域**: 使用自定义几何体创建侧视雷达扫描区域
4. **轨道可视化**: 显示卫星运行轨道

### Shader 实现
- 使用自定义 `ShaderMaterial` 实现 SAR 覆盖区域的渲染
- 实现地球遮挡检测，只显示可见的覆盖区域
- 地球表面交点高亮显示
- 菲涅尔效果增强边缘可见性

### 动画系统
- 卫星沿椭圆轨道运动，模拟真实的高度变化
- 实时更新 SAR 覆盖几何体
- 平滑的相机控制（OrbitControls）

## 使用方法

1. 打开 `sar.html` 文件
2. 使用鼠标拖拽旋转视角，滚轮缩放
3. 通过左侧控制面板调整参数：
   - 勾选/取消勾选 "Track Parent Altitude" 切换模式
   - 拖动滑块调整各项参数
4. 观察左下角实时信息面板查看当前状态

## 文件说明

- `sar.html`: 主要的 SAR 可视化文件
- `tt.html`: 原有的锥体裁剪示例文件

## 浏览器兼容性

需要支持以下特性的现代浏览器：
- WebGL 2.0
- ES6 Modules
- Import Maps

推荐使用：
- Chrome 89+
- Firefox 108+
- Edge 89+
- Safari 16.4+

## 参考

本实现参考了 STK (Satellite Tool Kit) 的 SAR 传感器模拟功能，使用 Three.js 在 Web 环境中实现类似的可视化效果。
