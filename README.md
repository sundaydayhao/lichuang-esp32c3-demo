# 立创 ESP32-C3 示例工程集合

这个仓库整理了一组基于 ESP-IDF 的 ESP32-C3 示例工程，覆盖 GPIO、I2C 传感器、姿态/方位检测、I2S 音频、SPI LCD、触摸屏、LVGL、Wi-Fi、SNTP、天气桌面、手持设备和语音 AI 对话等常见开发场景。

每个示例都是独立的 ESP-IDF 工程，需要进入对应工程目录后再执行 `idf.py` 命令。

## 示例目录

| 序号 | 目录 | 内容 |
| --- | --- | --- |
| 01 | `01-hello_world/hello_world` | Hello World 与 FreeRTOS 基础任务 |
| 02 | `02-gpio_key/gpio_key` | GPIO 按键输入 |
| 03 | `03-humi_temp/humi_temp` | 温湿度传感器读取 |
| 04 | `04-attitude/attitude` | 姿态传感器数据读取 |
| 05 | `05-azimuth/azimuth` | 电子罗盘/方位角读取 |
| 06 | `06-i2s_es8311/i2s_es8311` | I2S 与 ES8311 音频 Codec |
| 07 | `07-spi_lcd/spi_lcd` | SPI LCD 显示 |
| 08 | `08-spi_lcd_touch/spi_lcd_touch` | SPI LCD 与触摸 |
| 09 | `09-lvgl_demo/lvgl_demo` | LVGL 图形界面示例 |
| 10 | `10-scan/scan` | Wi-Fi 扫描 |
| 11 | `11-station/station` | Wi-Fi Station 连接 |
| 12 | `12-sntp/sntp` | SNTP 网络授时 |
| 13 | `13-weather/13-weather/weather` | HTTP 天气接口示例 |
| 14 | `14-desktop_weather/desktop_weather` | 桌面天气显示 |
| 15 | `15-handheld/15-handheld/handheld` | 手持综合示例 |
| 16 | `16-ai_chat/ai_chat` | 语音识别、AI 对话与语音合成示例 |

## 环境准备

1. 安装并配置 ESP-IDF。
2. 连接 ESP32-C3 开发板，并确认串口号。
3. 在 ESP-IDF 终端中进入任一示例工程目录。
4. 如工程依赖外部组件，首次构建时 ESP-IDF 会自动解析并下载组件。

## 编译与烧录

以 Hello World 为例：

```powershell
cd 01-hello_world\hello_world
idf.py set-target esp32c3
idf.py -p COMx build flash monitor
```

请将 `COMx` 替换为实际串口号。退出串口监视器可按 `Ctrl+]`。

其他示例的使用方式类似：进入对应工程目录后执行 `idf.py build flash monitor`。

## 配置说明

- Wi-Fi 相关示例通常需要通过 `idf.py menuconfig` 配置 SSID 和密码，或修改工程中的默认配置。
- 天气、语音识别、语音合成和 AI 对话示例需要配置对应服务的 Key、Token 或接口参数。
- 不建议把真实 Wi-Fi 密码、API Key、Token 等敏感信息提交到公开仓库。
- LCD、触摸、I2C、I2S 等外设示例需要确认开发板引脚与源码中的 GPIO 定义一致。

## 常用命令

```powershell
# 配置工程
idf.py menuconfig

# 编译
idf.py build

# 烧录并打开串口监视器
idf.py -p COMx flash monitor

# 清理构建产物
idf.py fullclean
```

## 注意事项

- 各示例目录内已有更具体的 `README.md`，遇到硬件连接或示例行为问题时请优先查看对应示例说明。
- 若下载组件较慢，可检查 ESP-IDF 组件管理器、代理或网络环境。
- 如果烧录失败，请确认串口未被其他程序占用，并检查开发板是否进入下载模式。
