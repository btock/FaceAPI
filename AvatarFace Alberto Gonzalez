public class MonsterFace extends FaceGroup
{
  public MonsterFace(String id) {
    super(id);
    PShape s = createShape(ELLIPSE,40,0,200,200);
    s.setFill(color(255));
    s.setStroke(color(0)); 
    shape.addChild(s);
  }
}


public class MonsterEye extends AnimatedFeature
{
   public MonsterEye(String id, int x, int y) {
     super(id,x,y);
     open();
   }

   public PShape open() {
    shape = createShape(ELLIPSE,x,y,20,20);
    shape.setFill(color(0));
    shape.setStroke(color(0));
    return super.open();
  } 

  public PShape close() {
    shape = createShape(LINE,x-10,y+2,x+10,y+2);
    shape.setFill(color(0));
    shape.setStrokeWeight(4);
    shape.setStroke(color(250,0,0));
    return super.close();
  }  
}// this is the constructor from the MonsterEyeBrowR
public class MonsterEyebrowR extends AnimatedFeature //right eyebrow
{
   public MonsterEyebrowR(String id, int x, int y) {
     super(id,x,y);
     open();
   }

   public PShape open() {
    shape = createShape(RECT,x,y,24,5);
    shape.setFill(color(190));
    shape.setStroke(color(110,250));
    return super.open();
  } 

  public PShape close() {
    shape = createShape(TRIANGLE,x+55,y-6,x-29,y+36, x+33, y-6);//(TRIANGLE,x-55,y-36,x+59,y+10, x-43, y-38);
    shape.setFill(color(0));
    shape.setStrokeWeight(4);
    shape.setStroke(color(250,0,0));
    return super.close();
  }  
}
// this is the constructor from the MonsterEyeBrowL
public class MonsterEyebrowL extends AnimatedFeature //left eyebrow
{
   public MonsterEyebrowL(String id, int x, int y) {
     super(id,x,y);
     open();
   }

   public PShape open() {
    shape = createShape(RECT,x,y,24,5);
    shape.setFill(color(190));
    shape.setStroke(color(110,250));
    return super.open();
  } 

  public PShape close() {
    shape = createShape(TRIANGLE,x-55,y-36,x+59,y+10, x-43, y-38);
    shape.setFill(color(0));
    shape.setStrokeWeight(4);
    shape.setStroke(color(255,0,0));
    return super.close();
  }  
}// this part will add a RECT shape on the eyes in order to fire laser from his eyes
/*public class MonsterLaserR extends AnimatedFeature //laser light //
{
   public MonsterLaserR(String id, int x, int y) {
     super(id,x,y);
     open();
   }

   public PShape open() {
    shape = createShape(RECT,x+100,y,24,5);
    shape.setFill(color(0));
    shape.setStroke(color(0));
    return super.open();
  } 

  public PShape close() {
    shape = createShape(ELLIPSE,x-10,y+2,x+10,y+2);
    shape.setFill(color(0));
    shape.setStrokeWeight(4);
    shape.setStroke(color(250,0,0));
    return super.close();
  }  
}*/
// this is the constructor for the mouth in the AvatarFace
public class MonsterMouth extends AnimatedFeature
{  
   public MonsterMouth(String id, int x, int y) {
     super(id,x,y);
     open();
   }
  
   public PShape open() {
    shape = createShape();
    shape.beginShape(TRIANGLE_STRIP);
    shape.fill(255);
    shape.stroke(0);
    shape.vertex(20, 75);
    shape.vertex(30, 20);
    shape.vertex(40, 75);
    shape.vertex(50, 20);
    shape.vertex(60, 75);
    shape.vertex(70, 20);
    shape.vertex(80, 75);
    shape.endShape(CLOSE);
    return super.open();
  } 

  public PShape close() {
    shape = createShape(LINE,x+25,y+50,x+75,y+50);
    shape.setFill(color(0));
    shape.setStrokeWeight(4);
    shape.setStroke(color(250,0,0));
    return super.close();
  } 
}


public class AvatarFace
{
    MonsterEye ojoIzq;
    MonsterEye ojoDer;
  MonsterMouth boca;
   MonsterFace cara;
    //issue #1 ADD EYEBROWS LEFT AND RIGHT
   MonsterEyebrowR cejaR;
   MonsterEyebrowL cejaL;
   //MonsterLaserR LaserR;// THE AVATAR WILL SHOT LASER FROM HIS EYES
  
  public AvatarFace()
  {
    ojoIzq = new MonsterEye("ojoIzq",   0, 0);
    ojoDer = new MonsterEye("ojoDer", 100, 0);
      boca = new MonsterMouth("boca",   0, 0);
      cara = new MonsterFace("puppet");  
      cejaR = new MonsterEyebrowR("cejaR", 90, -30); //right eyebrow position
      cejaL = new MonsterEyebrowL("cejaL", -20, -30); //Left eyebrow position
      //LaserR = new MonsterLaserR("LaserR", -10, 0); position of the laser light
    cara.add(ojoIzq);
    cara.add(ojoDer);
    cara.add(boca);
    cara.add(cejaR);// ADD leftBrow in MonsterFace
    cara.add(cejaL);// ADD leftBrow in MonsterFace
    //cara.add(LaserR);
  }
 //the program starts draw the Avatar using the MonsterFace Class
  public void draw(int x, int y) {
    cara.position(x,y);
    cara.draw();

  }

  public BasicState status(FeatureID id) {
    if (id == FeatureID.LeftEye) {
        return ojoIzq.status();
    } else if (id == FeatureID.RightEye) {
        return ojoDer.status();      
    }
    return BasicState.Undefined;
  }
 // this void will perform all the Action when we click in the draw  
  public void change(FeatureID id, Action action)
  {
    // PS BUG no-enum-switch 
    if (id == FeatureID.LeftEye) { // ojo izq?
      if (action == Action.closeEye) {
          cara.replaceShape(ojoIzq.getID(),ojoIzq.close());
      } else {
          cara.replaceShape(ojoIzq.getID(),ojoIzq.open());
      }
     
    }else if (id == FeatureID.LeftBrow) { // Here start the ReplaceShape in LeftBrow
      if (action == Action.openEyeBrowL) {
          cara.replaceShape(cejaL.getID(),cejaL.close());// will replace the LeftBrow for another shape
      } else {
          cara.replaceShape(cejaL.getID(),cejaL.open());// will return the original state in LeftBrow
      } 
    }else if (id == FeatureID.RightBrow) {// Here start the ReplaceShape in RightBrow
      if (action == Action.openEyeBrowL) {
          cara.replaceShape(cejaR.getID(),cejaR.close());//will replace the LeftBrow for another shape
      } else {
          cara.replaceShape(cejaR.getID(),cejaR.open());   //will replace the RighBrow for another shape  
      }
      //Here start the Replace in the Eyes and boca, and with every click that we perform here the action will change the shape
    } else if (id == FeatureID.RightEye) { 
      if (action == Action.closeEye) {
          cara.replaceShape(ojoDer.getID(),ojoDer.close());
      } else {
          cara.replaceShape(ojoDer.getID(),ojoDer.open());
      } // if close
    } else if (id == FeatureID.Mouth) { // boca?
      if (action == Action.closeMouth) {
          cara.replaceShape(boca.getID(),boca.close());
      } else {
          cara.replaceShape(boca.getID(),boca.open());
      } // if close
    } // else
  } // change()
} // AvatarFace class
