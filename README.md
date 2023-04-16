# Datt3400---Cyber_Flow-
let cam;

var cubes = [];
var noiseS = 1
var dark = true;

let sound;


function preload() {
  sound = loadSound('ytmp3free.cc_clean-bandit-x-elley-duhe-dont-leave-me-lonely-official-video-youtubemp3free.org.mp3');
}

function setup() {
  createCanvas(500, 500, WEBGL);
  amplitude = new p5.Amplitude();
  sound.loop();
  sound.play();
  
  fft = new p5.FFT();
  
  createEasyCam();
  document.oncontextmenu = ()=>false;
  var unitS = width/20;
  //ortho(-width / 2, width / 2, -height / 2, height / 2, 0, 5000);
  
  //consider removing
  /*
  for(let i=0; i<1; i++){
   let col = color(255, 200);//255
    let cube = new Cube(0, createVector(random(-width/2, width/2), random(-height/2, height/2), random(-width*2, width/2)), col, height/400);
      cubes.push(cube);
  }
  */
  
  for(let x=-width/2; x<width/2; x+=unitS){
    for(let y=-width*2; y<width/2; y+=unitS){
    colorMode(RGB);
      let col = color(((y/width+2)*255/2.5)%255, 255, 255, 200);
      //let col = color(255, 200);
     if(random(10) < 1){
      let v = random(100, 0);
       col = color(255, v, v, 255);
     }
      //if(random(10) < 1){
       //let v = random(100, 0);
       // col = color(v, v, 255, 255);
     // }
       //if(random(10) < 1){
         //let v = random(255, 0);
         //col = color(255, 230, v, 255);
      //}
       if(random(10) < 1){
         let v = random(255, 0);
        col = color(v, 255, v, 255);
       }
      let cube = new Cube(random(unitS*2), createVector(x, height/2, y), col,random(height/100));
      cubes.push(cube);
      cube = new Cube(random(unitS*2), createVector(x, -height/2, y), col,random(height/100));
      cubes.push(cube);
    }
  }
  
}

function draw() {
  
  print(frameRate());
  
 perspective(PI / 4.0);
  //camera(-width/2, -height, -width/2, 0, 0, 0, 0, 1, 0);
  let level = amplitude.getLevel();
  let size = map(level, 0, 1, 0, 200);
    box(size,size,size);
  
  fill(255, 200);
  background(225);
  if(dark)background(0);//220
  
  let spectrum = fft.analyze();
  //print(spectrum.length);

  
  for(let i=0; i<cubes.length; i++){
  

  let level = amplitude.getLevel();
    let index = map(i,0,cubes.length,0,spectrum.length);
  //let size = map(level, 0, 1, 0, 200);
    
    let size = 0;
    
    let cube = cubes[i];
    cube.update();
    cube.show(spectrum[int(index)*0.5]);
    
    
    //box(size,size,size);

}

function togglePlay() {
  if (sound.isPlaying() ){
    sound.pause();
  } else {
    sound.loop();
		amplitude = new p5.Amplitude();
		amplitude.setInput(sound);
  }
}
  
}

function mousePressed() {
  dark = false;
  noiseS = random(0.5, 2); // randomly change the noise scale
  for (let i = 0; i < cubes.length; i++) {
    let cube = cubes[i];
    let d = dist(cube.pos.x, cube.pos.y, mouseX, mouseY);
    if (d < cube.size/2) { // check if the mouse is over the cube
      cubes.splice(i, 1); // remove the cube from the array
      i--;
    } else {
      cube.pos.x += random(-width/4, width/4); // randomly change the x position
      cube.pos.y += random(-height/4, height/4); // randomly change the y position
    }
  }
}


function mousePressed() {
  dark = false;
}

function mouseReleased() {
  dark = true;

}
function mousePressed() {
  dark = false;
 noiseS = random(0.5, 2); // randomly change the noise scale
  for (let i = 0; i < cubes.length; i++) {
    let cube = cubes[i];
    cube.pos.x += random(-width/4, width/4); // randomly change the x position
   cube.pos.y += random(-height/4, height/4); // randomly change the y position
}

}


class Cube {
  constructor(size, pos, col, sw) {
    this.size = size
    this.pos = pos
    this.off = createVector(0, 0, 0);
    this.col = col;//color
    this.sw = sw;//stroke weight
  }

  update(amp) {
    let noiseS = map(amp, 0, 1, 0.5, 3); // map amplitude to noise scale
    let zoff = noise(this.pos.x / width / noiseS, this.pos.z / width / noiseS, frameCount / 100.0) * TWO_PI;
    
    //commented out - try and revise or fix
    
    //this.pos.add(p5.Vector.fromAngle(zoff).mult(amp * 50)); // use amplitude to change movement range
    
    
    this.pos.z += 30;
    if (this.pos.z > width / 2) {
      this.off.x = (mouseX - width / 2) * 0.7;
      this.off.y = (mouseY - height / 2) * 0.7;
      this.pos.z = -width * 2;
    
    }
  }
  
  show(sizeupdate){
    fill(this.col);
    if(green(this.col) == 255 && dark)fill(0, 200);
    push();
    if(green(this.sw) == 255 && dark)fill(0, 200);
    stroke(0);//0
    if(dark)stroke(255, 200);
    strokeWeight(0.2);
    rotate(PI/2);
    rotate(frameCount/500.0);
    let zoff = noise(this.pos.x/width/noiseS, this.pos.z/width/noiseS, frameCount/100.0)*height/4-height/8
    
    let x = this.pos.x+this.off.x;
    let y = this.pos.y+this.off.y+zoff;
    let z = this.pos.z;
    
    translate(x,y,z);
    box(sizeupdate);
    strokeWeight(30);
    scale(1);
  box(sizeupdate/1.5);
    pop(50);
  }
}

function keyPressed() {
  if (key === 's') {
    setup();
  }
}
