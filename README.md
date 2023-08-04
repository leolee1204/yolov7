# yolov7
train model and detect Uno

### pip install
* cd yolov7
* pip install -r requirements.txt

### About CUDA
* NVIDA Control Panel(Find CUDA Version)
* 左下角 按下系統資訊
* 執行階段版本 查看版本
* 下載相對應版本(https://developer.nvidia.com/cuda-toolkit-archive)
* 解壓縮, 將資料夾裡面 (bin, include, lib )覆蓋至 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\(CUDA VERSION內)

### pip pytorch
* https://pytorch.org/get-started/locally/
* for example input in terminal : pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

 ### error code soulation
 raise AssertionError("Torch not compiled with CUDA enabled") AssertionError: Torch not compiled with CUDA enabled
 * pip uninstall torch
 * pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

### download dataset
* https://public.roboflow.com/

### change train path
* ../Uno/data.yaml

```
train: ../Uno/train/images
val: ../Uno/valid/images

nc: 15
names: ['0', '1', '10', '11', '12', '13', '14', '2', '3', '4', '5', '6', '7', '8', '9']
```

### add ymal (yolov7>cfg>training)
* 複製一份 yolov7.yaml
* change name -> yolov7-uno.yaml
* change nc
```
nc: 80 
```

### training model
* python train.py --weights weights/yolov7.pt --cfg cfg/training/yolov7-uno.yaml --data ../Uno/data.yaml  --batch-size 2
* 生成 yolovt>weights best.pt

### detect test images
* python detect.py –weight weights/best.pt –source ../Uno/test/images/
* detect images info > runs/detect/exp 
