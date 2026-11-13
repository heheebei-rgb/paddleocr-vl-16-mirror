# PaddleOCR-VL 1.6 (0.9B) 权重镜像（GitHub 源码包分发）

[PaddlePaddle/PaddleOCR-VL-1.6](https://huggingface.co/PaddlePaddle/PaddleOCR-VL-1.6)（PaddleOCR 视觉语言 OCR 模型，apache-2.0，0.9B 参数）权重的分块镜像，用于无法直连 HuggingFace 的内网环境。

## 下载与重建
1. 本仓库页面 **Code → Download ZIP**（约 1.8GB），解压
2. 在解压目录执行 `python3 merge_and_verify.py`（Python3 标准库，无需联网）
3. 脚本自动把 21 个分块合并回 `model.safetensors` 并做 sha256 全量校验
4. 完成后本目录即完整模型：权重 + tokenizer 全套 + 4 个自定义模型代码文件（configuration/modeling/processing/image_processing_paddleocr_vl.py），transformers `trust_remote_code=True` 可直接加载（原模型卡见 MODEL_CARD.md）

## 内容清单
- `chunks/main/` — model.safetensors 的 21 个 90MB 分块
- `MANIFEST.json` — 全部文件的 sha256 + 字节数
- `merge_and_verify.py` — 合并 + 校验脚本
- tokenizer：tokenizer.json / tokenizer.model / added_tokens.json / special_tokens_map.json / tokenizer_config.json
- config.json / generation_config.json / preprocessor_config.json / processor_config.json / chat_template.jinja / inference.yml
- 自定义模型代码：configuration_paddleocr_vl.py / modeling_paddleocr_vl.py / processing_paddleocr_vl.py / image_processing_paddleocr_vl.py
