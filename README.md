# wxk-project4
![2](https://github.com/stream00/wxk-project4/blob/main/2.jpg)
![2j1](https://github.com/stream00/wxk-project4/blob/main/2j1.jpg)
![2j2](https://github.com/stream00/wxk-project4/blob/main/2j2.jpg)
![2j3](https://github.com/stream00/wxk-project4/blob/main/2j3.jpg)
```java
PImage img;
int n=1080*969;

void setup() {
  size(1080, 969);
  img=loadImage("2.jpg");
  img.resize(width, height);
  frameRate(30);
}

void draw() {
  noStroke();
  fill(255);
  rect(0, 0, width, height);
  //image(img,0,0);
  //background(0);
  float startX=mouseX;
  int step=2;
  for (int i=0; i<width; i+=step) {
    for (int j=0; j<height; j+=step) {
      int n=i+j*width;
      color c=img.pixels[n];
      float xoff=0;
      float yoff=0;
      if (i>startX) {
        float scl=map(i, startX, startX+width, 0, 10000);
        xoff=abs(randomGaussian())*scl;
        yoff=random(-scl*0.5, scl*0.5);
      }
      //随机粒子距离控制
      float r=random(0, 10);
      noStroke();
      fill(c);
      ellipse(i+xoff, j+yoff, r, r);
    }
  }
}

```

![3](https://github.com/stream00/wxk-project4/blob/main/3.jpg)
![3j1](https://github.com/stream00/wxk-project4/blob/main/3j1.jpg)
![3j2](https://github.com/stream00/wxk-project4/blob/main/3j2.jpg)
![3j3](https://github.com/stream00/wxk-project4/blob/main/3j3.jpg)
```java
//用粒子系统，截取像素点的颜色，并用rgb与brightness控制速度与角度，最后利用颜色“冷远暖近”的特性创造出空间感
PImage img;
xq[] xqs=new xq[640000];

void setup(){
  size(800,800);
  img=loadImage("3.jpg");
  img.resize(width, height);
for(int i=0;i<xqs.length;i+=20){
  float r,g,b,bn;
  color c=img.pixels[i];
      r=red(c);
      g=green(c);
      b=blue(c);
      bn=map(brightness(c),0,255,-1,1);
xqs[i]=new xq(new PVector (i%800,i/800),random(1,20),r,g,b,bn);
}
frameRate(60);
}

void draw(){
  noStroke();
  fill(0,1);
rect(0,0,width,height);
for(int i=0;i<xqs.length;i+=20){
xqs[i].update();
xqs[i].display();
xqs[i].check();
}
}
//randomGaussian();


class xq{
float a=0;
PVector loc;
int c;float vx=0,vy=0,r;
float B1,G1,R1,bn1;

xq(PVector location,float r,float R,float G,float B,float bn){
loc=location;
this.r=r;
R1=R;
G1=G;
B1=B;
bn1=bn;
}
//位置
void update(){
bn1+=0.02*noise(0.001*(loc.x+R1+B1-G1),0.005*(loc.y+R1+B1-G1))  ;
vx=2*sin(bn1);
vy=2*cos(bn1);
loc.x+=vx;
loc.y+=vy;
}
//画小球
void display(){
noStroke();
//blendMode(MULTIPLY);
//colorMode(HSB,360,100,100);
fill(R1,G1,B1);
ellipse(loc.x,loc.y,r,r);
}
//边界判定
void check(){
if(loc.x<0){loc.x=width;}
  if(loc.x>width){loc.x=0;}
if(loc.y<0){loc.y=height;}
if(loc.y>height){loc.y=0;}
}
}

```


![1](https://github.com/stream00/wxk-project4/blob/main/1.png)
![2](https://github.com/stream00/wxk-project4/blob/main/2.png)
![3](https://github.com/stream00/wxk-project4/blob/main/3.png)
![4](https://github.com/stream00/wxk-project4/blob/main/4.png)
![5](https://github.com/stream00/wxk-project4/blob/main/5.png)
![6](https://github.com/stream00/wxk-project4/blob/main/6.png)
![7](https://github.com/stream00/wxk-project4/blob/main/7.png)
![8](https://github.com/stream00/wxk-project4/blob/main/8.png)
```java
int t=8;
int frame=0;
PImage[] a=new PImage[t];
void setup() {
  size(800, 800);
  a[0]=loadImage("1.png");
  a[1]=loadImage("2.png");
  a[2]=loadImage("3.png");
  a[3]=loadImage("4.png");
  a[4]=loadImage("5.png");
  a[5]=loadImage("6.png");
  a[6]=loadImage("7.png");
  a[7]=loadImage("8.png");
}

void draw() {
  //fill(#FFE5C9);
  fill(255);
  rect(0, 0, width, height);
  image(a[0],300, 100);
 image(a[1],301, 105);
 image(a[2],302.2, 148);
  image(a[3],303.3, 140);
  image(a[4],303.7, 160);
  image(a[5],305.2, 130);
  image(a[6],305.7, 130);
  image(a[7],306.5, 130);
 // int n=second()%10;
  for(int i=0;i<100;i++){
  fill(#FFE5C9);
  noStroke();
  float m=map(mouseX,0,800,0,50);//用鼠标与map控制栅格移动
  rect(m+8*i,0,6.2,height);
  }
}

```







