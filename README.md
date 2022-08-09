#数据的爬取
root="./Image-Downloader-master"
根据文件内README操作


#数据的筛选（移除异常图像）
分两步：
1.初级筛选--根据文件信息、颜色特征、纹理特征
2.高级筛选--降维聚类

##第一步：初级筛选 sheep_adviced_filter.py
根据图片大小、长宽以及梯度初步筛选，将不满足的图片移到存放图片路径内remove文件中

###所需要的库文件
re 
os 
cv2
shutil
numpy

###运行方式及注意点
修改图片路径root_dir
注意要修改特定的文件大小以及长宽的限制

##第二步：高级筛选 sheep_advanced_filter.py
其中使用了两种降维的方法t-SNE，UMAP，两个方法最终都显示了二维特征分布图，择优选择性移除异常图像

###所需要的库文件
pip install umap-learn   
pip install opencv-python   
pip install matplotlib  
pytorch 
re 
os 
cv2
shutil
numpy
torchvision

###运行方式级注意点
修改图片路径root_dir
运行时会先下载预训练模型稍等片刻
注意112行name_list.append(img_name[6:9])，修改切片，根据图片名字，只取数字编号，在可视化的时候方便找出图片