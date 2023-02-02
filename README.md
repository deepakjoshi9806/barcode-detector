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
## Methodology
- This program uses YoloV5 and Pyzbar at the backend.
- Each image is tested for presence of certain objects such as Book, Bottle, Surfboard and Cell Phone with a threshold of 0.01.
- The reason this hack works is because of the assumption that the background is of uniform colour and the only objects that can be detected are the target objects. And That's why we set the threshold values as 0.01.
- Ones the objects are detected, a copy of object is passed onto the `decode()` function of pyzbar.
- If a barcode if found, A rectangle is drawn around the detected target region and  its data is stored in a Hash Map a.k.a Dictonery.
- The key of the hash map is the data of barcode and the value of hash map is the number of times that object is found in the sample image.
- If a batch of image is passed as input, then the barcode count is meant for all the objects detected in that batch of image.
- If the barcode is not detected, a Red rectangle is drawn at the centre of the centre of the detected object, to indicate that the barcode is not found.
