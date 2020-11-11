# set_gpu_fans_public
Controlling the fan speed of an NVIDIA GPU on a headless linux system requires spoofing a display.
This can be used to gain a few percent additonal performance, at the cost of increased noise.
For installation and usage, read the comments in cool_gpu.

## 使用说明
使用之前，需要对cool_gpu文件和nvscmd文件中的路径进行修改，需要修改的路径如下

### cool_gpu
- dir=/home/fzw/control_gpu_fans/set_gpu_fans_public -> 为你自己git下来的目录
- /usr/bin/nvidia-smi -pm 1 -> 为你自己机器上nvidia-smi命令的路径

### nvscmd
- /usr/bin/nvidia-smi -> 为你自己机器上nvidia-smi的路径
- /usr/bin/nvidia-settings -> 为你自己机器上nvidia-settings的路径

### Get Started
1. git clone https://github.com/zhiwei-Feng/set_gpu_fans_public.git
2. cd set_gpu_fans_public
3. sudo tcsh
4. ./cool_gpu >& controller.log &
5. tail -f controller.log

## temp of multi-gpu is individually obtained and adjusted 
```bash
  liuk@acgpu1 ~ $ nvidia-smi 
  Sat May 12 02:17:41 2018       
  +-----------------------------------------------------------------------------+
  | NVIDIA-SMI 396.24                 Driver Version: 396.24                    |
  |-------------------------------+----------------------+----------------------+
  | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
  | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
  |===============================+======================+======================|
  |   0  GeForce GTX 108...  On   | 00000000:18:00.0 Off |                  N/A |
  | 90%   72C    P2   202W / 250W |   2724MiB / 11178MiB |    100%      Default |
  +-------------------------------+----------------------+----------------------+
  |   1  GeForce GTX 108...  On   | 00000000:3B:00.0 Off |                  N/A |
  | 90%   72C    P2   196W / 250W |   2724MiB / 11178MiB |    100%      Default |
  +-------------------------------+----------------------+----------------------+
  |   2  TITAN V             On   | 00000000:86:00.0 Off |                  N/A |
  | 80%   63C    P2   142W / 250W |   2983MiB / 12066MiB |    100%      Default |
  +-------------------------------+----------------------+----------------------+
  |   3  TITAN V             On   | 00000000:AF:00.0  On |                  N/A |
  | 85%   66C    P2   151W / 250W |   2983MiB / 12066MiB |    100%      Default |
  +-------------------------------+----------------------+----------------------+
```
