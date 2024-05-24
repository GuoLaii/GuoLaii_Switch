# GuoLaii_Switch
A reproduction of  TheKOG's Infinity Gauntlet. Adding annotations and revising some details.
下载release使用。

文件说明：
train.ipynb : 模型的训练。由于受到环境与麦克风的影响，电脑接受到响指的音频会有差异，如果在现模型无法准确识别的话，建议换用KOG的模型或者干脆重新训练一个。
show.py : 输出指定音频文件的波形图，以此可以看出录制响指声音的区别。
record.py : 音频的录制。两个功能，1.训练样本的录制  2.实时录制声音，储存在tmp.wav中，供模型进行推理检测。
snap.py : 载入模型，检测实时声音与响指声音的相似度。
test.py : 检测以上各python函数是否能达到效果。
connect.py : 与esp32单片机建立蓝牙连接，并import snap, record  进行电脑麦克风的实时监测，若检测到声音与响指声音的相似度>0.9 则通过蓝牙向esp32发送字符串 "SWITCH"。 esp32接收到后，进行下一步操作(详见esp32文件夹)

tmp.wav： 储存实施录制声音的文件
Guolaii_model : 模型文件夹。因为我的设备录的响指声音与KOG大佬的有较大出入，因此重新录制训练数据集进行新模型的训练
Guolaii_audios : 训练数据集(偷懒了，只录了200个样本，并且没有录制负样本，这导致虽然可以检测响指声音，不过很容易误识别拍手等类似声音)
esp32 folder : 分为sever 和 test。  test使用经典蓝牙连接， 而sever使用BLE连接。（不知为何我的电脑无法搜索到BLE设备，所以测试时就使用了test）  烧录 '.ino'文件到esp32

复现时遇到的bug & 注意事项：
    一、在复现KOG大佬的项目时，connect.py文件中的pybluez库(import bluetooth)，总是安装失败，上网搜了好多方法也不管用，在此给出我的解决方法：
                用anaconda创建新python环境，版本使用3.10。 安装pybluez2（似乎是民间版本  pip install pybluez2）
    二、在train.ipynb中 使用Load_Snap等函数 加载音频时总是报错，找不到文件：
          1.更换为绝对路径
          2.对filename进行强制类型转换str()
    
