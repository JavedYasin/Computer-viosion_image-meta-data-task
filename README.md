# Computer-viosion_image-meta-data-task
import cv2
import numpy as np 
from PIL import Image
def add_border(image, percentage=0.2, border_color='black'):
    height, width = image.shape[:2]
    border_size = int(min(height, width) * percentage)
    if border_color == 'white':
        color = (255, 255, 255)
    elif border_color == 'gray':
        color = (128, 128, 128)
    elif border_color == 'black':
        color = (0, 0, 0)
    else:
        raise ValueError('Invalid border color')
    border_image = cv2.copyMakeBorder(image, border_size, border_size, border_size, border_size,cv2.BORDER_CONSTANT, value=color)
    return border_image


img = cv2.imread('/content/baboon (1).png')
display(Image.fromarray(img))
display(Image.fromarray(add_border(img)))


def resize_img(img):
    height, width,channel=img.shape
    new_width=1024
    new_height=int(height*(new_width/width))
    resized_img=cv2.resize(img,(new_width,new_height))
    return resized_img


img = cv2.imread('/content/Circle image.png')
display(Image.fromarray(img))
display(Image.fromarray(resize_img(img)))
print(img.shape,resize_img(img).shape)


def resize_image_using_factor(img,factor):
  width, height = img.shape[:2]  
  new_width = int(width*factor)
  new_height = int(height*factor)
  image=cv2.resize(img,(new_width, new_height))
  return image


img = cv2.imread('/content/Circle image.png')
display(Image.fromarray(img))
factor= 2
display(Image.fromarray(resize_image_using_factor(img,factor)))
print(img.shape,resize_image_using_factor(img,factor).shape)
