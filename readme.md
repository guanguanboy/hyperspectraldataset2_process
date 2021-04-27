#  高光谱数据预处理步骤

- 这里处理的是第二批采集到的数据

  

- step1: 将envi格式的高光谱数据转换为mat格式的数据。
调用convert_envi_to_mat.py将envi数据转换成mat格式的数据

- step2: 等间隔选择64个波段，并形成新的mat文件。 

首先肯定得修改mat_processed.py
修改方法：
方案：去掉前20个波段，去掉后12个波段。剩余192个波段

每3个波段中选择一个波段，最后形成一个64个band的高光谱数据。192/3 == 64

使用1ms的数据作为lowlight数据，使用15ms数据作为label数据。

- step3: 将mat文件，安装8：2的比例分解为训练集和测试集。结果输出到了lowlight_hyperspectral_datasets/lowlight_origin_mat/
目录下
split_to_train_test.py

- step4: 制作训练数据集
datalowlight.m文件，文件所在位置D:\DataSets\hyperspectraldatasets\lowlight_hyperspectral_datasets\data_preprocess\training_set_ augment

- step5: 制作测试数据集
generate_testdata_lowlight.m ， 文件所在位置：D:\DataSets\hyperspectraldatasets\lowlight_hyperspectral_datasets\data_preprocess\test_set_ pre-processing

