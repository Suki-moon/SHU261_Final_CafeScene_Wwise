# SHU261_Final_CafeScene_Wwise

初始化于 2026-11-09。

## 开始使用

```bash
git clone https://github.com/Suki-moon/SHU261_cafe.git
cd SHU261_cafe
```

## 说明


# 僻静街道咖啡馆 - 3D环境声设计 

## 📝 项目简介
本项目为《基础实践》期末作品，旨在通过数字音频工作站（REAPER）与游戏音频中间件（Wwise），设计并搭建一套位于秋季僻静街道旁的咖啡馆环境声系统。
作品听觉重心集中在**咖啡馆室内**，整体基调安静、舒适，通过基底循环声与各类随机的日常细节音效，构建出真实的室内外空间感。

## 🛠️ 使用工具
*   **音频剪辑与处理**：REAPER v7.83
*   **游戏音频中间件**：Wwise 2025.1.11.9262

## 🎧 声音资产清单 (WAV Format: 48kHz / 24bit / Stereo)
### 1. 基底环境声 (Base)
*   `base_cafe_music.wav` (约169秒)：包含室内极弱的空气底噪与背景白噪音，用于铺底。在 Wwise 中设置为 `Loop Infinite`（无限循环）。

### 2. 随机细节音效 (Random SFX)
所有短音效均在 Wwise 中放入 `Random Container`（随机容器），并开启 `Shuffle` 模式以避免机械重复。
*   **室内近景**：
    *   `random_chair_move` (x5)：椅子挪动声
    *   `random_cup_placed_on_table` (x6)：咖啡杯放置声
    *   `random_pouring_coffee` (x2)：咖啡冲泡水流声
    *   `random_footsteps` (x4)：室内脚步声
*   **室外远景**：
    *   `random_wind_chimme` (x6)：屋檐风铃声
    *   `random_bike_bell` (x4)：街道自行车铃声

## ⚙️ Wwise 交互逻辑与技术实现
1.  **随机触发**：利用 `Random Container` 管理所有短音效变体，设置 `Limit Repetition` 防止同一声音连续触发。
2.  **空间定位 (Positioning)**：所有随机声均开启 `3D Spatialization` (`Position + Orientation`)，并将 `Pan/3D Mix` 设为 `100`。
3.  **距离衰减 (Attenuation)**：为随机声绑定自定义衰减曲线。通过调整 `Max distance` 区分室内近景（极短距离）与室外远景（较长距离）。
4.  **频段模拟**：在衰减曲线中启用了 `Low-pass Filter`（低通滤波），模拟声音在空气中远距离传播时高频损失的物理现象。

## 📂 仓库目录结构
*   `/Assets_WAV`：存放最终导出的 48kHz/24bit WAV 音频资产。
*   `/Wwise_Project`：存放 Wwise 工程文件及配置（*注：已配置 `.gitignore` 排除缓存文件*）。
*   `/Screenshots`：存放 REAPER 剪辑工程、Wwise 层级、Positioning 参数设置及 Soundcaster 3D 测试的截图。
*   `README.md`：项目说明文档。
