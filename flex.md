
## 响应式WEB页面

### 什么是响应式WEB页面

页面的设计与开发应根据用户行为以及设备环境(系统平台、屏幕尺寸、屏幕定向等)进行相应的响应和调整



### 具体实现方式

1. 固定布局：   
    以像素作为页面的基本单位，不管设备屏幕及浏览器宽度，只设计一套尺寸
2. 可切换的固定布局：   
    同样以像素作为页面单位，参考主流设备尺寸，设计几套不同宽度的布局。通过识别的屏幕尺寸或浏览器宽度，选择最合适的那套宽度布局
3. 弹性网格和布局：   
    以百分比作为页面的基本单位，可以适应一定范围内所有尺寸的设备屏幕及浏览器宽度，并能完美利用有效空间展现最佳效果
4. 混合布局：   
    同弹性布局类似，可以适应一定范围内所有尺寸的设备屏幕及浏览器宽度，并能完美利用有效空间展现最佳效果；只是混合像素、和百分比两种单位作为页面单位

### CMP上的实现方式

**@media** 媒体查询技术

> @media 可以针对不同的屏幕尺寸设置不同的样式，特别是如果你需要设置设计响应式的页面，@media 是非常有用的。

##### 兼容性

- chrome    21
- IE        9
- FF	        3.5
- safari	    4.0
- opera     9






##### 具体实现

**html**

    <div class="row">
    	<div class="col-1350-3 col-1350-2 col-1350-1">
    		<div class="whole-report">
    			content     
    		</div>
    	</div>
    </div>

**css**

    @media screen and (min-width: 0px){
        .col-1350-1 {
            width: 100%;
            float: left;
            padding: 15px;
            /*float:left;*/
        }
    }
    @media screen and (min-width: 1000px){
        .col-1350-2 {
            width: 50%;
            float: left;
            padding: 15px;
            /*float:left;*/
        }
    }
    @media screen and (min-width: 1350px){
        .col-1350-3 {
            width: 33.33%;
            float: left;
            padding: 15px;
            /*float:left;*/
        }
    }




































