# TIL datasets

## Imagenet
Imagenet dataset의 object localization set의 경우
2012년부터 내용이 변경된 부분이 없다. 따라서 이 155GB의 데이터 셋이 필요한 경우 2012년 데이터 셋을 받아서 training을 돌려도 무방

## SVHN
[The Street View House Numbers (SVHN) Dataset](http://ufldl.stanford.edu/housenumbers/)으로 MNIST처럼 digit 데이터 셋이지만 구글 맵에서 존재하는 집주소의 이미지 들을 가지고 만든 dataset

2011년 NIPS [Reading Digits in Natural Images with Unsupervised Feature Learning, Yuval Netzer et el.](http://ufldl.stanford.edu/housenumbers/nips2011_housenumbers.pdf)에서 처음 소개

Dataset Information:
- SVHN train - 73,257 digits for training
- SVHN test - 26,032 digits for testing.
- SVHN extra (train) - 531,131 additional, somewhat less difficult samples, to use as extra
training data.

Framework support
- `torchvision`에서 `torchvision.datasets.svhn`으로 사용가능

## CUB-200
[Caltech-UCSD Birds 200](http://www.vision.caltech.edu/visipedia/CUB-200.html) 데이터 셋은 200여종의 북미에 많이 서식하는 조류 데이터 셋

Dataset Information:
- Number of categories: 200
- Number of images: 6,033
- Annotations: Bounding Box, Rough Segmentation, Attributes
