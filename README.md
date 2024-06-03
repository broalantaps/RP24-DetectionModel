# RP24-DetectionMode-Temp  

此文档还在填坑中，打完分区赛再继续完善

---

为促进新队伍视觉技术快速成长，老队伍不再固步自封，现开源RobotPilots视觉自瞄网络模型  

该模型的识别能力较强，能够缩小与强队之间的视觉识别GAP

---
backbone网络采用MobieNetV3，使用Openvino GPU推理，纯推理帧率可稳定125FPS

设备：NUC12WSKi7，内存条2x16G 3200MHz


---
Openvino版本：24（23也行）

**激活nuc上的gpu**  
mkdir neo  

cd neo  

wget https://github.com/intel/intel-graphics-compiler/releases/download/igc-1.0.13463.18/intel-igc-core_1.0.13463.18_amd64.deb  

wget https://github.com/intel/intel-graphics-compiler/releases/download/igc-1.0.13463.18/intel-igc-opencl_1.0.13463.18_amd64.deb  

wget https://github.com/intel/compute-runtime/releases/download/23.09.25812.14/intel-level-zero-gpu-dbgsym_1.3.25812.14_amd64.ddeb  

wget https://github.com/intel/compute-runtime/releases/download/23.09.25812.14/intel-level-zero-gpu_1.3.25812.14_amd64.deb  

wget https://github.com/intel/compute-runtime/releases/download/23.09.25812.14/intel-opencl-icd-dbgsym_23.09.25812.14_amd64.ddeb  

wget https://github.com/intel/compute-runtime/releases/download/23.09.25812.14/intel-opencl-icd_23.09.25812.14_amd64.deb  

wget https://github.com/intel/compute-runtime/releases/download/23.09.25812.14/libigdgmm12_22.3.0_amd64.deb  

wget https://github.com/intel/compute-runtime/releases/download/23.09.25812.14/ww09.sum  

sha256sum -c ww09.sum  

sudo dpkg -i *.deb  


**安装Openvino24**  

Step 1: Download the GPG-PUB-KEY-INTEL-SW-PRODUCTS.PUB. You can also use the following command  

wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS.PUB  

Step 2: Add this key to the system keyring  

sudo apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS.PUB  

Step 3: Add the repository via the following command  


Ubuntu 22  

echo "deb https://apt.repos.intel.com/openvino/2024 ubuntu22 main" | sudo tee /etc/apt/sources.list.d/intel-openvino-2024.list  

Ubuntu 20  

echo "deb https://apt.repos.intel.com/openvino/2024 ubuntu20 main" | sudo tee /etc/apt/sources.list.d/intel-openvino-2024.list  

Step 4: Update the list of packages via the update command  

sudo apt update  

Step 5: Verify that the APT repository is properly set up. Run the apt-cache command to see a list of all available OpenVINO packages and components  

apt-cache search openvino  

Step 6: Install OpenVINO Runtime  

sudo apt install openvino-2024.0.0  


Openvino代码仅供参考，不一定能跑（老东西已无力维护）

---

输出：0到8是四个关键点，顺序从左上角开始逆时针；9到13是颜色（红蓝灰紫），13到22是数字  



G（哨兵）
1（一号）
2（二号）	
3（三号）	
4（四号）	
5（五号）	
O（前哨站）
Bs（基地）
Bb（基地大装甲）	

---
使用指南：  

1、海康相机低曝光、高增益，光圈最大处往下拧一点  

2、烧饼使用模型时建议把置信度调高，避免误识别  

3、误识别一般只是闪过一帧，自瞄有连续三帧识别才锁敌的话问题不大   

---

2024南部分区赛深圳大学VS哈尔滨工业大学（深圳）效果视频：  

链接：https://pan.baidu.com/s/1hkM0rZQneXRZiHC24oldig?pwd=RP24
提取码：RP24    
