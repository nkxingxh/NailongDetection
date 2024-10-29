# NailongDetection

使用 YOLOX 检测图片中的奶龙等目标。

![输出效果图](./images/examples.png)

## 模型

请前往 Releases 中下载模型。压缩包中的 `labels.txt` 为分类标签文件。

## 使用

### 直接推理

请参考 [YOLOX 的 ONNX 推理脚本](https://github.com/Megvii-BaseDetection/YOLOX/blob/main/demo/ONNXRuntime/onnx_inference.py)。

```
python onnx_inference.py -m "nailong_v2_m.onnx" -i "输入图片" -o "输出目录" -s 0.3 --input_shape 640,640
```

### 搭建API服务

[nkxingxh/yolox-onnx-api-server](https://github.com/nkxingxh/yolox-onnx-api-server)

[搭建API服务](https://github.com/nkxingxh/yolox-onnx-api-server)给其他程序调用。

### MiraiEz 图片过滤

> 支持 mirai-api-http 的 PHP 机器人框架。
> 方便、快速、高效地使用 PHP 编写你自己的 Bot。

[群图片过滤插件](https://github.com/nkxingxh/miraiez-plugins/blob/main/top.nkxingxh.miraiez.yolox.ImageFilter.php)

使用插件前, 需要先[搭建API服务](#搭建API服务)。

安装插件后, 在BOT所在的任意群发送一张任意图片, 插件会自动生成配置。

修改配置中的 `classes` 部分即可指定目标类别。具体选项说明请查看生成的配置文件。

```json
"classesDesc": "可以配置多个类别组",
"classes": [
    {
        "classId": [1],
        "className": ["nailong"],
        "score": 0.7,
        "actionDesc": "可以对每一组类别单独设置动作",
        "action": {
            "recall": false,
            "reply": "拒绝唐龙",
        },
    },
    {
        "classId": [],
        "className": ["long"],
        "score": 0.75,
        "action": {
            "recall": false,
            "reply": "龙图也是龙"
        }
    }
]
```

### nonebot-plugin-nailongremove

[Refound-445/nonebot-plugin-nailongremove](https://github.com/Refound-445/nonebot-plugin-nailongremove)

> NailongRemove 是一款奶龙识别插件，可以识别群中的奶龙表情包并撤回该表情。

安装插件后, 修改配置中的 `nailong_model:int=1` 即可。

插件默认使用 `nailong_v2.1_m.onnx` 模型进行检测。

## 声明

本项目仅用作学习 YOLOX 模型训练与推理，且本项目没有任何承诺与保证。
