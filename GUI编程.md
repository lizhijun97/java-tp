# GUI编程

组件

- 窗口
- 弹窗
- 面板
- 文本框
- 列表框
- 按钮
- 图片
- 监听事件
- 鼠标、键盘事件

## 1、简介

GUI核心：Swing、AWT

缺点：1.界面不美观 2.需要jre环境

重点：了解MVC架构，了解监听

## 2、AWT

### 2.1、AWT简介

1. 包含很多类和接口
2. 元素：窗口、按钮、文本框
3. java.awt

![image-20220723105137112](image/image-20220723105137112.png)

### 2.2、组件和容器

#### 1.Frame窗口

```java
// 第一个案例
package com.cxx.gui;

import java.awt.*;

public class TestFrame {
    public static void main(String[] args) {
        // Frame 源码
        Frame fra = new Frame("java图形界面窗口");
        // 需要设置可见性
        fra.setVisible(true);
        // 设置窗口大小、背景颜色
        fra.setSize(400, 400);
        fra.setBackground(new Color(100, 100, 100));
        fra.setLocation(200, 200);
        fra.setResizable(false);
    }
}
// 第二个案例
package com.cxx.gui;

import java.awt.*;

public class TestFrame1 {
    public static void main(String[] args) {
        MyFrame myFrame1 = new MyFrame(100, 100, 200, 200, Color.DARK_GRAY);
        MyFrame myFrame2 = new MyFrame(100, 100, 300, 300, Color.white);
    }
}

class MyFrame extends Frame{

    static int id = 0;

    public MyFrame(int x, int y,int w,int h,Color color)  {
        super("MyFrame+"+(++id));
        setBackground(color);
        setBounds(x,y,w,h);
        setVisible(true);
    }
}
```

效果图：

![image-20220723113807296](image/image-20220723113807296.png)

####  2.面板Panel

案例

```java
package com.cxx.gui;

import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class TestPanel {
    public static void main(String[] args) {
        Frame frame =new Frame();
        Panel panel = new Panel();
        // 设置布局
        frame.setLayout(null);
        // 设置坐标
        frame.setBounds(300,300,500,500);
        frame.setBackground(new Color(207, 207, 208));
        // panel设置坐标，基于frame
        panel.setBounds(50,50,400,400);
        panel.setBackground(new Color(10,10,10));
        frame.add(panel);
        frame.setVisible(true);
        // 设置监听事件，关闭窗口
        // 适配器模式
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                // super.windowClosing(e);
                System.exit(0);
            }
        });
    }
}
```

效果图

![image-20220723135342194](image/image-20220723135342194.png)

## 3、Swing