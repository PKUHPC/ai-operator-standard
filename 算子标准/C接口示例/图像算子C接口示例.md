# C语言参考定义示例（图像算子部分）

<p id="701"></p>

## 7.1 调整图像亮度
### C语法：
```c++
Status op_adjust_brightness(const Tensor image,
                            const float brightness_factor,
                            Tensor *out);
```
### 参数：
image(IN)：表示待调整的图像，维度为3维或4维。  
brightness_factor(IN)：表示调整亮度的幅度，数据类型为32位浮点数或64位浮点数。  
out (OUT)：表示调整亮度后的图像，数据类型和维度信息与输入image保持一致。
### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围，例如brightness_factor＞1。

----------

<p id="702"></p>

## 7.2 调整图像对比度
### C语法：
```c++
Status op_adjust_contrast(const Tensor image,
                        const float contrast_factor,
                        Tensor *out);
```
### 参数：
image(IN)：表示待调整的图像，维度为3维或4维。  
contrast_factor(IN)：表示调整对比度的幅度，数据类型为32位浮点数或64位浮点数，注意contrast_factor非负。  
out (OUT)：表示调整对比度后的图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围，例如contrast_factor＜0。

---------

<p id="703"></p>

## 7.3 图像伽马变换（幂律变换）
### C语法：
```c++
Status op_adjust_gamma(const Tensor image,
                        const float gamma,
                        const float gain,
                        Tensor *out);
```
### 参数：
image(IN)：表示待变换的图像，维度为3维或4维。  
gamma(IN)：表示伽马变换（幂律变换）的指数参数，数据类型为32位浮点数或64位浮点数，非负。  
gain(IN)：表示伽马变换（幂律变换）的乘子参数，数据类型为32位浮点数或64位浮点数。  
out (OUT)：表示伽马变换（幂律变换）后的图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围，例如gamma＜0。

---------

<p id="704"></p>

## 7.4 调整图像色调
### C语法：
```c++
Status op_adjust_hue(const Tensor image,
                    const float hue_factor,
                    Tensor *out);
```
### 参数：
image(IN)：表示待调整的图像，维度为3维或4维。  
hue_factor(IN)：表示调整色调的幅度，数据类型为32位浮点数或64位浮点数，范围为[-1, 1]。  
out (OUT)：表示调整色调后的图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。

---------

<p id="705"></p>

## 7.5 调整图像饱和度
### C语法：
```c++
Status op_adjust_saturation(const Tensor image,
                            const float saturation_factor,
                            Tensor *out);
```
### 参数：
image(IN)：表示待调整的图像，维度为3维或4维。  
saturation_factor(IN)：表示调整饱和度的幅度，数据类型为32位浮点数或64位浮点数，非负。  
out (OUT)：表示调整饱和度后的图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="706"></p>

## 7.6 随机调整图像亮度
### C语法：
```c++
Status op_random_brightness(const Tensor image,
                            const float lower,
                            const float upper,
                            const int seed,
                            Tensor *out);
```
### 参数：
image(IN)：表示待调整的图像，维度为3维或4维。  
lower(IN)：亮度调整参数brightness_factor的下限，数据类型为32位浮点数或64位浮点数。  
upper(IN)：亮度调整参数brightness_factor的上限，数据类型为32位浮点数或64位浮点数。  
seed(IN)：int32类型变量，用于生成随机种子。  
out (OUT)：表示调整亮度后的图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="707"></p>

## 7.7 随机调整图像对比度
### C语法：
```c++
Status op_random_contrast(const Tensor image,
                        const float lower,
                        const float upper,
                        const int seed,
                        Tensor *out);
```
### 参数：
image(IN)：表示待调整的图像，维度为3维或4维。  
lower(IN)：对比度调整参数contrast_factor的下限，数据类型为32位浮点数或64位浮点数。  
upper(IN)：对比度调整参数contrast_factor的上限，数据类型为32位浮点数或64位浮点数。  
seed(IN)：int32类型变量，用于生成随机种子。  
out (OUT)：表示调整对比度后的图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="708"></p>

## 7.8 调随机调整图像色调
### C语法：
```c++
Status op_random_hue(const Tensor image,
                    const float lower,
                    const float upper,
                    const int seed,
                    Tensor *out);
```
### 参数：
image(IN)：表示待调整的图像，维度为3维或4维。  
lower(IN)：色调调整参数hue_factor的下限，数据类型为32位浮点数或64位浮点数，取值范围为[-1, 1]。  
upper(IN)：色调调整参数hue_factor的上限，数据类型为32位浮点数或64位浮点数，取值范围为[-1, 1]。  
seed(IN)：int32类型变量，用于生成随机种子。  
out (OUT)：表示调整色调后的图像，数据类型和维度信息与输入image保持一致。  

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。

---------

<p id="709"></p>

## 7.9 随机调整图像饱和度
### C语法：
```c++
Status op_random_saturation(const Tensor image,
                            const float lower,
                            const float upper,
                            const int seed,
                            Tensor *out);
```
### 参数：
image(IN)：表示待调整的图像，维度为3维或4维。  
lower(IN)：饱和度调整参数saturation_factor的下限，数据类型为32位浮点数或64位浮点数。  
upper(IN)：饱和度调整参数saturation_factor的上限，数据类型为32位浮点数或64位浮点数。  
seed(IN)：int32类型变量，用于生成随机种子。  
out (OUT)：表示调整饱和度后的图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。

---------

<p id="710"></p>

## 7.10 RGB图像转灰度图像
### C语法：
```c++
Status op_rgb_to_grayscale(const Tensor image,
                            Tensor *out);
```
### 参数：
image(IN)：表示待转换的RGB图像，维度为3维或4维，其中channel维度为3。  
out (OUT)：表示转换后的灰度图像，数据类型、batch_size、宽高信息与输入image保持一致，通道数channel值变为1。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_UNINITIALIZED_OBJECT：表示输入张量对象不合法。

---------

<p id="711"></p>

## 7.11 灰度图像转RGB图像
### C语法：
```c++
Status op_grayscale_to_rgb(const Tensor image,
                            Tensor *out);
```
### 参数：
image(IN)：表示待转换的灰度图像，维度为3维或4维，其中channel维度为1。  
out (OUT)：表示转换后的RGB图像，数据类型、batch_size、宽高信息与输入image保持一致，通道数channel值变为3。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_UNINITIALIZED_OBJECT：表示输入张量对象不合法。

---------

<p id="712"></p>

## 7.12 RGB图像转HSV图像
### C语法：
```c++
Status op_rgb_to_hsv(const Tensor image,
                    Tensor *out);
```
### 参数：
image(IN)：表示待转换的RGB图像，维度为3维或4维，其中channel维度为3。  
out (OUT)：表示色彩空间转换后的HSV图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_UNINITIALIZED_OBJECT：表示输入张量对象不合法。

---------

<p id="713"></p>

## 7.13 HSV图像转RGB图像
### C语法：
```c++
Status op_hsv_to_rgb(const Tensor image,
                    Tensor *out);
```
### 参数：
image(IN)：表示待转换的HSV图像，维度为3维或4维，其中channel维度为3。  
out (OUT)：表示色彩空间转换后的RGB图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_UNINITIALIZED_OBJECT：表示输入张量对象不合法。

---------

<p id="714"></p>

## 7.14 RGB图像转YUV图像
### C语法：
```c++
Status op_rgb_to_yuv(const Tensor image,
                    Tensor *out);
```
### 参数：
image(IN)：表示待转换的RGB图像，维度为3维或4维，其中channel维度为3。  
out (OUT)：表示色彩空间转换后的YUV图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_UNINITIALIZED_OBJECT：表示输入张量对象不合法。

---------

<p id="715"></p>

## 7.15 YUV图像转RGB图像
### C语法：
```c++
Status op_yuv_to_rgb(const Tensor image,
                    Tensor *out);
```
### 参数：
image(IN)：表示待转换的YUV图像，维度为3维或4维，其中channel维度为3。  
out (OUT)：表示色彩空间转换后的RGB图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_UNINITIALIZED_OBJECT：表示输入张量对象不合法。

---------

<p id="716"></p>

## 7.16 RGB图像转YIQ图像
### C语法：
```c++
Status op_rgb_to_yiq(const Tensor image,
                    Tensor *out);
```
### 参数：
image(IN)：表示待转换的RGB图像，维度为3维或4维，其中channel维度为3。  
out (OUT)：表示色彩空间转换后的YIQ图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_UNINITIALIZED_OBJECT：表示输入张量对象不合法。

---------

<p id="717"></p>

## 7.17 YIQ图像转RGB图像
### C语法：
```c++
Status op_yiq_to_rgb(const Tensor image,
                    Tensor *out);
```
### 参数：
image(IN)：表示待转换的YIQ图像，维度为3维或4维，其中channel维度为3。  
out (OUT)：表示色彩空间转换后的RGB图像，数据类型和维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_UNINITIALIZED_OBJECT：表示输入张量对象不合法。

---------

<p id="718"></p>

## 7.18 图像数据类型转换
### C语法：
```c++
Status op_convert_image_dtype(const Tensor image,
                            char *dtype,
                            Tensor *out);
```
### 参数：
image(IN)：表示待转换的图像，维度为3维或4维。  
dtype(IN)：表示目标图像的数据类型，可以为32位整数“int32”，32位浮点数“float32”或64位浮点数“float64”。  
out (OUT)：表示数据类型转换后的图像，维度信息与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。

---------

<p id="719"></p>

## 7.19 图像水平翻转
### C语法：
```c++
Status op_horizontal_flip(const Tensor image,
                        Tensor *out);
```
### 参数：
image(IN)：表示待翻转的图像，维度为3维或4维。  
out (OUT)：表示左右翻转后的图像，数据类型和维度信息与输入图像保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。

---------

<p id="720"></p>

## 7.20 图像垂直翻转
### C语法：
```c++
Status op_vertical_flip(const Tensor image,
                        Tensor *out);
```
### 参数：
image(IN)：表示待翻转的图像，维度为3维或4维。  
out (OUT)：表示上下翻转后的图像，数据类型和维度信息与输入图像保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。

---------

<p id="721"></p>

## 7.21 图像随机水平翻转
### C语法：
```c++
Status op_random_horizontal_flip(const Tensor image,
                                const float prob,
                                const int seed,
                                Tensor *out);
```
### 参数：
image(IN)：表示待翻转的图像，维度为3维或4维。  
prob(IN)：表示翻转的概率，默认值为0.5。  
seed(IN)：int32类型变量，用于生成随机种子。  
out (OUT)：表示处理后的图像，数据类型和维度信息与输入图像保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="722"></p>

## 7.22 图像随机垂直翻转
### C语法：
```c++
Status op_random_vertical_flip(const Tensor image,
                                const float prob,
                                const int seed,
                                Tensor *out);
```
### 参数：
image(IN)：表示待翻转的图像，维度为3维或4维。  
prob(IN)：表示翻转的概率，默认值为0.5。  
seed(IN)：int32类型变量，用于生成随机种子。  
out (OUT)：表示处理后的图像，数据类型和维度信息与输入图像保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="723"></p>

## 7.23 图像转置
### C语法：
```c++
Status op_image_transpose(const Tensor image,
                        Tensor *out);
```
### 参数：
image(IN)：表示待转置的图像，维度为3维或4维。  
out (OUT)：表示转置后的图像，数据类型与输入图像保持一致，输出图像宽度等于输入图像的高度，高度等于输入图像的宽度，batch_size和channels信息与输入相同。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。

---------

<p id="724"></p>

## 7.24 图像逆时针旋转90°
### C语法：
```c++
Status op_rot90(const Tensor image,
                const int k,
                Tensor *out);
```
### 参数：
image(IN)：表示待旋转的图像，维度为3维或4维。  
k(IN)：表示逆时针旋转90°的次数，数据类型为32位整数，默认值为1。  
out (OUT)：表示旋转后的图像，数据类型与输入图像保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="725"></p>

## 7.25 中心裁剪操作
### C语法：
```c++
Status op_center_crop(const Tensor image,
                    const int target_height,
                    const int target_width,
                    Tensor *out);
```
### 参数：
image(IN)：表示待裁剪的图像，维度为3维或4维。  
target_height(IN)：表示裁剪的高度，数据类型为32位整数，取值范围为(0, height]。  
target_width(IN)：表示裁剪的宽度，数据类型为32位整数，取值范围为(0, width]。  
out (OUT)：表示裁剪后得到的图像，其中batch_size和channel信息与输入image	一样，高、宽信息为裁剪后的target_height，target_width，数据类型与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="726"></p>

## 7.26 随机裁剪操作
### C语法：
```c++
Status aitisa_random_crop(const Tensor image,
                        const int target_height,
                        const int target_width,
                        Tensor *out);
```
### 参数：
image(IN)：表示待裁剪的图像，维度为3维或4维。  
target_height(IN)：表示裁剪的高度，数据类型为32位整数，取值范围为(0, height]。  
target_width(IN)：表示裁剪的宽度，数据类型为32位整数，取值范围为(0, width]。  
out (OUT)：表示裁剪后得到的图像，其中batch_size和channel信息与输入image	一样，高、宽信息为裁剪后的target_height，target_width，数据类型与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="727"></p>

## 7.27 图像裁剪操作
### C语法：
```c++
Status op_crop_to_bounding_box(const Tensor image,
                                const int offset_height,
                                const int offset_width,
                                const int target_height,
                                const int target_width,
                                Tensor *out);
```
### 参数：
image(IN)：表示待裁剪的图像，维度为3维或4维。  
offset_height(IN)：表示裁剪起始高度，32位整数，取值范围为[0, height)。  
offset_width(IN)：表示裁剪起始宽度，32位整数，取值范围为[0, width)。  
target_height(IN)：表示裁剪目标高度，32位整数，取值范围为(0, height]。  
target_height(IN)：表示裁剪目标宽度，32位整数，取值范围为(0, width]。  
out (OUT)：表示裁剪后得到的图像，其中batch_size和channel信息与输入image	一样，高、宽信息为裁剪后的target_height，target_width，数据类型与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="728"></p>

## 7.28 图像填充操作
### C语法：
```c++
Status op_pad_to_bounding_box(const Tensor image,
                            const int top,
                            const int bottom,
                            const int left,
                            const int right,
                            Tensor *out);
```
### 参数：
image(IN)：表示待填充的图像，维度为3维或4维。  
top(IN)：表示上边界填充高度，32位整数。  
bottom(IN)：表示下边界填充高度，32位整数。  
left(IN)：表示左边界填充宽度，32位整数。  
right(IN)：表示左边界填充宽度，32位整数。  
out (OUT)：表示填充后得到的图像，其中batch_size和channel信息与输入image	一样，高、宽信息为填充后的宽度和高度，数据类型与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="729"></p>

## 7.29 图像填充裁剪操作
### C语法：
```c++
Status op_resize_with_crop_or_pad(const Tensor image,
                                const int target_height,
                                const int target_width,
                                Tensor *out);
```
### 参数：
image(IN)：表示待填充的图像，维度为3维或4维。  
target_height(IN)：表示目标图像的高度，32位整数。  
target_width(IN)：表示目标图像的宽度，32位整数。  
out (OUT)：表示填充后得到的图像，其中batch_size和channel信息与输入image	一样，高、宽信息为填充后的宽度和高度，数据类型与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="730"></p>

## 7.30 图像缩放操作
### C语法：
```c++
Status op_resize(const Tensor image,
                const int target_height,
                const int target_width,
                const INTER inter_mode,
                Tensor *out);
```
### 参数：
image(IN)：表示输入图像，维度为3维或4维。  
target_size(IN)：表示目标图像高度，数据类型为32位整数。  
target_width(IN)：表示目标图像宽度，数据类型为32位整数。  
inter_mode(IN)：插值模式，INTER类型常量，包括以下4种：  
* LINEAR：双线性插值
* NEAREST：最近邻插值
* BICUBIC：双三次插值  

out (OUT)：表示调整大小后得到的图像，其中batch_size和channel信息与输入image	一样，高、宽信息为调整后的target_height，target_width，数据类型与输入image保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="731"></p>

## 7.31 图像高斯模糊
### C语法：
```c++
Status op_Gaussian_blur(const Tensor image,
                        const int kernel_size,
                        const double sigma,
                        Tensor *out);
```
### 参数：
image(IN)：表示输入图像，维度为3维或4维。  
kernel_size(IN)：表示高斯卷积核的大小，数据类型为32位整数，且需要为大于零的奇数。  
sigma(IN)：表示高斯卷积核的标准差，数据类型为32位浮点数，默认值为1.0。  
out(OUT)：表示输出图像，维度信息和数据类型与输入图像保持一致

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------

<p id="732"></p>

## 7.32 图像梯度计算
### C语法：
```c++
Status op_image_gradients(const Tensor image,
                        Tensor *grad_x,
                        Tensor *grad_y);
```
### 参数：
image(IN)：表示输入图像，维度为3维或4维。  
grad_x(OUT)：表示输入图像x方向的梯度。  
grad_y(OUT)：表示输入图像y方向的梯度。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。

---------

<p id="733"></p>

## 7.33 图像归一化
### C语法：
```c++
Status op_image_normalize(const Tensor image,
                        const double *mean,
                        const double *std,
                        Tensor *out);
```
### 参数：
image(IN)：表示待归一化的图像，维度为3维或4维。  
mean(IN)：表示图像各通道的均值，数据类型为32位浮点数，64位浮点数。  
std(IN)：表示图像各通道的方差，数据类型为32位浮点数，64位浮点数。  
out (OUT)：表示归一化后得到的图像，数据类型和维度信息与输入图像保持一致。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH：表示参数的数据类型不一致。  
STATUS_INVALID_ARGUMENT：参数设置超过合法范围。

---------