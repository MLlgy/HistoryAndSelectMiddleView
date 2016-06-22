### 浏览

![histogram_week.gif](http://upload-images.jianshu.io/upload_images/1796947-ba3b83d7b036c154.gif?imageMogr2/auto-orient/strip)


![hitogram_month.gif](http://upload-images.jianshu.io/upload_images/1796947-7a09f3ec9c120607.gif?imageMogr2/auto-orient/strip)


![histogram_move.gif](http://upload-images.jianshu.io/upload_images/1796947-dd65e25171918672.gif?imageMogr2/auto-orient/strip)

### 特性

- 比例将根据传入数据的最大值自动计算
- 可以更改一屏最大显示行数
- 颜色字体大小等属性可以更改

### 用法

在布局文件中添加

````
<com.salmonzhg.histogramview_demo.views.HistogramView
    android:id="@+id/histogram"
    android:layout_width="match_parent"
    android:layout_height="150dp"
    app:date_text_color="@color/colorPrimary"
    app:date_text_size="14sp"
    app:histogram_color="@color/colorPrimaryDark" />
````
在控制器中添加

````

    HistogramView.HistogramEntity[] entities = new HistogramView.HistogramEntity[30];
    for (int i = 0; i < entities.length; i++) {
        String showInTimeLime = String.valueOf(i); //也可以是 "Mon","Tue","Thr"
        int count = (int) (Math.random()*10); // 任意整型 
        HistogramView.HistogramEntity e = new HistogramView.HistogramEntity(
            showInTimeLime, count);
        entities[i] = e;
    }

    mHistogram.setSelectListener(new HistogramView.OnSelectListener() {
        @Override
        public void onSelected(int index) {
            showToast(index + " selected" + "\nvalue: " + data[index].count);
        }
    });

    // 设置数据同时也会触发动画
    mHistogram.setData(entities);


````