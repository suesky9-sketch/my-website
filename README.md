# 竞品包装分析数据平台

这是一个可直接分享和部署的静态 HTML 数据可视化网站，核心页面由 `index.html`、`styles.css`、`app.js` 和 `data.js` 组成。

## 本地预览

```powershell
python -m http.server 5173
```

打开：

```text
http://127.0.0.1:5173/
```

## 更新数据

1. 用新文件替换 `竞品包装分析数据库-2026.07.08.xlsx`。
2. 运行：

```powershell
python build_data.py
```

3. 提交或上传新的 `data.js` 和 `assets/generated/images/`，重新部署网站。

`build_data.py` 会读取杯类、瓶类两个工作表，并自动抽取 Excel 中嵌入的产品图、杯底图、瓶底图和特殊点图片。

## 地图依赖

首页世界地图使用本地化 ECharts 文件：`assets/vendor/echarts.min.js` 和 `assets/vendor/world.js`。部署或分享时请保留 `assets/` 目录，地图即可离线显示完整国家轮廓热力图。

## Vercel 部署

推荐方式：

1. 将本目录上传到 GitHub 仓库。
2. 在 Vercel 中选择 `New Project`，导入该仓库。
3. Framework Preset 选择 `Other`。
4. Build Command 留空。
5. Output Directory 留空或设为 `.`。
6. 点击 Deploy。

也可以使用 Vercel CLI：

```powershell
npx vercel
```

生产部署：

```powershell
npx vercel --prod
```

`.vercelignore` 会排除源 Excel、根目录参考图和本地转换脚本，但保留网站运行所需的前端文件、地图依赖和生成图片。
