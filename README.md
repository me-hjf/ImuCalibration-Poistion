# ImuCalibration-Poistion

IMU校正+定位

选用的是维特智能BEWT901CL九轴IMU


[![视频]( http://g1.ykimg.com/054202085D079D9E0000012FE702BF7B)](https://v.youku.com/v_show/id_XNDIzMjAzMDA3Mg==.html?spm=a2hzp.8244740.0.0)

[![asciicast](https://asciinema.org/a/42383.png)](https://asciinema.org/a/42383)

视频和计算的姿态没有对上，这也是个挺难的问题，见谅。

单纯IMU定位还有有些困难，有空要读读刘儿兀教授的文章。

使用了PDR中（ https://github.com/shenshikexmu/Gait-Tracking-With-x-IMU ），对速度归0的方法，用四元数不再变动作为速度为0的依据 

姿态没有使用融合算法，加速度噪音挺大，融合后姿态还是有噪音，可能参数需要再调，这需要时间，没有做。

定位不准的原因：

1，何时为静止的判断还是不够准确，使得位置在传感器静止时出现偏移。

2，初始的IMU姿态计算，由于没有滤波算法，初始姿态误差使得IMU在世界坐标系下的加速度的计算结果产生误差。但在我这个数据集上，我自己的尝试，没有滤波比滤波的定位效果要好，滤波后位置漂移更大。还是滤波参数要调。

3，与PDR不同的是，在校正过程中IMU姿态变化很大，而在PDR中IMU的一个轴总是向下，IMU坐标系的重力方向计算相对准确（静止时重力基本是同一个向量）。而校正过程，轴变化导致坐标系的重力方向计算误差大一些（轴在转动，静止时重力是不同的方向）。

4，最后几笔画弧还是挺漂亮，这个和PDR一样，IMU测的重力向量基本没变。
