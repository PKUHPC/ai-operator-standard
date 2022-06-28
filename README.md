# ai-operator-standard

## 优化器算子接口
框架版本：
* Tensorflow：2.9.0
* PyTorch：1.11.0
<!-- * MindSpore：xxx -->
<!-- * Paddle：xxx -->

| 算子             | TensorFlow                                                                                                                    | PyTorch                                                                                                                           | MindSpore | Paddle |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | --------- | ------ |
| sgd              | [tf.keras.optimizers.SGD](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/keras/optimizers/SGD)                 | [torch.optim.SGD](https://pytorch.org/docs/1.11/generated/torch.optim.SGD.html?highlight=sgd#torch.optim.SGD)                     |           |        |
| momentum         | [tf.keras.optimizers.SGD](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/keras/optimizers/SGD)                 | [torch.optim.SGD](https://pytorch.org/docs/1.11/generated/torch.optim.SGD.html?highlight=sgd#torch.optim.SGD)                     |           |        |
| adagrad          | [tf.keras.optimizers.Adagrad](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/keras/optimizers/Adagrad)         | [torch.optim.Adagrad](https://pytorch.org/docs/1.11/generated/torch.optim.Adagrad.html?highlight=adagrad#torch.optim.Adagrad)     |           |        |
| adadelta         | [tf.keras.optimizers.Adadelta](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/keras/optimizers/Adadelta)       | [torch.optim.Adadelta](https://pytorch.org/docs/1.11/generated/torch.optim.Adadelta.html?highlight=adadelta#torch.optim.Adadelta) |           |        |
| rmsprop          | [tf.keras.optimizers.RMSprop](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/keras/optimizers/RMSprop)         | [torch.optim.RMSprop](https://pytorch.org/docs/1.11/generated/torch.optim.RMSprop.html?highlight=rmspro#torch.optim.RMSprop)      |           |        |
| centered_rmsprop | [tf.raw_ops.ApplyCenteredRMSProp](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/raw_ops/ApplyCenteredRMSProp) | /                                                                                                                                 |           |        |
| adam             | [tf.keras.optimizers.Adam](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/keras/optimizers/Adam)               | [torch.optim.Adam](https://pytorch.org/docs/1.11/generated/torch.optim.Adam.html?highlight=adam#torch.optim.Adam)                 |           |        |
| adamax           | [tf.keras.optimizers.Adamax](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/keras/optimizers/Adamax)           | [torch.optim.Adamax](https://pytorch.org/docs/1.11/generated/torch.optim.Adamax.html?highlight=adamax#torch.optim.Adamax)         |           |        |

-----------
## 图像处理算子接口

框架版本：
* Tensorflow：2.9.0
* PyTorch：1.11.0
* torchvision：0.12
<!-- * MindSpore：xxx -->
<!-- * Paddle：xxx -->

| 算子                    | TensorFlow                                                                                                                      | PyTorch                                                                                                                                                                                                                             | MindSpore | Paddle |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | ------ |
| adjust_brightness       | [tf.image.adjust_brightness](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/adjust_brightness)             | [torchvision.transforms.functional.adjust_brightness](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.adjust_brightness.html?highlight=brightness#torchvision.transforms.functional.adjust_brightness)  |           |        |
| adjust_contrast         | [tf.image.adjust_contrast](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/adjust_contrast)                 | [torchvision.transforms.functional.adjust_contrast](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.adjust_contrast.html?highlight=contras#torchvision.transforms.functional.adjust_contrast)           |           |        |
| adjust_gamma            | [tf.image.adjust_gamma](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/adjust_gamma)                       | [torchvision.transforms.functional.adjust_gamma](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.adjust_gamma.html?highlight=gamma#torchvision.transforms.functional.adjust_gamma)                      |           |        |
| adjust_hue              | [tf.image.adjust_hue](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/adjust_hue)                           | [torchvision.transforms.functional.adjust_hue](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.adjust_hue.html?highlight=hue#torchvision.transforms.functional.adjust_hue)                              |           |        |
| adjust_saturation       | [tf.image.adjust_saturation](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/adjust_saturation)             | [torchvision.transforms.functional.adjust_saturation](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.adjust_saturation.html?highlight=satura#torchvision.transforms.functional.adjust_saturation)      |           |        |
| random_brightness       | [tf.image.random_brightness](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/random_brightness)             | /                                                                                                                                                                                                                                   |           |        |
| random_contrast         | [tf.image.random_contrast](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/random_contrast)                 | /                                                                                                                                                                                                                                   |           |        |
| random_hue              | [tf.image.random_hue](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/random_hue)                           | /                                                                                                                                                                                                                                   |           |        |
| random_saturation       | [tf.image.random_saturation](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/random_saturation)             | /                                                                                                                                                                                                                                   |           |        |
| rgb_to_grayscale        | [tf.image.rgb_to_grayscale](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/rgb_to_grayscale)               | [torchvision.transforms.functional.rgb_to_grayscale](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.rgb_to_grayscale.html?highlight=rgb#torchvision.transforms.functional.rgb_to_grayscale)            |           |        |
| grayscale_to_rgb        | [tf.image.grayscale_to_rgb](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/grayscale_to_rgb)               | /                                                                                                                                                                                                                                   |           |        |
| rgb_to_hsv              | [tf.image.rgb_to_hsv](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/rgb_to_hsv)                           | /                                                                                                                                                                                                                                   |           |        |
| hsv_to_rgb              | [tf.image.hsv_to_rgb](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/hsv_to_rgb)                           | /                                                                                                                                                                                                                                   |           |        |
| rgb_to_yuv              | [tf.image.rgb_to_yuv](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/rgb_to_yuv)                           | /                                                                                                                                                                                                                                   |           |        |
| yuv_to_rgb              | [tf.image.yuv_to_rgb](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/yuv_to_rgb)                           | /                                                                                                                                                                                                                                   |           |        |
| rgb_to_yiq              | [tf.image.rgb_to_yiq](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/rgb_to_yiq)                           | /                                                                                                                                                                                                                                   |           |        |
| yiq_to_rgb              | [tf.image.yiq_to_rgb](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/yiq_to_rgb)                           | /                                                                                                                                                                                                                                   |           |        |
| convert_image_dtype     | [tf.image.convert_image_dtype](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/convert_image_dtype)         | [torchvision.transforms.functional.convert_image_dtype](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.convert_image_dtype.html?highlight=dtype#torchvision.transforms.functional.convert_image_dtype) |           |        |
| horizontal_flip         | [tf.image.flip_left_right](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/flip_left_right)                 | [torchvision.transforms.functional.hflip](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.hflip.html?highlight=flip#torchvision.transforms.functional.hflip)                                            |           |        |
| vertical_flip           | [tf.image.flip_up_down](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/flip_up_down)                       | [torchvision.transforms.functional.vflip](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.vflip.html?highlight=flip#torchvision.transforms.functional.vflip)                                            |           |        |
| random_horizontal_flip  | [tf.image.random_flip_left_right](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/random_flip_left_right)   | [torchvision.transforms.RandomHorizontalFlip](https://pytorch.org/vision/0.12/generated/torchvision.transforms.RandomHorizontalFlip.html?highlight=flip#torchvision.transforms.RandomHorizontalFlip)                                |           |        |
| random_vertical_flip    | [tf.image.random_flip_up_down](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/random_flip_up_down)         | [torchvision.transforms.RandomVerticalFlip](https://pytorch.org/vision/0.12/generated/torchvision.transforms.RandomVerticalFlip.html?highlight=flip#torchvision.transforms.RandomVerticalFlip)                                      |           |        |
| image_transpose         | [tf.image.transpose](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/transpose)                             | [torch.transpose](https://pytorch.org/docs/1.11/generated/torch.transpose.html#torch.transpose)                                                                                                                                     |           |        |
| rot90                   | [tf.image.rot90](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/rot90)                                     | [torch.rot90](https://pytorch.org/docs/1.11/generated/torch.rot90.html?highlight=rot#torch.rot90)                                                                                                                                   |           |        |
| center_crop             | [tf.image.central_crop](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/central_crop)                       | [torchvision.transforms.CenterCrop](https://pytorch.org/vision/0.12/generated/torchvision.transforms.CenterCrop.html?highlight=crop#torchvision.transforms.CenterCrop)                                                              |           |        |
| random_crop             | [tf.image.random_crop](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/random_crop)                         | [torchvision.transforms.RandomCrop](https://pytorch.org/vision/0.12/generated/torchvision.transforms.RandomCrop.html?highlight=random%20crop#torchvision.transforms.RandomCrop)                                                     |           |        |
| crop_to_bounding_box    | [tf.image.crop_to_bounding_box](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/crop_to_bounding_box)       | /                                                                                                                                                                                                                                   |           |        |
| pad_to_bounding_box     | [tf.image.pad_to_bounding_box](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/pad_to_bounding_box)         | /                                                                                                                                                                                                                                   |           |        |
| pad_to_bounding_box     | [tf.image.pad_to_bounding_box](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/pad_to_bounding_box)         | [torchvision.transforms.Pad](https://pytorch.org/vision/0.12/generated/torchvision.transforms.Pad.html?highlight=pad#torchvision.transforms.Pad)                                                                                    |           |        |
| resize_with_crop_or_pad | [tf.image.resize_with_crop_or_pad](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/resize_with_crop_or_pad) | [torchvision.transforms.functional.resized_crop](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.resized_crop.html?highlight=resize#torchvision.transforms.functional.resized_crop)                     |           |        |
| resize                  | [tf.image.resize](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/resize)                                   | [torchvision.transforms.functional.resize](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.resize.html?highlight=resize#torchvision.transforms.functional.resize)                                       |           |        |
| Gaussian_blur           | /                                                                                                                               | [torchvision.transforms.functional.gaussian_blur](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.gaussian_blur.html?highlight=gauss#torchvision.transforms.functional.gaussian_blur)                   |           |        |
| image_gradients         | [tf.image.image_gradients](https://tensorflow.google.cn/versions/r2.9/api_docs/python/tf/image/image_gradients)                 | /                                                                                                                                                                                                                                   |           |        |
| image_normalize         | /                                                                                                                               | [torchvision.transforms.functional.normalize](https://pytorch.org/vision/0.12/generated/torchvision.transforms.functional.normalize.html?highlight=normalize#torchvision.transforms.functional.normalize)                           |           |        |

-----------
## 分布式训练算子接口

框架版本：
* Tensorflow：2.9.0
* PyTorch：1.11.0
<!-- * MindSpore：xxx -->
<!-- * Paddle：xxx -->

| 算子                      | TensorFlow | PyTorch | MindSpore | Paddle |
| ------------------------- | ---------- | ------- | --------- | ------ |
| comm_init                 | []()       | []()    |           |        |
| comm_create_by_ranks      | []()       | []()    |           |        |
| comm_dup                  | []()       | []()    |           |        |
| comm_destroy              | []()       | []()    |           |        |
| comm_get_size             | []()       | []()    |           |        |
| comm_get_rank             | []()       | []()    |           |        |
| get_async_op_status       | []()       | []()    |           |        |
| wait                      | []()       | []()    |           |        |
| send                      | []()       | []()    |           |        |
| recv                      | []()       | []()    |           |        |
| broadcast                 | []()       | []()    |           |        |
| all_reduce                | []()       | []()    |           |        |
| comm_reduce               | []()       | []()    |           |        |
| all_gather                | []()       | []()    |           |        |
| comm_gather               | []()       | []()    |           |        |
| comm_scatter              | []()       | []()    |           |        |
| comm_reduce_scatter       | []()       | []()    |           |        |
| comm_all_to_all           | []()       | []()    |           |        |
| comm_barrier              | []()       | []()    |           |        |
| comm_send_async           | []()       | []()    |           |        |
| comm_recv_async           | []()       | []()    |           |        |
| comm_broadcast_async      | []()       | []()    |           |        |
| comm_all_reduce_async     | []()       | []()    |           |        |
| comm_reduce_async         | []()       | []()    |           |        |
| comm_all_gather_async     | []()       | []()    |           |        |
| comm_gather_async         | []()       | []()    |           |        |
| comm_scatter_async        | []()       | []()    |           |        |
| comm_reduce_scatter_async | []()       | []()    |           |        |
| comm_all_to_all_async     | []()       | []()    |           |        |
| comm_barrier_async        | []()       | []()    |           |        |