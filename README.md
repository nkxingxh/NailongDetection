# NailongDetection

使用 YOLOX 检测图片中的奶龙等目标。

## 模型

请前往 Releases 中下载模型。

## 使用

请参考 [YOLOX 的 ONNX 推理脚本](https://github.com/Megvii-BaseDetection/YOLOX/blob/main/demo/ONNXRuntime/onnx_inference.py)。

```
python onnx_inference.py -m "nailong_v2_m.onnx" -i "输入图片" -o "输出目录" -s 0.3 --input_shape 640,640
```

## 声明

本项目仅用作学习 YOLOX 模型训练与推理，且本项目没有任何承诺与保证。
