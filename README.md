# wxk-project4
![2](https://github.com/stream00/wxk-project4/blob/main/2.jpg)


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






