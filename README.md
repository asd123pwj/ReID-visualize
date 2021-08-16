> GitHub：https://github.com/asd123pwj/ReID-visualize
>  
> Blog: https://mwhls.top/2858.html

#### Functions

1. input:
   1 query path
   n gallery path
   n gallery match

2. output:

   - 16_male_front_t_01500_117.log:

     ![ReIDVisualizeLog.PNG](https://i.loli.net/2021/08/16/FzpgiCun2mvLTdW.png)

   - 16_male_front_t_01500_117.jpg:

   ![16_male_front_t_01500_117.jpg](https://i.loli.net/2021/08/16/RcNt3Ixw6nSF2My.jpg)

#### Usage-用法

1. import 导入
   `from ReID_visualize import Visualization as vis`
2. initialize 初始化
   `v = vis()`
3. load query 加载query
   `v.load_query('./path/query.jpg')`
4. load gallery 加载gallery
   `v.load_gallery('./path/gallery.jpg', True)`
   `v.load_gallery(['./g1.jpg', './g2.jpg', './g3.jpg'], [True, True, False])`
   True表示图像匹配，False表示不匹配。
5. clear 清理
   `v.clear()`
   clear cache, prepare to visualize the next (query and gallery)
   清除上一次的query与gallery，保持已可视化的数量(index)不变，为下一次可视化做准备
6. set style 设置标注方式
   `v.set_style(style=1, match_color = [0, 255, 0], mismatch_color = [255, 0, 0])`
   style:
   0: framed by a rectangle 
       被矩形框框着
   1: a line in the top
       顶部有一条线标注
   2: only index and True/False
       只显示序号以及True/False
   match_color: 
       the color of match, default is [0, 255, 0]\(green)
       匹配的标注颜色，默认为[0, 255, 0]绿色
   mismatch_color: 
       the color of mismatch, default is [255, 0, 0]\(red)
       不匹配的标注颜色，默认为[255, 0, 0]红色
7. set output path 设置输出路径   
   `v.set_output_path(output='./log/visualize')`

#### Usage sample

```python
from ReID_visualize import Visualization as vis
#	data preparation
query_path = './query/query1.jpg'
gallery_path = ['./load/method1/gallery/1.jpg',
				'./load/method1/gallery/2.jpg',
				'./load/method1/gallery/3.jpg',
				'./load/method1/gallery/4.jpg' ]
gallery_match = [True, True, False, True]

v = vis()

v.load_query(query_path)
v.load_gallery(gallery_path, gallery_match)
v.visualize()   #   visualize the data above, and number of visualization +1 to 1
#   output:   (1: query1.jpg), (1: query1.log)

v.clear()       #   clear the data above, prepare for next visualization.
v.load_query(query_path)
v.load_gallery(gallery_path, gallery_match)
v.load_gallery('./load/method2/gallery/1.jpg', True)
v.load_gallery('./load/method2/gallery/2.jpg', False)
v.visualize()   #   visualize the data above, and number of visualization +1 to 2
#   output:   (2: query1.jpg), (2: query1.log)
```

#### 使用示例

```python
from ReID_visualize import Visualization as vis

#	数据准备
query_path = './query/query1.jpg'
gallery_path = ['./load/method1/gallery/1.jpg',
				'./load/method1/gallery/2.jpg',
				'./load/method1/gallery/3.jpg',
				'./load/method1/gallery/4.jpg' ]
gallery_match = [True, True, False, True]

v = vis()

v.load_query(query_path)
v.load_gallery(gallery_path, gallery_match)
v.visualize()   #   可视化上面的数据，并将index +1 至 1
#   output:   (1: query1.jpg), (1: query1.log)

v.clear()       #   清理上面的数据，为下一次可视化作准备
v.load_query(query_path)
v.load_gallery(gallery_path, gallery_match)
v.load_gallery('./load/method2/gallery/1.jpg', True)
v.load_gallery('./load/method2/gallery/2.jpg', False)
v.visualize()   #   可视化上面的数据，并将index +1 至 2
#   output:   (2: query1.jpg), (2: query1.log)
```

