### 6.3 Peterson 算法
---
- Peterson算法是对临界区问题的一种解答

- 共享数据段
    ````java
    int turn;
    boolean flag[2] 
    ````
- 算法实现
    ````java
    do{
        flag[i]=true;
        turn=j;
        while(flag[j]&&turn==j){
        }
        //临界区代码
        flag[i]=false;
        //剩余区代码
    }while(True)
    ````
- 算法解读
    - 共享数据段
        - `turn` 表示哪个进程**可以**进入其临界区
        - `flag[i]` 表示进程 `i` **想要**进入其临界区
    - 进入区解读
        - `flag[i]=true`代表这个进程想要进入临界区
        - `turn=j` 代表它很谦让，将可以进入临界区的权限赋给`j`
        - 然后通过 `while(flag[j]&&turn==j){}` 进行阻塞，此时
            1. 若 `j` 不想进入临界区则阻塞无效，`i` 进入临界区
            2. 若 `j` 想进入临界区，则通过`turn`值来确定谁被阻塞，谁进入临界区
    - 退出区解读
        - `flag[i]=false` 代表执行完毕临界区代码后，`i` 不再想进入临界区了
---
&copy; 2018 T0UGH. All rights reserved.