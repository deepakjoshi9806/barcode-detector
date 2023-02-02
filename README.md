# Barcode-Detection
This assignment uses YOLOv5 and pyzbar to best detect the barcodes in a sample picture with multiple target objects.

## Description
Here are the steps to run the project:
- Implement Yolov5 with the tuned model parameters.
- Use the trained model and inference on a new image.
- For each object in target image, run pyzbar decode function to extract the barcode value.
- Serially print the output containing the barcode data and its associated count on the command line.

## Installation

1. Install python 39 (for best results)
2. Install CUDA from [Here](https://developer.nvidia.com/cuda-downloads). Choose:
- 		Version:10
- 		Installer Type: exe(local)
- 		Architecture: x86_64 (for 64bit) or x86 for 32bit
- 		OS: As required
3. Installing PyTorch: visit [here](https://pytorch.org/get-started/locally/) and generate the command to install PyTorch. Choose:
- 		PyTorch Build: Stable
- 		OS: As required
- 		package: pip
- 		Language: Python
- 		Computer platform: CUDA 11 or CPU if you don't have a GPU
- 		Run the generated command on the CLI
4. Clone this Repository locally and run:
- 		pip install -r requirements.txt
5. If there are errors referring to Visual Studio C++ Compiler, please install it 
6. There are sample images in `img` Directory. To get started with Detection run: 
- 		python detect.py --source img  --classes 73 39 37 62 67 --hide-labels --hide-conf
7. A window with Input image will appear, press ESC to clear it.
8. This command Iterates through all the images inside the img Directory and labels each object and detected barcode. The data inside the barcode will be serially printed on the CLI.
9. To detect barcode in a particular image run:
- 		python detect.py --source img/ImageNAME.jpg  --classes 73 39 37 62 67 --hide-labels --hide-conf
10. The output will be saved to runs/detect/LATEST directory.
11. The Output from the previously provided images is saved at `img/datect/exp42`
