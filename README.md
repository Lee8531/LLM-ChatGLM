# LLM-ChatGLM
基于移动云服务器+昇腾910B实现NPU的部署ChatGLM-6B的api服务
# 步骤
1、安装MindSpore，参考：https://gitee.com/mindspore/mindspore

2、安装 transformers 库
	pip install git+https://github.com/huggingface/transformers

3、安装依赖
	pip install git-lfs
	pip install chardet
	pip install torch
	pip install modelscope
	pip install accelerate
	pip install -U sentence-transformers
	pip install sse_starlette
	pip install loguru
	pip install tiktoken
	pip install -U pydantic

4、搭建chatGLM3-6B的api
	1、改造官网原脚本实现基于NPU的部署
	   改造官网的api_server.py->my_api_server.py,实现基于NPU的推理，my_api_server.py文件已上传到目录

5、解决报错
	1、无法找到libgomp-d22c30c5.so.1.0.0，那么找到自己的路径指定变量即可
	export LD_PRELOAD=/root/miniconda3/envs/mindspore2.2.11_py39/lib/python3.9/site-packages/scikit_learn.libs/libgomp-d22c30c5.so.1.0.0
	2、报错信息：AttributeError: 'ChatCompletionResponse' object has no attribute 'model_dump_json'
	model_dump_json -> 改成 json 即可
	3、报错信息：'UsageInfo' has no attribute 'model_validate'，升级pydantic即可
