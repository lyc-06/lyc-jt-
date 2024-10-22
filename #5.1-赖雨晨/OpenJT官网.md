# OpenJT官网—页面制作过程

## 1.页面结构设计
首先,我设计了页面的基本结构,包括以下几个主要部分:
- 顶部导航栏: 包括logo,四个可跳转的不同板块
- 主体: 包括轮播图,对OpenJT的初总体介绍
- 底部: 包括联系方式、友情链接、版权信息

## 2. HTML结构编写

### 2.1 基本HTML结构
创建了基本的HTML文档结构,设置语言为中文,并添加了必要的meta标签，设置了网页的标题。同时为了字体的美观，引入了字体文件。

### 2.2 页面结构
```html
<header>
    <nav>
        <!-- 导航菜单将在这里添加 -->
    </nav>
</header>

<div class="carousel">
    <!-- 轮播图将在这里添加 -->
</div>

<div class="content">
    <!-- 主要内容将在这里添加 -->
</div>

<footer>
    <!-- 页脚内容将在这里添加 -->
</footer>
```
## 3.CSS样式编写
### 3.1 全局样式
```css
body {
    font-family: 'Roboto', sans-serif;
    margin: 0;
    padding: 0;
}
```
- 设置了```body```的字体为```Roboto```,以提升文本可读性和现代视觉效果。 
- 并设置了```margin```和```padding```为0,以实现无缝的页面布局和更好的设计控制。
  
### 3.2 顶部导航栏样式

- 设置导航栏的颜色为黑白经典配色，使得页面带有极简主义的美观。
- 使用```position: fixed```将导航栏固定在页面顶部，并使用```z-index```属性将其置于其他元素之上。
- 为了突出OpenJT，在导航栏上固定了一个logo,并且使用```bold```属性使其更加醒目。
- 设置下拉菜单```dropdown```的样式：
  
   - 使用```display: none```将其隐藏
   - 使用```position: absolute```将其定位于导航栏下方
  - 使用```dropdown:hover .dropdown-content {display: block;}```实现鼠标悬停时显示下拉菜单内容。。

### 3.3 轮播图样式
- 固定轮播图的高度和宽度，使用```position: relative```将其定位于页面中央，并使用```overflow: hidden```属性防止轮播图溢出。
  
- 规定图片样式
  
- 规定切换按钮样式
     - 固定按钮位置在轮播图中间，一左一右。
     - 使用```cursor: pointer;```,实现当鼠标悬停在按钮上时，长出手指形状的鼠标指针，表示可以点击，增强交互效果。

### 3.4 标题样式
- 设置一级标题和二级标题的字体大小、颜色等，使得标题更加突出。

- 使用```margin-top```和```margin-bottom```属性设置标题的上下边距，使得标题与下面的内容有足够的距离。

- 使用```text-align: center;```属性将一级标题居中显示。

### 3.5 主体内容样式
- 设置字体样式、大小，内外边距等，使得内容更加整齐美观。
  
- 使用```box-shadow```属性为主体内容添加类似于边框的阴影，增强视觉效果。

- 设置图片的宽高，在图片与内容项文本之间添加40像素的右边距，使两者之间留有空隙，提升可读性。
  
- 将标题的下边距设定为40像素，确保标题与后续内容之间有足够的空间。

### 3.6 页脚样式
- 与页眉的样式和颜色统一，使得页面整体美观。
  
- 设置联系方式、友情链接、版权信息的样式。

- 模仿网页页脚的一般样式，通过```justify-content: space-between;```实现在横向（主轴）上均匀分配空间，首尾元素（例如联系方式和版权信息）将被推向两端，中间的元素（友情链接）会均匀分布。

- 通过```align-items: center;```让页脚中的文本元素垂直居中显示。

- 设置友情链接的样式,并实现鼠标悬停时显示下划线：
  ```css
  footer a:hover {  
    text-decoration: underline; }
  ```

## 4. 实现javascript功能
### 4.1 固定导航栏
- 事件监听：
  
  当用户在浏览器窗口中滚动（scroll）时，将会触发后面定义的匿名函数。在滚动事件发生时，这段代码会执行。
```javascript
  window.addEventListener('scroll', function() { ... })
 ```

- 获取导航栏元素:
  
   使用```document.querySelector``` 方法来选择页面中的 ```<header>``` 元素，并将其存储在变量 'header' (即网页顶部的导航栏)中。
  ```javascript
  var header = document.querySelector('header');
  ```

- 添加或移除类名：

  当页面向下滚动时，导航栏添加 sticky 类，使其固定在页面顶部。当页面向上滚动时，sticky 类被移除，导航栏恢复原状。
 ```javascript
  header.classList.toggle('sticky', window.pageYOffset > 0);
  ```
  ### 4.2 轮播图
- 元素选择：
  通过```var ```选择相应元素，设置轮播图的基本结构和状态，为实现图片轮播的交互逻辑打下了基础。
  
- 函数 showImage(index):
展示指定索引的图片，并隐藏其他所有图片。
```javascript
  function showImage(index) {
        for (var i = 0; i < images.length; i++) {
          images[i].style.display = 'none';
        }
        images[index].style.display = 'block';
      }
```

- 函数 nextImage():用于切换到下一张图片。
```javascript
function nextImage() {
        currentIndex++;
        if (currentIndex >= images.length) {
          currentIndex = 0;
        }
        showImage(currentIndex);
      }
```

- 事件监听器 ```prevBtn.addEventListener('click', ...):``` 实现点击上一张按钮时切换到上一张图片。
  
```javascript
   prevBtn.addEventListener('click', function() {
        currentIndex--;
        if (currentIndex < 0) {
          currentIndex = images.length - 1;
        }
        showImage(currentIndex);
      });
   ```

-定时器 : 实现每隔5秒切换到下一张图片。
```javascript
  setInterval(nextImage, 5000); 
```
  
## 5. 页面内容完善
### 5.1 顶部导航栏
- 使用```ul```创建无序列表，里面包含多个 ```li``` 列表项，这些项代表导航菜单的各个链接。
- 顶部导航栏的logo: 采用OpenJT作为导航栏的logo。
- 在```dropdown```这个类里添加内容，用```<a href="#" target="_self">```创建下拉菜单的链接,并且在当前窗口中打开链接。
  
### 5.2 轮播图
- 在[Unsplash](https://mani-unsplash-clone.netlify.app/)网站上找到适合的图片，并下载到本地。
- 使用```<img src="...">```标签将下载的图片添加到轮播图的```<div>```元素，并且用```alt="..."```属性添加替代文本。
- 控制按钮：
  ```html
  <div class="carousel-control prev">&lsaquo;</div>
    <div class="carousel-control next">&rsaquo;</div>
  ```
  生成左箭头和右箭头图标。用户可以点击这些按钮来手动切换图片。

### 5.3 主体内容
- 设置居中的标题：```OpenJT   智启未来，创见无限```
- 将OpenJT公司的核心理念和价值观分为三个主要内容：企业文化、行为准则和使命愿景。
- 选择合适的图片插入，并且编写每个部分的相应文字内容，有效地向访客传达关于OpenJT的品牌形象和价值主张。

### 5.4 页脚
- 使用```<p>```标签显示联系的信息，包括联系电话、电子邮件、地址、版权信息，让用户能够迅速找到联系的方式。
- 提供了与公司在不同社交媒体上的互动通道，用```target="_blank"```属性性打开新窗口。


  
 ## 6. 总结
 1.初步认识到如何具体地搭建一个网页：
 
 页面的美观，主题的明确，与用户的交互体验，都是需要着重考虑的问题。为了让用户在短时间内快速了解到公司的产品和服务，并与公司建立深入的联系，必须在短时间内抓住用户的眼球，快速响应用户的需求，并提供有价值的服务。

 2.掌握了html的基本语法，如标签的嵌套、属性的设置、注释的添加等，并能将它们应用到网页的结构中。
 
 3.掌握了css的布局、字体、颜色、边框、背景、动画、交互等属性的使用，并能将它们应用到网页的设计中。

 4.掌握了掌握了javascript的基本语法，如事件监听、定时器等基本概念，并能使用它们实现一些基本的功能。将它们应用到网页的交互中。


 