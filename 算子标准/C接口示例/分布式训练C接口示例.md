# C语言参考定义示例（图像算子部分）

<p id="701"></p>

## 7.1 创建初始通信器
### C语法：
```c++
Status op_comm_init (const char *comm_lib,
                    const int world_size,
                    const int rank, 
                    const char *root,
                    Communicator *comm);
```
### 参数：
comm_lib (IN)：表示后端通信库类型，例如NCCL、GLOO、MPI等等。  
world_size (IN)：正整数，表示参与通信的进程数量。  
rank (IN)：非负整数，表示当前进程的进程号，应当大于或等于0，且小于world_size。在参与通信的进程间唯一。  
root (IN)：表示根进程的统一资源标识符。根进程（即进程号等于0的进程）以外的进程通过该标识符与根进程通信，并进一步获取与其他进程通信所需的信息。该标识符的形式可以是TCP/UDP端口，共享文件系统中的文件等等。  
comm (OUT)：表示所创建的通信器。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_LIB_NOT_EXIST：表示通信库类型不存在。  
STATUS_INVAID_ROOT：表示根进程标志的格式不合法。  
STATUS_ACCESS_ROOT_FAILED：表示无法根据根进程标志与根进程通信。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="702"></p>

## 7.2 根据进程号数组创建通信器
### C语法：
```c++
Status op_comm_create_by_ranks (const Communicator comm,
                                const int *ranks,
                                const int n_ranks, 
                                Communicator *new_comm);
```
### 参数：
comm (IN)：表示原通信器。  
color(IN)：表示当前进程的颜色，颜色相同的进程会被归属到同一个新的通信器中。  
key (IN)：表示排序键，新的通信器将根据该参数升序排列来确定进程在新通信器中的进程号，排序键相同的进程则根据其在原通信器中的进程号大小升序排列。  
new_comm (OUT)：表示所创建的新通信器。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="703"></p>

## 7.3 复制通信器
### C语法：
```c++
Status op_comm_dup (const Communicator comm,
                    Communicator *new_comm);
```
### 参数：
comm (IN)：表示原通信器。  
new_comm (OUT)：表示所创建的新通信器。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="704"></p>

## 7.4 销毁通信器
### C语法：
```c++
Status op_comm_destroy (const Communicator comm);
```
### 参数：
comm (IN)：表示待销毁的通信器。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="705"></p>

## 7.5 查询进程数量
### C语法：
```c++
Status op_comm_get_size (const Communicator comm,
                        int *n_processes);
```
### 参数：
comm (IN)：表示要查询的通信器。  
n_processes (OUT)：表示所查询的通信器中进程的数量。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="706"></p>

## 7.6 查询当前进程的进程号
### C语法：
```c++
Status op_comm_get_rank (const Communicator comm,
                        int *rank);
```
### 参数：
comm (IN)：表示要查询的通信器。  
rank (OUT)：表示当前进程的进程号。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="707"></p>

## 7.7 查询异步操作的完成状态
### C语法：
```c++
Status op_ get_async_op_status (const AsyncOp op,
                                AsyncOpStatus *status);
```
### 参数：
op (IN)：表示要查询的异步操作。  
status (OUT)：所查询的异步操作的完成状态，其是枚举类型变量，具体定义为
```c++
typedef enum _async_op_status {  
    IN_PROGRESS,  
    COMPLETED,  
    ERROR  
} AsyncOpStatus;
```
### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="708"></p>

## 7.8 等待异步操作完成
### C语法：
```c++
Status op_wait (const AsyncOp op);
```
### 参数：
op (IN)：表示要等待的异步操作。
### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="709"></p>

## 7.9 发送
### C语法：
```c++
Status op_comm_send (const Communicator comm,
                    const Tensor input,
                    const int dst_rank, 
                    const int tag);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要发送的张量。  
dst_rank (IN)：表示接收进程的进程号。  
tag (IN)：表示附带的数据匹配标签值，必须为非负整数。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="710"></p>

## 7.10 创建初始通信器
### C语法：
```c++
Status op_comm_recv (const Communicator comm,
                    const int src_rank,
                    const int tag,
                    Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
dst_rank (IN)：表示发送进程的进程号。  
tag (IN)：表示附带的数据匹配标签值，必须为非负整数或-1；为-1时表示接收带有任何标签的数据，为非负整数时表示仅接收带有相同标签的数据。  
output (OUT)：表示接收到的张量。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="711"></p>

## 7.11 广播
### C语法：
```c++
Status op_comm_broadcast (const Communicator comm,
                        const Tensor input,
                        const int src_rank, 
                        Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要发送的张量。  
src_rank (IN)：表示发送进程的进程号。  
output (OUT)：表示接收到的张量，发送进程的该参数会被忽略。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [[1, 2, 3, 4],
 *    [5, 6, 7, 8]]
 */

op_comm_broadcast (comm, input, 0, output);
/* output(rank=0): 
 *   [[1, 2, 3, 4],
 *    [5, 6, 7, 8]]
 */

/* output(rank=1): 
 *   [[1, 2, 3, 4],
 *    [5, 6, 7, 8]]
 */

/* output(rank=2): 
 *   [[1, 2, 3, 4],
 *    [5, 6, 7, 8]]
 */
```
---------

<p id="712"></p>

## 7.12 全局规约
### C语法：
```c++
Status op_comm_all_reduce (const Communicator comm,
                        const Tensor input,
                        const CommReduceMode mode,
                        Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行规约的张量。  
mode(IN)：表示进行规约时使用的操作类型。其定义为：  
```c++
enum CommReduceMode {
  SUM,      //求和规约
  PROD,     // 乘积规约
  MAX,      //求最大规约
  MIN,      //求最小规约
  BAND,     // 位与
  BOR,      // 位或
  BXOR,     // 位异或
};
```
output (OUT)：表示规约后得到的张量。
### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [1, 5, 7, 2]
 */
/* input(rank=1): 
 *   [4, 0, 3, 3]
 */
/* input(rank=2): 
 *   [6, 2, 9, 1]
 */
op_comm_all_reduce (comm, input, SUM, output);
/* output(rank=0): 
 *   [11, 7, 19, 6]
 */

/* output(rank=1): 
 *   [11, 7, 19, 6]
 */

/* output(rank=2): 
 *   [11, 7, 19, 6]
 */
```

---------

<p id="713"></p>

## 7.13 规约
### C语法：
```c++
Status op_comm_reduce (const Communicator comm,
                        const Tensor input,
                        const CommReduceMode mode,
                        const int dst_rank,
                        Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行规约的张量。  
mode(IN)：表示进行规约时使用的操作类型。其定义为：  
```c++
enum CommReduceMode {
  SUM,      //求和规约
  PROD,     // 乘积规约
  MAX,      //求最大规约
  MIN,      //求最小规约
  BAND,     // 位与
  BOR,      // 位或
  BXOR,     // 位异或
};
```
dst_rank (IN)：表示接收结果的进程的进程号。  
output (OUT)：表示规约后得到的张量。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [1, 5, 7, 2]
 */
/* input(rank=1): 
 *   [4, 0, 3, 3]
 */
/* input(rank=2): 
 *   [6, 2, 9, 1]
 */
op_comm_reduce (comm, input, SUM, 1, output);
/* output(rank=0): 
 *   NULL
 */

/* output(rank=1): 
 *   [11, 7, 19, 6]
 */

/* output(rank=2): 
 *   NULL
 */
```
---------

<p id="714"></p>

## 7.14 全局聚集
### C语法：
```c++
Status op_comm_all_gather (const Communicator comm,
                        const Tensor input,
                        Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行聚集的张量。  
output (OUT)：表示聚集得到的张量。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [1, 5, 7, 2]
 */
/* input(rank=1): 
 *   [4, 0, 3, 3]
 */
/* input(rank=2): 
 *   [6, 2, 9, 1]
 */
op_comm_all_gather (comm, input, output);
/* output(rank=0): 
 *   [[1, 5, 7, 2],
 *    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
 */

/* output(rank=1): 
 *   [[1, 5, 7, 2],
 *    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
 */

/* output(rank=2): 
 *   [[1, 5, 7, 2],
 *    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
 */
```

---------

<p id="715"></p>

## 7.15 聚集
### C语法：
```c++
Status op_comm_gather (const Communicator comm,
                    const Tensor input,
                    const int dst_rank,
                    Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行聚集的张量。  
dst_rank (IN)：表示接收结果的进程号。  
output (OUT)：表示聚集得到的张量。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [1, 5, 7, 2]
 */
/* input(rank=1): 
 *   [4, 0, 3, 3]
 */
/* input(rank=2): 
 *   [6, 2, 9, 1]
 */
op_comm_gather (comm, input, 1, output);
/* output(rank=0): 
 *   NULL
 */

/* output(rank=1): 
 *   [[1, 5, 7, 2],
 *    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
 */

/* output(rank=2): 
 *   NULL
 */
```
---------

<p id="716"></p>

## 7.16 分散
### C语法：
```c++
Status op_comm_scatter (const Communicator comm,
                        const Tensor input,
                        const int src_rank,
                        Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行分散的张量。  
src_rank (IN)：表示分发张量的进程的进程号。  
output (OUT)：分发后各进程接收到的张量。  

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
*   NULL
*/
/* input(rank=1): 
*   [[1, 5, 7, 2],
*    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
*/
/* input(rank=2): 
 *   NULL
 */

op_comm_scatter (comm, input, 1, output);
/* output(rank=0): 
 *   [1, 5, 7, 2]
 */
/* output(rank=1): 
 *   [4, 0, 3, 3]
 */
/* output(rank=2): 
 *   [6, 2, 9, 1]
 */
```
---------

<p id="717"></p>

## 7.17 规约分散
### C语法：
```c++
Status op_comm_reduce_scatter (const Communicator comm,
                                const Tensor input,
                                const CommReduceMode mode,
                                Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行规约分散的张量。  
mode (IN)：表示进行规约时使用的操作类型。其定义为：  
```c++
enum CommReduceMode {
  SUM,      //求和规约
  PROD,     // 乘积规约
  MAX,      //求最大规约
  MIN,      //求最小规约
  BAND,     // 位与
  BOR,      // 位或
  BXOR,     // 位异或
};
```
output (OUT)：表示规约分散后得到的张量。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [[1, 5],[8,1],[3,2]]
 */
/* input(rank=1): 
 *   [[2, 7],[3,3],[0,7]]
 */
/* input(rank=3): 
 *   [[3, 0],[2,1],[6,4]]
 */
op_comm_reduce_scatter (comm, input, SUM, output);
/* output(rank=0): 
 *   [6, 12]
 */

/* output(rank=1): 
 *   [13, 5]
 */

/* output(rank=2): 
 *   [9, 13]
 */
```
---------

<p id="718"></p>

## 7.18 所有对所有
### C语法：
```c++
Status op_comm_all_to_all (const Communicator comm,
                            const Tensor input,
                            Tensor *output);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要发送的张量。  
output (OUT)：表示接收到的张量。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [9,8,6]
 */
/* input(rank=1): 
 *   [1,5,7]
 */
/* input(rank=3): 
*   [0,4,0]
*/
op_comm_all_to_all (comm, input, output);
/* output(rank=0): 
*   [9,1,0]
*/

/* output(rank=1): 
*   [8,5,4]
*/

/* output(rank=2): 
*   [6,7,0]
*/
```
---------

<p id="719"></p>

## 7.19 屏障
### C语法：
```c++
Status op_comm_barrier (const Communicator comm);
```
### 参数：
comm (IN)：表示所使用的通信器。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="720"></p>

## 7.20 异步发送
### C语法：
```c++
Status op_comm_send_async (const Communicator comm,
                            const Tensor input,
                            const int dst_rank, 
                            const int tag,
                            AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要发送的张量。  
dst_rank (IN)：表示接收进程的进程号。  
tag (IN)：表示附带的数据匹配标签值，必须为非负整数。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="721"></p>

## 7.21 异步接收
### C语法：
```c++
Status op_comm_recv_async (const Communicator comm,
                            const int src_rank,
                            const int tag,
                            Tensor *output,
                            AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
dst_rank (IN)：表示发送进程的进程号。  
tag (IN)：表示附带的数据匹配标签值，必须为非负整数或-1；为-1时表示接收带有任何标签的数据，为非负整数时表示仅接收带有相同标签的数据。  
output (OUT)：表示接收到的张量。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值： 
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------

<p id="722"></p>

## 7.22 异步广播
### C语法：
```c++
Status op_comm_broadcast_async (const Communicator comm,
                                const Tensor input,
                                const int src_rank, 
                                Tensor *output,
                                AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要发送的张量。  
src_rank (IN)：表示发送进程的进程号。  
output (OUT)：表示接收到的张量，发送进程的该参数会被忽略。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [[1, 2, 3, 4],
 *    [5, 6, 7, 8]]
 */

op_comm_broadcast_async (comm, input, 0, output);
/* output(rank=0): 
 *   [[1, 2, 3, 4],
 *    [5, 6, 7, 8]]
 */

/* output(rank=1): 
 *   [[1, 2, 3, 4],
 *    [5, 6, 7, 8]]
 */

/* output(rank=2): 
 *   [[1, 2, 3, 4],
 *    [5, 6, 7, 8]]
 */
```
---------

<p id="723"></p>

## 7.23 异步全局规约
### C语法：
```c++
Status op_comm_all_reduce_async (const Communicator comm,
                                const Tensor input,
                                const CommReduceMode mode,
                                Tensor *output,
                                AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行规约的张量。  
mode(IN)：表示进行规约时使用的操作类型。其定义为：  
```c++
enum CommReduceMode {
  SUM,      //求和规约
  PROD,     // 乘积规约
  MAX,      //求最大规约
  MIN,      //求最小规约
  BAND,     // 位与
  BOR,      // 位或
  BXOR,     // 位异或
};
```
output (OUT)：表示规约后得到的张量。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [1, 5, 7, 2]
 */
/* input(rank=1): 
 *   [4, 0, 3, 3]
 */
/* input(rank=2): 
 *   [6, 2, 9, 1]
 */
op_comm_all_reduce_async (comm, input, SUM, output);
/* output(rank=0): 
 *   [11, 7, 19, 6]
 */

/* output(rank=1): 
 *   [11, 7, 19, 6]
 */

/* output(rank=2): 
 *   [11, 7, 19, 6]
 */
```
---------

<p id="724"></p>

## 7.24 异步规约
### C语法：
```c++
Status op_comm_reduce_async (const Communicator comm,
                            const Tensor input,
                            const CommReduceMode mode,
                            const int dst_rank,
                            Tensor *output,
                            AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行规约的张量。  
mode(IN)：表示进行规约时使用的操作类型。其定义为：  
```c++
enum CommReduceMode {
  SUM,      //求和规约
  PROD,     // 乘积规约
  MAX,      //求最大规约
  MIN,      //求最小规约
  BAND,     // 位与
  BOR,      // 位或
  BXOR,     // 位异或
};
```
dst_rank (IN)：表示接收结果的进程的进程号。  
output (OUT)：表示规约后得到的张量。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [1, 5, 7, 2]
 */
/* input(rank=1): 
 *   [4, 0, 3, 3]
 */
/* input(rank=2): 
 *   [6, 2, 9, 1]
 */
op_comm_reduce_async (comm, input, SUM, 1, output);
/* output(rank=0): 
 *   NULL
 */

/* output(rank=1): 
 *   [11, 7, 19, 6]
 */

/* output(rank=2): 
 *   NULL
 */
```
---------

<p id="725"></p>

## 7.25 异步全局聚集
### C语法：
```c++
Status op_comm_all_gather_async (const Communicator comm,
                                const Tensor input,
                                Tensor *output,
                                AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行聚集的张量。  
output (OUT)：表示聚集得到的张量。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [1, 5, 7, 2]
 */
/* input(rank=1): 
 *   [4, 0, 3, 3]
 */
/* input(rank=2): 
 *   [6, 2, 9, 1]
 */
op_comm_all_gather_async (comm, input, output);
/* output(rank=0): 
 *   [[1, 5, 7, 2],
 *    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
 */

/* output(rank=1): 
 *   [[1, 5, 7, 2],
 *    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
 */

/* output(rank=2): 
 *   [[1, 5, 7, 2],
 *    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
 */
```
---------

<p id="726"></p>

## 7.26 异步聚集
### C语法：
```c++
Status op_comm_gather_async (const Communicator comm,
                            const Tensor input,
                            const int dst_rank,
                            Tensor *output,
                            AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行聚集的张量。  
dst_rank (IN)：表示接收结果的进程号。  
output (OUT)：表示聚集得到的张量。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [1, 5, 7, 2]
 */
/* input(rank=1): 
 *   [4, 0, 3, 3]
 */
/* input(rank=2): 
 *   [6, 2, 9, 1]
 */
op_comm_gather_async (comm, input, 1, output);
/* output(rank=0): 
 *   NULL
 */

/* output(rank=1): 
 *   [[1, 5, 7, 2],
 *    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
 */

/* output(rank=2): 
 *   NULL
 */
```
---------

<p id="727"></p>

## 7.27 异步分散
### C语法：
```c++
Status op_comm_scatter_async (const Communicator comm,
                            const Tensor input,
                            const int src_rank,
                            Tensor *output,
                            AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行分散的张量。  
src_rank (IN)：表示分发张量的进程的进程号。  
output (OUT)：分发后各进程接收到的张量。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_RANK_ NOT_EXIST：表示进程号不存在于通信器中。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
*   NULL
*/
/* input(rank=1): 
*   [[1, 5, 7, 2],
*    [4, 0, 3, 3]
*    [6, 2, 9, 1]]
*/
/* input(rank=2): 
 *   NULL
 */

op_comm_scatter_async (comm, input, 1, output);
/* output(rank=0): 
 *   [1, 5, 7, 2]
 */
/* output(rank=1): 
 *   [4, 0, 3, 3]
 */
/* output(rank=2): 
 *   [6, 2, 9, 1]
 */
```
---------

<p id="728"></p>

## 7.28 异步规约分散
### C语法：
```c++
Status op_comm_reduce_scatter_async (const Communicator comm,
                                    const Tensor input,
                                    const CommReduceMode mode,
                                    Tensor *output,
                                    AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要进行规约分散的张量。  
mode (IN)：表示进行规约时使用的操作类型。其定义为：  
```c++
enum CommReduceMode {
  SUM,      //求和规约
  PROD,     // 乘积规约
  MAX,      //求最大规约
  MIN,      //求最小规约
  BAND,     // 位与
  BOR,      // 位或
  BXOR,     // 位异或
};
```
output (OUT)：表示规约分散后得到的张量。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [[1, 5],[8,1],[3,2]]
 */
/* input(rank=1): 
 *   [[2, 7],[3,3],[0,7]]
 */
/* input(rank=3): 
 *   [[3, 0],[2,1],[6,4]]
 */
op_comm_reduce_scatter_async (comm, input, SUM, output);
/* output(rank=0): 
 *   [6, 12]
 */

/* output(rank=1): 
 *   [13, 5]
 */

/* output(rank=2): 
 *   [9, 13]
 */
```
---------

<p id="729"></p>

## 7.29 异步所有对所有
### C语法：
```c++
Status op_comm_all_to_all_async (const Communicator comm,
                                const Tensor input,
                                Tensor *output,
                                AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
input (IN)：表示需要发送的张量。  
output (OUT)：表示接收到的张量。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INVALID_ARGUMENT：表示其他参数不合法。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

### 示例：
假设共有3个进程参与通信。
```c++
/* input(rank=0): 
 *   [9,8,6]
 */
/* input(rank=1): 
 *   [1,5,7]
 */
/* input(rank=3): 
*   [0,4,0]
*/
op_comm_all_to_all_async (comm, input, output);
/* output(rank=0): 
*   [9,1,0]
*/

/* output(rank=1): 
*   [8,5,4]
*/

/* output(rank=2): 
*   [6,7,0]
*/
```
---------

<p id="730"></p>

## 7.30 异步屏障
### C语法：
```c++
Status op_comm_barrier_async (const Communicator comm,
                            AsyncOp *op);
```
### 参数：
comm (IN)：表示所使用的通信器。  
op (OUT)：表示本次的异步操作，用于后续查询操作的完成状态，或者等待操作完成等。

### 返回值：
STATUS_SUCCESS：表示操作成功。  
STATUS_COMM_ NOT_EXIST：表示通信器不存在。  
STATUS_INTERNAL_ERROR: 表示内部调用操作出错。

---------
