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
9. The output will be saved to `runs/detect/LATEST` directory.
10. To detect barcode in a particular image run:
- 		python detect.py --source img/ImageNAME.jpg  --classes 73 39 37 62 67 --hide-labels --hide-conf

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
- No seperate model is used to partially detect the barcode, so this is out of picture at the moment. 

## Cases Considered:
1. Output the imput image.
2. Draw black BBox around detected Items.
3. Draw Green BBox around detected Barcode
4. Print the data of the barcode with its associated count
5. Draw red BBox around items where no barcode is detected
## Output images:
Output from terminal on barcode data and its associated count:
{
    "b'8901030656026'": 2,
    "b'8901719112737'": 2,
    "b'8901030574252'": 1,
    "b'8901725114916'": 3,
    "b'8901063160088'": 3,
    "b'8901030578199'": 4,
    "b'8901719107771'": 1,
    "b'8901725118457'": 2,
    "b'8901719110856'": 1
}

![1](https://user-images.githubusercontent.com/60206883/216367855-e3f59b0b-3abc-4da6-a6bc-5bdbc61e4928.jpg)
![2](https://user-images.githubusercontent.com/60206883/216367946-584b990a-44e3-4f0e-9959-2906765ae619.jpg)
![3](https://user-images.githubusercontent.com/60206883/216368084-c56340f8-8045-4f48-a1c7-ca047e5a3f48.jpg)
![4](https://user-images.githubusercontent.com/60206883/216368096-d440f5da-95c7-4238-9710-d831c0b34530.jpg)
![5](https://user-images.githubusercontent.com/60206883/216368119-3d0d37b2-ea74-4871-b5c4-1f56dd44884d.jpg)
![6](https://user-images.githubusercontent.com/60206883/216368217-ea2fe0b5-8bbe-48d6-8925-86189b3329cf.jpg)
![7](https://user-images.githubusercontent.com/60206883/216368249-19395707-753f-4435-ab89-6904e6299a86.jpg)
![8](https://user-images.githubusercontent.com/60206883/216368268-c9c02b7f-25a7-4651-b6f2-49bee2aa194c.jpg)
![9](https://user-images.githubusercontent.com/60206883/216368293-45f74aab-3574-43b5-a9a0-d35eed054584.jpg)
![10](https://user-images.githubusercontent.com/60206883/216368314-751e68a4-ee08-4657-a644-22c1f9cf63cf.jpg)
![11](https://user-images.githubusercontent.com/60206883/216368328-4043f3bc-a75f-4d28-bb98-2b8887ff4914.jpg)
![12](https://user-images.githubusercontent.com/60206883/216368350-a10de4bd-9018-46ed-86a5-ee834d030cd5.jpg)
![13](https://user-images.githubusercontent.com/60206883/216368387-6aea9bdf-1a20-4828-a457-6deda57ca481.jpg)

