float radius; //transient variable hahahaha
float radii = 70; //main radius variable
float x, y;
float px, py; //previous x and y
float n;
float [] points; //array containing y values of waveform
float time = 0;
float angle;
float control; //controls how many circles are present

//Control Variables
int clicked , clicked2;
float speedx, boxx;
float box_y, box2_y;

void setup(){
  size(800, 500);
  points = new float [220];
  clicked = 0;
  speedx = width - 770;
  boxx = width - 300;
  box_y = height - 30 - 7.5;
}


void draw(){
  background(255);
  x = 0;
  y = 0;

  controls();

  translate(200, 250);
  //Main circle drawing loop
  for (int i = 0; i < control; i++){
        px = x;
        py = y;

        n = i*2+1;
        radius = radii*(4 / (n*PI));
        x += radius*cos(n*angle);
        y += radius*sin(n*angle);

        //Main circle
        pushStyle();
        noFill();
        strokeWeight(0.60);
        stroke(0);
        circle(px, py, radius*2);
        popStyle();

        //Secondary circles;
        pushStyle();
        strokeWeight(0.5);
        fill(255,0,0);
        stroke(255,0,0);
        circle(x, y, radius/15);
        popStyle();

        //Line from circle to circle
        pushStyle();
        strokeWeight(5);
        stroke(255, 255, 0, 125);
        line(px, py, x, y);
        popStyle();
  }

  //The connecting line from circle to waveform
  pushStyle();
  strokeWeight(1.5);
  stroke(255, 0, 0, 125);
  line(x, y, 350, y);
  popStyle();

  //Waveform graphing

  translate(350, 0);
  for (int i = points.length-1; i > 0; i--) {
    points[i] = points[i-1];
  }
  points[0] = y;
  for (int i = 1; i < points.length; i++) {
    pushStyle();
    strokeWeight(2);
    stroke(0, 255, 0);
    line(i, points[i], i-1, points[i-1]);
    popStyle();
  }

  //Increasing angle over time
  angle += time;
}

void controls(){
  //Mapping of mouse movement to animations speeds ang circle numbers
  time = map(speedx, (width - 770), (width - 770 + 200), 0.01, 0.2);
  control = map(boxx, (width - 300), (width - 300 + 200), 1, 50);

  //Speed Control
  line(width - 770, height - 30, width - 770 + 200, height - 30);
  rect(speedx, height - 30 - 7.5, 15, 15);
  if (clicked == 1){
    speedx = mouseX;

    if (mouseX >= (width - 770 + 200)){
       speedx = width - 770 + 200;
    }
    if (mouseX <= (width - 770)){
       speedx = width - 770;
    }
  }

  //Circle Control
  line(width - 300, height - 30, width - 300 + 200, height - 30);
  rect(boxx, height - 30 - 7.5, 15, 15);
  if (clicked2 == 1){
    boxx = mouseX;

    if (mouseX >= (width - 300 + 200)){
       boxx = width - 300 + 200;
    }
    if (mouseX <= (width - 300)){
       boxx = width - 300;
    }
  }
}


//Speed Control
void mousePressed(){
  //Speed Control Logic
   if (mouseX >= speedx && mouseX <= speedx + 15){
       if (mouseY >= box_y && mouseY <= box_y + 15){
          clicked = 1;
       }
   }

  //Circle Control Logic
   if (mouseX >= boxx && mouseX <= boxx + 15){
       if (mouseY >= box_y && mouseY <= box_y + 15){
          clicked2 = 1;
       }
   }
}

void mouseReleased(){
  clicked = 0;
  clicked2 = 0;
}
