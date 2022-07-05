# C语言参考定义示例（优化器算子部分）

<p id="701"></p>

## 7.1 SGD优化器
### C语法：
```c++
Status op_sgd (const Tensor param,
                const Tensor grad, 
                const double learning_rate,
                Tensor *param_out);
```
### 参数：
param (IN)：表示待更新参数。  
grad (IN)：表示梯度张量。  
learning_rate (IN)：表示学习率。  
param_out (OUT)：更新后的参数。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH: 表示参数的数据类型不一致。

---------

<p id="702"></p>

## 7.2 Momentum优化器
### C语法：
```c++
Status op_momentum (const Tensor param,
                    const Tensor grad, 
                    const Tensor momentum,
                    const double momentum_factor,
                    const double learning_rate,
                    cont bool use_nestrov,
                    Tensor *param_out,
                    Tensor *momentum_out);
```
### 参数：
param (IN)：表示待更新参数。  
grad (IN)：表示梯度张量。  
momentum (IN)：表示动量。  
momentum_factor (IN)：表示动量因子。  
learning_rate (IN)：表示学习率。  
use_nestrov (IN)：表示是否在参数更新过程中使用赋能牛顿动量。  
param_out (OUT)：表示更新后的参数。  
momentum_out (OUT)：表示更新后的动量因子。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH: 表示参数的数据类型不一致。

---------

<p id="703"></p>

## 7.3 AdaGrad优化器
### C语法：
```c++
Status op_adagrad (const Tensor param,
                    const Tensor grad, 
                    const Tensor accum,
                    const double learning_rate,
                    Tensor *param_out,
                    Tensor *accum_out);
```
### 参数：
param (IN)：表示待更新参数。  
grad (IN)：表示梯度张量。  
accum (IN)：表示梯度平方和。  
learning_rate (IN)：表示学习率。  
param_out (OUT)：更新后的参数。  
accum_out (OUT)：表示更新后的梯度平方和。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH: 表示参数的数据类型不一致。

---------

<p id="704"></p>

## 7.4 AdaDelta优化器
### C语法：
```c++
Status op_adadelta (const Tensor param,
                    const Tensor grad, 
                    const Tensor mean_square,
                    const double alpha,
                    const Tensor accum_update,
                    const double learning_rate,
                    const double epsilon,
                    Tensor *param_out,
                    Tensor *mean_square_out,
                    Tensor * accum_update_out);
```
### 参数：
param (IN)：表示待更新参数。  
grad (IN)：表示梯度张量。  
mean_square (IN)：表示梯度均方。  
alpha (IN)：表示衰减率。  
accum_update(IN): 表示参数更新量均方。  
learning_rate (IN)：表示学习率。  
epsilon (IN)：表示平滑项。  
param_out (OUT)：更新后的参数。  
mean_square_out (OUT)：表示更新后的梯度均方。  
accum_update_out (OUT)：表示更新后的参数更新量均方。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH: 表示参数的数据类型不一致。

---------

<p id="705"></p>

## 7.5 RMSProp优化器
### C语法：
```c++
Status op_rmsprop (const Tensor param,
                    const Tensor grad, 
                    const Tensor mean_square,
                    const Tensor momentum,
                    const double momentum_factor,
                    const double alpha,
                    const double learning_rate,
                    const double epsilon,
                    Tensor *param_out,
                    Tensor *mean_square_out,
                    Tensor *momentum_out);
```
### 参数：
param (IN)：表示待更新参数。  
grad (IN)：表示梯度张量。  
mean_square (IN)：表示梯度均方。  
momentum (IN)：表示动量。  
momentum_factor (IN)：表示动量因子。  
alpha (IN)：表示衰减率。  
learning_rate (IN)：表示学习率。  
epsilon (IN)：表示平滑项。  
param_out (OUT)：更新后的参数。  
mean_square_out (OUT)：表示更新后的梯度均方。  
momentum_out (OUT)：表示更新后的动量因子。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH: 表示参数的数据类型不一致。

---------

<p id="706"></p>

## 7.6 CenteredRMSProp优化器
### C语法：
```c++
Status op_centered_rmsprop (const Tensor param,
                            const Tensor grad,
                            const Tensor mean_grad, 
                            const Tensor mean_square,
                            const Tensor momentum,
                            const double momentum_factor,
                            const double alpha,
                            const double learning_rate,
                            const double epsilon,
                            Tensor *param_out,
                            Tensor *mean_grad_out,
                            Tensor *mean_square_out,
                            Tensor *momentum_out);
```
### 参数：
param (IN)：表示待更新参数。  
grad (IN)：表示梯度张量。  
mean_grad (IN)：表示平均梯度。  
mean_square (IN)：表示梯度均方。  
momentum (IN)：表示动量。  
momentum_factor (IN)：表示动量因子。  
alpha (IN)：表示衰减率。  
learning_rate (IN)：表示学习率。  
epsilon (IN)：表示平滑项。  
param_out (OUT)：更新后的参数。  
mean_grad_out (OUT)：表示更新后的平均梯度。  
mean_square_out (OUT)：表示更新后的梯度均方。  
momentum_out (OUT)：表示更新后的动量。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH: 表示参数的数据类型不一致。

---------

<p id="707"></p>

## 7.7 Adam优化器
### C语法：
```c++
Status op_adam (const Tensor param,
                const Tensor grad, 
                const Tensor m,
                const Tensor v,
                const double beta1,
                const double beta2,
                const double beta1_power,
                const double beta2_power,
                const double learning_rate,
                const double epsilon,
                Tensor *param_out,
                Tensor *m_out,
                Tensor *v_out);
```
### 参数：
param (IN)：表示待更新参数。  
grad (IN)：表示梯度张量。  
m (IN)：表示训练过程中累加的动量一。  
v (IN)：表示训练过程中累加的动量二。  
beta1 (IN)：表示计算动量一时的衰减率。  
beta2 (IN)：表示计算动量二时的衰减率。  
beta1_power (IN)：表示衰减率一的幂。  
beta2_power (IN)：表示衰减率二的幂。  
learning_rate (IN)：表示学习率。  
epsilon (IN)：表示平滑项。  
param_out (OUT)：更新后的参数。  
m_out (OUT)：表示更新后的动量一。  
v_out (OUT)：表示更新后的动量二。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_TYPE_MISMATCH: 表示参数的数据类型不一致。

---------

<p id="708"></p>

## 7.8 AdaMax优化器
### C语法：
```c++
Status op_adamax (const Tensor param,
                    const Tensor grad,
                    const Tensor mean_grad, 
                    const double alpha,
                    const double alpha_power,
                    const double beta,
                    const Tensor grad_max,
                    const double learning_rate,
                    const double epsilon,
                    Tensor *param_out,
                    Tensor *mean_grad_out,
                    Tensor *grad_max_out);
```
### 参数：
param (IN)：表示待更新参数。  
grad (IN)：表示梯度张量。  
mean_grad (IN)：表示平均梯度。  
alpha (IN)：表示计算平均梯度时使用的衰减率。  
alpha_power (IN)：表示计算平均梯度时使用的衰减率的幂。  
beta (IN)：表示计算梯度最大值时使用的衰减率。  
grad_max (IN)：表示梯度最大值。  
learning_rate (IN)：表示学习率。  
epsilon (IN)：表示平滑项。  
param_out (OUT)：更新后的参数。  
mean_grad_out (OUT)：表示更新后的平均梯度。  
grad_max_out (OUT)：表示更新后的梯度最大值。

### 返回值：
STATUS_SUCCESS：表示操作成功。
STATUS_TYPE_MISMATCH: 表示参数的数据类型不一致。

---------