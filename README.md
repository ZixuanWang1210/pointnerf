# Point-NeRF: Point-based Neural Radiance Fields (CVPR 2022)

## Docker模拟复现

### 注意
截止目前，Docker-image正在上传DockerHub，还**未**上传完成 （上传带宽有限，理想情况下预计8.19号中午前完成上传）

预训练模型和数据集正在上传百度网盘，还**未**上传完成

没有测试从头训练模型部分的代码，测试中直接使用预训练的MVSNet作为checkpoint

作者提供了很多数据集进行测试，但是代码的复用性较差，每个数据集都使用不同的python脚本处理，我检查并排除了**NeRF Synthetics**数据集相关py脚本中的bug，其他数据集暂时还没有处理（TanksAndTemple、scannet）

可以保证的是，在本篇READNE中出现的所有命令都是经过测试且没有问题的

### 实验环境
Docker-image：wzx1210/pointnerf:v2.0.0

下载项目
```
git clone https://e.coding.net/thu-sig-cop/robotgrasping/pointnerf.git
```

启动dev-container


### 下载预训练模型
从百度网盘下载checkpoints，并解压到项目的根目录

目录结构如下所示：

```
pointnerf
├── checkpoints
│   ├── init
    ├── MVSNet
    ├── nerfsynth
    ├── col_nerfsynth
    ├── scannet
    ├── tanksntemples
```

### 下载数据集
从百度网盘下载data_src，并解压到项目根目录

目录结构如下所示：
```
pointnerf
├── data_src
│   ├── dtu
    │   │   │──Cameras
    │   │   │──Depths
    │   │   │──Depths_raw
    │   │   │──Rectified
    ├── nerf
    │   │   │──nerf_synthetic
    │   │   │──nerf_synthetic_colmap
    ├── TanksAndTemple
    ├── scannet
    │   │   │──scans 
    |   │   │   │──scene0101_04
    |   │   │   │──scene0241_01
```

### 运行测试

```
    bash dev_scripts/w_n360/chair_test.sh
```
运行结果在，checkpoints/nerfsynth/chair/test_200000/vids中查看视频、checkpoints/nerfsynth/chair/test_200000/images中查看逐帧渲染的照片

测试指标在Testing结束时在终端中输出

类似的，也可以尝试在nerfsynth中的其他场景上测试，并查看结果
```
    bash dev_scripts/w_n360/chair_test.sh
    bash dev_scripts/w_n360/drums_test.sh
    bash dev_scripts/w_n360/ficus_test.sh
    bash dev_scripts/w_n360/hotdog_test.sh
    bash dev_scripts/w_n360/lego_test.sh
    bash dev_scripts/w_n360/materials_test.sh
    bash dev_scripts/w_n360/mic_test.sh
    bash dev_scripts/w_n360/ship_test.sh
```

