.. _cn_api_vision_transforms_rotate:

rotate
-------------------------------

.. py:function:: paddle.vision.transforms.rotate(img, angle, resample=False, expand=False, center=None, fill=0)

按角度旋转图像。

参数
:::::::::

    - img (PIL.Image|numpy.ndarray) - 输入图像。
    - angle (float|int) - 旋转角度，顺时针。
    resample (int|str, optional): An optional resampling filter. If omitted, or if the 
            image has only one channel, it is set to PIL.Image.NEAREST or cv2.INTER_NEAREST 
            according the backend. when use pil backend, support method are as following: 
            - "nearest": Image.NEAREST, 
            - "bilinear": Image.BILINEAR, 
            - "bicubic": Image.BICUBIC
            when use cv2 backend, support method are as following: 
            - "nearest": cv2.INTER_NEAREST, 
            - "bilinear": cv2.INTER_LINEAR, 
            - "bicubic": cv2.INTER_CUBIC
    - expand (bool，可选) - 是否要对旋转后的图片进行大小扩展，默认值: False，不进行扩展。
            当参数值为True时，会对图像大小进行扩展，让其能够足以容纳整个旋转后的图像。
            当参数值为False时，会按照原图像大小保留旋转后的图像。
            **这个扩展操作的前提是围绕中心旋转且没有平移。**
    - center (2-tuple，可选) - 旋转的中心点坐标，原点是图片左上角，默认值是图像的中心点。
    - fill (int，可选) - 对图像扩展时填充的值。默认值：0。

返回
:::::::::

    ``PIL.Image 或 numpy ndarray``，旋转后的图像。

代码示例
:::::::::
    
.. code-block:: python
        
    import numpy as np
    from PIL import Image
    from paddle.vision.transforms import functional as F

    fake_img = (np.random.rand(256, 300, 3) * 255.).astype('uint8')

    fake_img = Image.fromarray(fake_img)

    rotated_img = F.rotate(fake_img, 90)
    print(rotated_img.size)
    