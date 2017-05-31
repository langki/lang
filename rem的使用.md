- 使用
- 动态赋值页面根元素(html)的字体大小

'(function (doc, win) {
    var docEl = doc.documentElement,
    resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize';

    var recalc = function () {
        var width = docEl.clientWidth;

        if (width > 640) {
            width = 640 ;
        }
        if (width < 320) {
            width = 320 ;
        }

        docEl.style.fontSize = 100 * (width / 1080) + 'px';     //1080 是设计图的宽度  
      };
    recalc();


    if (!doc.addEventListener) return;
    win.addEventListener(resizeEvt, recalc, false);
})(document, window);'

页面引入这段脚本，再根据实际设计图取值，给相应的部位设置 css。

例如根元素(html)字体大小为 100 像素时，宽为 100 像素的 div，其样式设置为 width:1rem; 。

- 心得：

1080 是设计图宽度，这样可以直接在图上量取数值，写在样式中。例如间距 40px ，赋值 0.4rem 。

chrome 支持的最小字体为 12px，所以设置为 100px，方便取值。
