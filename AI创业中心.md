# AI创业中心—页面制作中心
## 1.页面结构设计
包括以下几个主要部分:
- 页眉
- 轮播图
- 介绍卡片
- “立即咨询”的按钮
  
## 2.页眉部分
保持与其他页面的一致性（不再赘述），固定“OpenJT-AI创业中心”的字样在页眉中央。

## 3.轮播图部分
- 轮播图及其按钮样式，详见```OpenJT官网.md```的```3.3```部分。
- script代码，详见```OpenJT官网.md```的```4.2```部分。
- 轮播图内容部分，详见```OpenJT官网.md```的```5.2```部分。

## 4.介绍卡片部分
1.  - 使用Flexbox布局，卡片能够灵活排列并适应不同屏幕宽度。
    - ```justify-content: space-between;```:在主轴上均匀分配空间，使得子元素之间的间距一致。

    - ```flex-wrap: wrap;```:当空间不足时，允许子元素换行，保持布局的良好性。

    - ```margin-top: 3rem;```:顶部留出3rem的空白，使得卡片与顶部的距离更大。
 ```css
  .features {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            margin-top: 3rem;
        }
 ```
2. - 设置卡片的宽度、背景色。
   
   - ```flex-basis: calc(45% - 2rem);```:为卡片内部添加内边距，防止内容与边界直接接触，增强可读性。

    - ```border-radius: 5px;```：为卡片的角添加圆角效果，使其看起来更柔和。

   - ```box-shadow: 0 2px 5px rgba(0,0,0,0.1);```：为卡片添加轻微的阴影效果，使其在页面上更具层次感。

   - ```margin-bottom: 2rem;```：为每个卡片底部添加间距，避免相邻卡片之间贴得过近
  
   - ```transition: transform 0.3s ease;```：定义卡片在状态变化时的过渡效果，使得动画显得更自然。
```css
 .feature {
            flex-basis: calc(45% - 2rem);
            background-color: white;
            padding: 1.5rem;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            margin-bottom: 2rem;
            transition: transform 0.3s ease;
        }
 ```

 3. 卡片浮动效果：当鼠标悬停在卡片上时，卡片会向上移动5个像素，产生一种浮动的效果，增强用户互动体验。
   ```css
   .feature:hover {
            transform: translateY(-5px);
        }
   ```

4. 卡片内部标题样式：设置卡片标题颜色为深灰，并且在标题底部添加间距，避免标题与卡片内容直接接触，提升视觉效果。
   
   ```css
   .feature h2 {
            color: #333;
            margin-bottom: 1rem;
        }
   ```
## 5.“立即咨询”的按钮部分

 ### 5.1. 按钮的样式设计
  1. 通过```display: inline-block;```该元素的显示方式设为行内块元素。这意味着该元素可以设置宽度和高度，同时也能与其他行内元素在同一行显示。
   
   2. 通过```background-color: #c4c0c0;```设置按钮的背景色。
   
   3. 通过```color: white;```设置按钮的文字颜色。
   
   4. 通过```padding: 10px 20px;```设置按钮的内边距。
   
   5. 通过```text-decoration: none;```取消文本的装饰效果，比如下划线，确保按钮文字显得简洁。
   
   6. ```border-radius: 5px;```将背景的边角设置为5px的圆角，使按钮的外观更加柔和，提升用户体验。
   
   7. ```font-weight: bold;```设定文字为加粗，使得按钮上的文字更加显眼。
   
   8. ```transition: background-color 0.3s;```设置按钮的背景色的过渡效果，时间为0.3秒。当用户悬停在按钮上时，背景颜色的变化将会顺畅地过渡到新颜色。
  ```css
   .cta-button {
            display: inline-block;
            background-color: #c4c0c0;
            color: white;
            padding: 10px 20px;
            text-decoration: none;
            border-radius: 5px;
            font-weight: bold;
            transition: background-color 0.3s;
            
        }
```
   9.  设置一个伪类```:hover```，当用户悬停在按钮上时，按钮的背景色将会变为深灰色，增强视觉反馈。
  ```css
   .cta-button:hover {
            background-color: #333;
        }
   ```

   ### 5.2. 按钮的功能实现
   1. ```document.querySelector('.cta-button')```选择页面中类名为cta-button的第一个元素。
   2. ```addEventListener('click', function(){});```为按钮添加点击事件，当用户点击按钮时，执行函数体内的代码。
   
   3. ```e.preventDefault();```阻止默认行为，防止页面跳转。(此处也并未添加实际链接)
   4. ```alert('请联系我们，我们将竭诚为您提供专业的AI技术咨询服务。');```按钮点击后会弹出一个警告框，提示用户联系以获取AI技术咨询服务，增强了与用户的交互。

   ```javascript
    // 按钮
      document.querySelector('.cta-button').addEventListener('click', function(e) {
            e.preventDefault();
            alert('请联系我们，我们将竭诚为您提供专业的AI技术咨询服务。');
        });
   ```

