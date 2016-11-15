#ใบงานที่ 10
##การเขียนโปรแกรมกราฟฟิกส์ด้วย GDI+ (2)
##นางสาวนภารัตน์ ฐิติกรโกวิท 5030180
##กล่าวนำ
ใบงานนี้ มีวัตถุประสงค์ เพื่อให้นักศึกษา ได้รู้จักกับ GDI+ ซึ่งจะช่วยให้นักษาสามารถ
* วาดรูปร่างต่างๆ โดยใช้ GDI+ ได้


## การวาดเส้นตรง
การวาดเส้นตรง เป็นการเชื่อมต่อระหว่างจุด จำนวน 2 จุด  โดยใช้ออบเจกต์ Pen เป็นตัวกำหนดลักษณะของเส้น 

แก้ไข code ต่อไปนี้ในฟังก์ชัน private void Form1_Paint(object sender, PaintEventArgs e)
* [Graphics.DrawLine Method](https://msdn.microsoft.com/en-us/library/system.drawing.graphics.drawline(v=vs.110).aspx)

<p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-1.png">
</p>


Code

```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab10
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            Pen blackPen = new Pen(Color.Black, 3);
            Point point1 = new Point(100, 100);
            Point point2 = new Point(200, 100);
            e.Graphics.DrawLine(blackPen, point1, point2);
            blackPen.Dispose();
        }
    }
}


```

ผลการทดลอง


![](https://github.com/NAPHARAT/LAB-10/blob/master/imgs/1.JPG)

## การวาดเส้นตรงด้วย pen style และ brush
* [PenType Enumeration](https://msdn.microsoft.com/en-us/library/system.drawing.drawing2d.pentype(v=vs.110).aspx)
 <p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-2.png">
</p>


Code


```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab10
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            Pen pen = new Pen(Color.Red);
            e.Graphics.DrawLine(pen, 10, 50, 220, 50);


            pen = new Pen(Color.Green,2);
            pen.DashStyle = DashStyle.DashDot;
            e.Graphics.DrawLine(pen, 10, 80, 220, 80);

            pen = new Pen(Brushes.DeepSkyBlue,4);
            e.Graphics.DrawLine(pen, 10, 120, 220, 120);
            pen.Dispose();
            //Pen blackPen = new Pen(Color.Black, 3);
            //Point point1 = new Point(100, 100);
            //Point point2 = new Point(200, 100);
            //e.Graphics.DrawLine(blackPen, point1, point2);

        }
    }
}



```

ผลการทดลอง

![](https://github.com/NAPHARAT/LAB-10/blob/master/imgs/2.JPG);

## การกำหนดจุดปลายของเส้นตรงด้วย style แบบต่างๆ

* [LineCap Enumeration](https://msdn.microsoft.com/en-us/library/system.drawing.drawing2d.linecap(v=vs.110).aspx)
<p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-3.png">
</p>

Code

```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab10
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            //Pen pen = new Pen(Color.Red);
            //e.Graphics.DrawLine(pen, 10, 50, 220, 50);


            //pen = new Pen(Color.Green,2);
            //pen.DashStyle = DashStyle.DashDot;
            //e.Graphics.DrawLine(pen, 10, 80, 220, 80);

            //pen = new Pen(Brushes.DeepSkyBlue,4);
            //e.Graphics.DrawLine(pen, 10, 120, 220, 120);
            
            //Pen blackPen = new Pen(Color.Black, 3);
            //Point point1 = new Point(100, 100);
            //Point point2 = new Point(200, 100);
            //e.Graphics.DrawLine(blackPen, point1, point2);


            Pen[] objPen = new Pen[11];
            for(int i = 0 ; i != 11 ; i++)
            {
                objPen[i] = new Pen(Color.Blue, 9);
            }
            objPen[0].EndCap = LineCap.AnchorMask;
            objPen[2].EndCap = LineCap.ArrowAnchor ;
            objPen[3].EndCap = LineCap.DiamondAnchor ;
            objPen[4].EndCap = LineCap.Flat ;
            objPen[5].EndCap = LineCap.NoAnchor ;
            objPen[6].EndCap = LineCap.Round ;
            objPen[7].EndCap = LineCap.RoundAnchor ;
            objPen[8].EndCap = LineCap.Square ;
            objPen[9].EndCap = LineCap.SquareAnchor ;
            objPen[10].EndCap = LineCap.Triangle ;
            for (int i = 0; i != 11; i++)
            {
                e.Graphics.DrawLine(objPen[i], 10, 10 + 20 * i, 200, 10 + 20 * i);
                objPen[i].Dispose();
            }

        }
    }
}



```

ผลการทดลอง

![](https://github.com/NAPHARAT/LAB-10/blob/master/imgs/3.JPG)
##การวาดเส้นโค้ง
การวาดเส้นโค้ง ทำได้โดยการกำหนดจุดไว้ใน array ของ point แล้วส่งให้กับฟังก์ชัน DrawCurve ดังตัวอย่างต่อไปนี้
<p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-4.png">
</p>


Code

```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab10
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            Pen pen = new Pen(Color.Green);
            Point[] pt = {new Point (20,200),new Point(50,20),
                         new Point(100,100),new Point(150,20),
                         new Point(200,200)};
            e.Graphics.DrawCurve(pen, pt);
            pen.Dispose();



            //Pen pen = new Pen(Color.Red);
            //e.Graphics.DrawLine(pen, 10, 50, 220, 50);


            //pen = new Pen(Color.Green,2);
            //pen.DashStyle = DashStyle.DashDot;
            //e.Graphics.DrawLine(pen, 10, 80, 220, 80);

            //pen = new Pen(Brushes.DeepSkyBlue,4);
            //e.Graphics.DrawLine(pen, 10, 120, 220, 120);
            
            //Pen blackPen = new Pen(Color.Black, 3);
            //Point point1 = new Point(100, 100);
            //Point point2 = new Point(200, 100);
            //e.Graphics.DrawLine(blackPen, point1, point2);


            //Pen[] objPen = new Pen[11];
            //for(int i = 0 ; i != 11 ; i++)
            //{
            //    objPen[i] = new Pen(Color.Blue, 9);
            //}
            //objPen[0].EndCap = LineCap.AnchorMask;
            //objPen[2].EndCap = LineCap.ArrowAnchor ;
            //objPen[3].EndCap = LineCap.DiamondAnchor ;
            //objPen[4].EndCap = LineCap.Flat ;
            //objPen[5].EndCap = LineCap.NoAnchor ;
            //objPen[6].EndCap = LineCap.Round ;
            //objPen[7].EndCap = LineCap.RoundAnchor ;
            //objPen[8].EndCap = LineCap.Square ;
            //objPen[9].EndCap = LineCap.SquareAnchor ;
            //objPen[10].EndCap = LineCap.Triangle ;
            //for (int i = 0; i != 11; i++)
            //{
            //    e.Graphics.DrawLine(objPen[i], 10, 10 + 20 * i, 200, 10 + 20 * i);
            //    objPen[i].Dispose();
            //}

        }
    }
}


```
ผลการทดลอง

![](https://github.com/NAPHARAT/LAB-10/blob/master/imgs/4.JPG)


## การวาดเส้นโค้งด้วย Graphics path
 <p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-5.png">
</p> 


Code
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab10
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            
            GraphicsPath gp = new GraphicsPath();
            gp.AddCurve(new Point[] {
                new Point(100,50),
                new Point(105,40),
                new Point(120, 40),
                new Point(130, 65),
                new Point(100, 100)
            }, 0.5f);
            gp.AddCurve(new Point[] {
                new Point(100,100),
                new Point(70,65),
                new Point(80,40),
                new Point(95,40),
                new Point(100,50)
            }, 0.5f);
            e.Graphics.DrawPath(Pens.Red, gp);
        }

           

        }
    }

```


ผลการทดลอง

![](https://github.com/NAPHARAT/LAB-10/blob/master/imgs/5.JPG)
## การวาดรูปทรงสี่เหลี่ยม
### การวาดสี่เหลี่ยมครั้งละรูปเดียว
  <p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-6.png">
</p> 


Code
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab10
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            Pen mypen = new Pen(Color.Blue);
            e.Graphics.DrawRectangle(mypen, 10, 120, 100, 100);
            Rectangle rect = new Rectangle(10, 10, 100, 100);
            e.Graphics.DrawRectangle(mypen, rect);
        }



            //Pen pen = new Pen(Color.Green);
            //Point[] pt = {new Point (20,200),new Point(50,20),
            //             new Point(100,100),new Point(150,20),
            //             new Point(200,200)};
            //e.Graphics.DrawCurve(pen, pt);
            //pen.Dispose();

        //    GraphicsPath gp = new GraphicsPath();
        //    gp.AddCurve(new Point[] {
        //        new Point(100,50),
        //        new Point(105,40),
        //        new Point(120, 40),
        //        new Point(130, 65),
        //        new Point(100, 100)
        //    }, 0.5f);
        //    gp.AddCurve(new Point[] {
        //        new Point(100,100),
        //        new Point(70,65),
        //        new Point(80,40),
        //        new Point(95,40),
        //        new Point(100,50)
        //    }, 0.5f);
        //    e.Graphics.DrawPath(Pens.Red, gp);
        //}

            //Pen pen = new Pen(Color.Red);
            //e.Graphics.DrawLine(pen, 10, 50, 220, 50);


            //pen = new Pen(Color.Green,2);
            //pen.DashStyle = DashStyle.DashDot;
            //e.Graphics.DrawLine(pen, 10, 80, 220, 80);

            //pen = new Pen(Brushes.DeepSkyBlue,4);
            //e.Graphics.DrawLine(pen, 10, 120, 220, 120);

            //Pen blackPen = new Pen(Color.Black, 3);
            //Point point1 = new Point(100, 100);
            //Point point2 = new Point(200, 100);
            //e.Graphics.DrawLine(blackPen, point1, point2);


            //Pen[] objPen = new Pen[11];
            //for(int i = 0 ; i != 11 ; i++)
            //{
            //    objPen[i] = new Pen(Color.Blue, 9);
            //}
            //objPen[0].EndCap = LineCap.AnchorMask;
            //objPen[2].EndCap = LineCap.ArrowAnchor ;
            //objPen[3].EndCap = LineCap.DiamondAnchor ;
            //objPen[4].EndCap = LineCap.Flat ;
            //objPen[5].EndCap = LineCap.NoAnchor ;
            //objPen[6].EndCap = LineCap.Round ;
            //objPen[7].EndCap = LineCap.RoundAnchor ;
            //objPen[8].EndCap = LineCap.Square ;
            //objPen[9].EndCap = LineCap.SquareAnchor ;
            //objPen[10].EndCap = LineCap.Triangle ;
            //for (int i = 0; i != 11; i++)
            //{
            //    e.Graphics.DrawLine(objPen[i], 10, 10 + 20 * i, 200, 10 + 20 * i);
            //    objPen[i].Dispose();
            //}

        }
    }


```


ผลการทดลอง

![](https://github.com/NAPHARAT/LAB-10/blob/master/imgs/6.JPG)
###การวาดสี่เหลี่ยมพร้อมกันครั้งละหลายๆ รูป
  <p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-7.png">
</p> 


## การวาดวงกลมและวงรี
วงรีต่างจากวงกลมตรงที่เส้นผ่านศูนย์กลางในแกนตั้งและแกนนอนจะไม่เท่ากัน ในภาษาโปรแกรมส่วนใหญ่จะมีเฉพาะฟังก์ชันวาดวงรี ถ้าต้องการวาดวงกลม ให้กำหนดเส้นผ่านศูนย์กลางในแกนตั้งและแกนนอนให้เท่ากัน
   <p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-8.png">
</p> 

## การวาดส่วนโค้ง (Arc)
   <p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-9.png">
</p> 
## การวาดรูป Pie
  <p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-10.png">
</p>  

## การสร้าง graphics path จากรูปต่างๆ 
  <p align="center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-10/blob/master/imgs/lab10-11.png">
</p>  

#แบบฝึกหัด
ให้วาดรูปวิว โดยใช้รูปร่างต่างๆ ที่ทำการทดลองใน Lab นี้

##เอกสารอ้างอิง
### [Graphics Methods](https://msdn.microsoft.com/en-us/library/system.drawing.graphics_methods(v=vs.110).aspx)
### [System.Drawing Namespace](https://msdn.microsoft.com/en-us/library/system.drawing(v=vs.110).aspx)
### [GDI+ .NET Color & HatchStyle Chart](https://drewnoakes.com/snippets/GdiColorChart/)

