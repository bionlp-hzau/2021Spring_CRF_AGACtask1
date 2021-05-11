# 2021Spring_CRF_AGACtask1

## Wapiti工作环境配置

```
git clone https://github.com/Jekub/Wapiti.git
cd Wapiti
sudo make
sudo make install
./wapiti (有帮助文档输出表示安装成功)
```

注意事项：

1、如果make失败，先安装gcc

2、如果git不成功，直接下载到工作目录解压后make


## 数据准备

```
git clone https://github.com/ouyangsizhuo/2021Spring_CRF_AGACtask1.git
```
进入工作文件夹，解压AGAC压缩包


## 训练模型

```
wapiti train -a sgd-l1 -t 3 -i 10 -p pat/Tok321dis.pat <(cat AGAC/train_split/*.txt) AGAC/mod/AGAC_train.mod
```

## 预测标签

```
wapiti label -c -m AGAC/mod/AGAC_train.mod <(cat AGAC/test_split/*.txt) AGAC/train_out.tab
```

## 评估结果

```
perl conlleval.pl -d $'\t' <AGAC/train_out.tab | tee AGAC/train_out.eval
```

