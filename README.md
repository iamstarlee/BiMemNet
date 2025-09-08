# 0. 多卡并行训练和推理
```python
CUDA_VISIBLE_DEVICES=2,3,4,5,6,7 python -m torch.distributed.launch --nproc_per_node=6 --master_port=25641 train.py
```
```python
CUDA_VISIBLE_DEVI=0 python predict.py
```

# 1. 连续学习化训练
- 需要对网络添加一定数量的生成模块，具体体现在注释掉train.py中333~342行的代码，修改490~491行优化器的参数pg0→reg_params，注释掉493行和494行。
