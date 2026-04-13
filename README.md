# Ultralytics YOLO26n 在树莓派4B 上的基准测试
# Ultralytics YOLO26n on Raspberry Pi 4B Benchmark

本项目展示了 Ultralytics YOLO26n 模型在 **树莓派4B** 上的基准测试结果。
This project showcases the benchmark results of the Ultralytics YOLO26n model on the **Raspberry Pi 4B**.

---

## 基准测试结果 | Benchmark Results

测试环境：
- **设备:** 树莓派4B（4GB）
- **系统:** Raspberry Pi OS (Debian GNU/Linux 13)
- **输入尺寸:** 416
- **Ultralytics 版本:** 8.4.37

Environment:
- **Device:** Raspberry Pi 4B (4GB)
- **OS:** Raspberry Pi OS (Debian GNU/Linux 13)
- **Image Size:** 416
- **Ultralytics Version:** 8.4.37

### 详细数据表 | Detailed Data Table

| 格式（部分） \| Format(Partial) | 大小 \| Size (MB) | 指标/mAP50-95(边界框) \| metrics/mAP50-95(B) | 推理时间 \| Inference time (ms/im) | 帧率 \| FPS |
| :--- | :--- | :--- | :--- | :--- |
| PyTorch | **5.3** | **0.4392** | 654.04 | 1.53 |
| TorchScript | 9.7 | 0.4306 | 712.83 | 1.4 |
| ONNX | 9.4 | 0.4306 | 197.76 | 5.06 |
| OpenVINO | 9.6 | 0.4306 | 188.16 | 5.31 |
| MNN | 9.3 | 0.4306 | 206.52 | 4.84 |
| NCNN | 9.3 | 0.4371 | **184.24** | **5.43** |

> 推理时间不包含预处理和后处理。测试时设备已安装外部散热以防止降频。
> Inference time does not include pre/ post-processing. The device was equipped with external cooling to prevent throttling during testing.
---

## 如何复现 | How to Reproduce

要在所有导出格式上重现上述基准测试，请运行以下代码：
To reproduce the above benchmarks on all export formats, run this code:

```Bash
# Benchmark YOLO26n speed and accuracy on the COCO128 dataset for all export formats
yolo benchmark model=yolo26n.pt data=coco128.yaml imgsz=416
```