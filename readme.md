## 1. Lossy compression demo
See how image compression works!

Original image: ![Parrot](images/inquiline_kea.jpg)
Compressed image example: ![Compressed parrot](images/output.png)

Red channel reduction: 66%   
Green channel reduction: 53%   
Blue channel reduction: 30%    

### Process
1. Split the image into rgb channels
2. Decide on a threshold `t1`, between 0 - 100. 
3. For each channel per pixel, discard pixels values lower than threshold `t1`. This means higher thresholds have more pixels thrown away - more compression.
4. Stack these channels back together into an image


### Prerequisites
- Python 3.13
- PIL (Pillow) for image processing.

### Getting started

1. Clone this repository and cd into it
2. If you don't have Pillow, you can create a virtual environment. Example using uv for python package management:
```
uv venv
source .venv/bin/activate (on mac)
uv pip install Pillow
```
3. Run `python3 lossy_compression.py`

## 2. Steganography demo
This image contains a message.
![grayscale-coded-image](images/grayscale-coded-kea.png)
A closer look at where the message is hidden.
![grayscale-lsb-plane](images/grayscale-lsb-plane.png) 

### Prerequisites
- Python 3.13
- cv2, numpy, matplotlib. 
- ipykernel for running jupyter notebooks

### Getting started
1. If you don't have above libraries, you can use
```
uv venv
source .venv/bin/activate (on mac)
uv pip install notebook cv2 numpy matplotlib 
```
2. Open a new terminal and run `jupyter notebook`
3. Click on this file.


### Process
1. Convert hidden message into ascii representations and then into binary 
2. In each channel, each pixel is stored in a single byte, which is 8 bits. This provides us with 8 bit planes of varying significance
To be discreet, we extract the least significant bit plane values.
3. Mix our message in binary representation into the lowest bit plane
4. Add the decoded bit plane back to the original image
5. To verify, we could retrieve the message from the image