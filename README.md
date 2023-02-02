# Barcode-detection
This assignment uses YOLOv5 and pyzbar to best detect the barcodes in a sample picture with multiple target objects.

## Description
Here are the steps to run the project:
- Implement Yolov5 with the tuned model parameters
- use the model trained and inference on a new image
- for each object in target image, run pyzbar decode function to extract the barcode value
- serially print the output containing the barcode data and its associated count on the command line 

## Installation

1. install python 39 (for best results)
2. install CUDA from [Here](https://developer.nvidia.com/cuda-downloads). Choose:
- 		version:10
- 		Installer Type: exe(local)
- 		Architecture: x86_64 (for 64bit) or x86 for 32bit
- 		OS: As required
3. Installing PyTorch: visit [here](https://pytorch.org/get-started/locally/) and generate the command to install PyTorch. Choose:
- 		PyTorch Build: Stable
- 		OS: As required
- 		package: pip
- 		Language: Pythob
- 		Computer platform: CUDA 11 or CPU if you don't have a GPU
- 		Run the generated command on the CLI
4. Clone this Repository locally and run:
5. 		pip install -r requirements.txt
6. If there are errors referring to Visual Studio, please install it 
7. There are sample images in [img] Directory. Run: 
- 		python detect.py --source img  --classes 73 39 37 62 67 --hide-labels --hide-conf
8. A window with Input image will appear, press ESC to clear it.
9. This command Iterates through all the images inside the img Directory and labels each object and detected barcode. The data inside the barcode will be serially printed on the CLI.
10. To detect barcode in a particular image run:
- 		python detect.py --source img/ImageNAME.jpg  --classes 73 39 37 62 67 --hide-labels --hide-conf
11. The output will be saved to `runs/detect/LATEST` directory. 
