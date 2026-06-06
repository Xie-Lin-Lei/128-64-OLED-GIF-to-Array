# 在线访问地址

https://xie-lin-lei.github.io/128-64-OLED-GIF-to-Array/

# 128*64 OLED GIF to Array

这是一个用于 `128x64` 单色 OLED 屏幕的 GIF 转数组工具。网页会在浏览器本地读取 GIF 图片，自动把 GIF 拆分成每一帧静态图，然后把每一帧转换成 Arduino/C 可用的 `uint8_t` 数组。

输出格式示例：

```cpp
const uint8_t bitmap_1[] = {
  0x00, 0x00, 0x00
};

const uint8_t bitmap_2[] = {
  0x00, 0x00, 0x00
};
```

所有处理都在浏览器本地完成，图片不会上传到服务器。

## 如何使用

1. 打开网页。

   本地使用时，双击 `index.html`，或者在浏览器地址栏输入：

   ```text
   file:///D:/128_64_OLED/index.html
   ```

2. 上传 GIF 图片。

   在 `Select GIF image` 区域点击 `选择文件`，选择需要转换的 GIF。网页会自动读取 GIF，并显示拆分出的帧数。

3. 确认画布尺寸。

   `Canvas size(s)` 已固定为：

   ```text
   128 x 64 px
   ```

   这个尺寸不可修改，适合 128x64 单色 OLED 屏幕。

4. 调整图像设置。

   可以根据显示效果调整：

   - `Background color`：背景颜色
   - `Invert image colors`：反转黑白
   - `Dithering`：二值化或 Floyd-Steinberg 抖动
   - `Brightness / alpha threshold`：亮度阈值
   - `Scaling`：缩放方式
   - `Rotate image`：旋转图像
   - `Flip image`：水平或垂直翻转

5. 查看预览。

   `Preview` 区域会显示当前帧的 128x64 单色效果。右侧会显示 GIF 拆分出的所有帧，可以点击不同帧查看预览。

6. 生成数组。

   上传 GIF 后网页会自动生成代码，也可以点击 `Generate code` 重新生成。

   默认数组名称为：

   ```cpp
   bitmap_1
   bitmap_2
   bitmap_3
   ```

   如果 GIF 有 28 帧，就会生成：

   ```cpp
   const uint8_t bitmap_1[] = { ... };
   const uint8_t bitmap_2[] = { ... };
   ...
   const uint8_t bitmap_28[] = { ... };
   ```

7. 复制或下载结果。

   - 点击 `Copy Output` 复制输出框里的全部数组代码。
   - 点击 `Download .h` 下载头文件。
   - 如果浏览器阻止自动下载，点击旁边出现的 `Manual download` 链接。

## 注意事项

- 本工具专门面向 `128x64` OLED，画布尺寸固定为 `128 x 64`。
- 每一帧会生成 `1024 bytes` 数据，因为 `128 x 64 / 8 = 1024`。
- 使用 `file://` 本地打开时，部分浏览器可能会限制复制或自动下载。如果遇到问题，建议开启 GitHub Pages 后通过 HTTPS 网页使用。
- `gifuct-js.min.js` 是本地 GIF 解码依赖，请和 `index.html` 放在同一目录。

## 作者

解林磊
