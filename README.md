# GuoLaii_Switch
A reproduction of  TheKOG's Infinity Gauntlet. Adding annotations and revising some details.
下载release使用。

文件说明：
train.ipynb : 模型的训练。由于受到环境与麦克风的影响，电脑接受到响指的音频会有差异，如果在现模型无法准确识别的话，建议换用KOG的模型或者干脆重新训练一个。
show.py : 输出指定音频文件的波形图，以此可以看出录制响指声音的区别。
![$Z`%1{MPEZUT9DD23H3RO`V](https://github.com/GuoLaii/GuoLaii_Switch/assets/170413627/08fa1cbd-fa4a-409a-babe-24e2018fe00a)

record.py : 音频的录制。两个功能，1.训练样本的录制  2.录制声音，储存在tmp.wav中，供模型进行推理检测。
