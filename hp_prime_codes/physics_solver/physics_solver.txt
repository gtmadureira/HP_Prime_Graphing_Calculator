// 2015-11-21
// by: Gustavo Madureira
// gtmadureira@gmail.com

// This program will let you solve 139 physics equations for any variable within each equation.

#pragma mode( separator(.,;) integer(h32) )

physicscat01();
physicscat02();
kinematics();
atom();
circuits();
currents();
diffraction();
electric();
emfields();
energy();
forces();
gravity();
induction();
magnetic();
matter();
mirrors();
miscellaneous();
momentum();
motion2d();
quantum();
reflection();
thermal();
vectors();
velocity();
waves();
work();


EXPORT PHSOLVER() //******** splash program ********
BEGIN
IF MSGBOX(CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+" Physics Solver© "
          +CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)
          +CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)
          +" • by: Gustavo Madureira "+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)
          +CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+CHAR(32)+" • gtmadureira@gmail.com ",1)==1 THEN
 
physicscat01(); ELSE
RETURN "GOOD BYE";
END;
END; //******** end splash program ********


physicscat01() //******** category selection - first page ********
BEGIN
LOCAL ch;
CHOOSE(ch,"Physics Solver"," ♦ QUIT ♦ ","  • Kinematics ","  • Atoms ","  • Circuits ","  • Electrical Currents ",
          "  • Diffra. & Interf. of Light ","  • Electric Fields ","  • Electric & Magnetic Fields ","  • Energy ",
          "  • Forces ","  • Universal Gravitation ","  • Electromagnetic Induction ","  • Magnetic Fields "," ❱❱❱ NEXT ❱❱❱ ");
CASE
IF ch==1  THEN RETURN "GOOD BYE"; END;
IF ch==2  THEN kinematics();      END;
IF ch==3  THEN atom();            END;
IF ch==4  THEN circuits();        END;
IF ch==5  THEN currents();        END;
IF ch==6  THEN diffraction();     END;
IF ch==7  THEN electric();        END;
IF ch==8  THEN emfields();        END;
IF ch==9  THEN energy();          END;
IF ch==10 THEN forces();          END;
IF ch==11 THEN gravity();         END;
IF ch==12 THEN induction();       END;
IF ch==13 THEN magnetic();        END;
IF ch==14 THEN physicscat02();    END;
DEFAULT
RETURN "GOOD BYE";
END;
END; //******** end category selection - first page ********


physicscat02() //******** category selection - second page ********
BEGIN
LOCAL ch;
CHOOSE(ch,"Physics Solver"," ❰❰❰ BACK ❰❰❰ ","  • States of Matter ","  • Mirrors & Lenses ","  • Miscellaneous ","  • Momentum ",
          "  • Motion 2D ","  • Quantum Theory ","  • Reflection & Refraction ","  • Thermal Energy ","  • Vectors ","  • Velocity ",
          "  • Waves ","  • Work "," ♦ QUIT ♦ ");
CASE
IF ch==1  THEN physicscat01();    END;
IF ch==2  THEN matter();          END;
IF ch==3  THEN mirrors();         END;
IF ch==4  THEN miscellaneous();   END;
IF ch==5  THEN momentum();        END;
IF ch==6  THEN motion2d();        END;
IF ch==7  THEN quantum();         END;
IF ch==8  THEN reflection();      END;
IF ch==9  THEN thermal();         END;
IF ch==10 THEN vectors();         END;
IF ch==11 THEN velocity();        END;
IF ch==12 THEN waves();           END;
IF ch==13 THEN work();            END;
IF ch==14 THEN RETURN "GOOD BYE"; END;
DEFAULT
RETURN "GOOD BYE";
END;
END; //******** end category selection - second page ********


//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#----------------------------------------------------   BEGIN KINEMATICS PROGRAM ---------------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################
kinematics()
BEGIN

LOCAL ch0,ch1,stack;
LOCAL ā,v,v₀,a,t,t₀,s;
LOCAL S0,S1,S2,S3;

CHOOSE(ch0,"Kinematics"," ❰❰❰ BACK ❰❰❰ ","  ā = (v-v₀)/(t-t₀) ",   
           "  v = v₀+at ","  s = [(v₀+v)/2]*t ","  s = (v₀*t)+1/2*(a*t²) ",
           "  v² = v₀²+2*a*s ");

CASE

//*************************************************************************************************************************************
IF ch0==1 THEN physicscat01(); END; //*************************************************************************************************
//*************************************************************************************************************************************

//*************************************************************************************************************************************
IF ch0==2 THEN
  CHOOSE(ch1,"ā=(v-v₀)/(t-t₀)"," ❰❰❰ BACK ❰❰❰ ","  Solve → ā ",   
             "  Solve → v ","  Solve → v₀ ","  Solve → t ","  Solve → t₀ ");

 CASE


  
IF ch1==1 THEN
kinematics();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{v,[0],{30,40,1}},{v₀,[0],{30,40,2}},{t,[0],{30,40,3}},{t₀,[0],{30,40,4}},{stack,0,{85,0,6}}},
         "Solving → Average Acceleration",{"v: ","v₀: ","t: ","t₀: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s).","Enter 'Initial Velocity'_(m/s).",
         "Enter 'Final Time'_(s).","Enter 'Initial Time'_(s).",
         "Put 'Avg. Acceleration'_(m/s²) on the stack ?"},{0,0,0,0,0},{0,0,0,0,0});
    
S1:=±∞ _(m/s²);
S2:=0 _(m/s²);

 IF (v-v₀)==0 AND (t-t₀)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("ā = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF (t-t₀)==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("ā = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE

   ā:=(v-v₀)/(t-t₀);
   S0:="ā = "+ā _(m/s²);
   
   IF stack==1 THEN RETURN ā _(m/s²); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;
   
   END;
  
  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{ā,[0],{30,40,1}},{t,[0],{30,40,2}},{t₀,[0],{30,40,3}},{v₀,[0],{30,40,4}},{stack,0,{85,0,6}}},
         "Solving → Final Velocity",{"ā: ","t: ","t₀: ","v₀: ","Stack ? "},
        {"Enter 'Avg. Acceleration'_(m/s²).","Enter 'Final Time'_(s).",
         "Enter 'Initial Time'_(s).","Enter 'Initial Velocity'_(m/s).",
         "Put 'Final Velocity'_(m/s) on the stack ?"},{0,0,0,0,0},{0,0,0,0,0});
 
 v:=ā*(t-t₀)+v₀;
 S0:="v = "+v _(m/s);
   
 IF stack==1 THEN RETURN v _(m/s); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";

  END;
   
 END;
  
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{v,[0],{30,40,1}},{ā,[0],{30,40,2}},{t,[0],{30,40,3}},{t₀,[0],{30,40,4}},{stack,0,{85,0,6}}},
         "Solving → Initial Velocity",{"v: ","ā: ","t: ","t₀: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s).","Enter 'Avg. Acceleration'_(m/s²).",
         "Enter 'Final Time'_(s).","Enter 'Initial Time'_(s).",
         "Put 'Initial Velocity'_(m/s) on the stack ?"},{0,0,0,0,0},{0,0,0,0,0});
 
 v₀:=v-ā*(t-t₀);
 S0:="v₀ = "+v₀ _(m/s);
   
 IF stack==1 THEN RETURN v₀ _(m/s); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";

  END;
   
 END;
  
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{v,[0],{30,40,1}},{v₀,[0],{30,40,2}},{ā,[0],{30,40,3}},{t₀,[0],{30,40,4}},{stack,0,{85,0,6}}},
         "Solving → Final Time",{"v: ","v₀: ","ā: ","t₀: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s).","Enter 'Initial Velocity'_(m/s).",
         "Enter 'Avg. Acceleration'_(m/s²).","Enter 'Initial Time'_(s).",
         "Put 'Final Time'_(s) on the stack ?"},{0,0,0,0,0},{0,0,0,0,0});
 
S1:=±∞ _(s);
S2:=0 _(s);

 IF (v-v₀)==0 AND ā==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("t = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF ā==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("t = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE

   t:=((v-v₀)/ā)+t₀;
   S0:="t = "+t _(s);
   
   IF stack==1 THEN RETURN t _(s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;
   
   END;
  
  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==6 THEN
 INPUT({{t,[0],{30,40,1}},{v,[0],{30,40,2}},{v₀,[0],{30,40,3}},{ā,[0],{30,40,4}},{stack,0,{85,0,6}}},
         "Solving → Initial Time",{"t: ","v: ","v₀: ","ā: ","Stack ? "},
        {"Enter 'Final Time'_(s).","Enter 'Final Velocity'_(m/s).",
         "Enter 'Initial Velocity'_(m/s).","Enter 'Avg. Acceleration'_(m/s²).",
         "Put 'Initial Time'_(s) on the stack ?"},{0,0,0,0,0},{0,0,0,0,0});
 
S1:=±∞ _(s);
S2:=0 _(s);

 IF (v-v₀)==0 AND ā==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("t₀ = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF ā==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("t₀ = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE

   t₀:=t-((v-v₀)/ā);
   S0:="t₀ = "+t₀ _(s);
   
   IF stack==1 THEN RETURN t₀ _(s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;
   
   END;
  
  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==3 THEN
  CHOOSE(ch1,"v=v₀+at"," ❰❰❰ BACK ❰❰❰ ","  Solve → v ",   
             "  Solve → v₀ ","  Solve → a ","  Solve → t ");

 CASE


IF ch1==1 THEN
 kinematics();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{v₀,[0],{30,40,1}},{a,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Final Velocity",{"v₀: ","a: ","t: ","Stack ? "},
        {"Enter 'Initial Velocity'_(m/s)","Enter 'Acceleration'_(m/s²).",
         "Enter 'Time'_(s).","Put 'Final Velocity'_(m/s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 v:=v₀+a*t;
 S0:="v = "+v _(m/s);

 IF stack==1 THEN RETURN v _(m/s); ELSE
   
  IF MSGBOX(S0,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{v,[0],{30,40,1}},{a,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Initial Velocity",{"v: ","a: ","t: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s)","Enter 'Acceleration'_(m/s²).",
         "Enter 'Time'_(s).","Put 'Initial Velocity'_(m/s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 v₀:=v-a*t;
 S0:="v₀ = "+v₀ _(m/s);
  
 IF stack==1 THEN RETURN v₀ _(m/s); ELSE
 
  IF MSGBOX(S0,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{v,[0],{30,40,1}},{v₀,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Acceleration",{"v: ","v₀: ","t: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s)","Enter 'Initial Velocity'_(m/s).",
         "Enter 'Time'_(s).","Put 'Acceleration'_(m/s²) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(m/s²);
S2:=0 _(m/s²);
 
 IF (v-v₀)==0 AND t==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("a = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF t==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("a = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   a:=(v-v₀)/t;
   S0:="a = "+a _(m/s²);

   IF stack==1 THEN RETURN a _(m/s²); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;  
  
 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{v,[0],{30,40,1}},{v₀,[0],{30,40,2}},{a,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Time",{"v: ","v₀: ","a: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s)","Enter 'Initial Velocity'_(m/s).",
         "Enter 'Acceleratiob'_(m/s²).","Put 'Time'_(s) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(s);
S2:=0 _(s);
 
 IF (v-v₀)==0 AND a==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("t = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF a==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("t = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   t:=(v-v₀)/a;
   S0:="t = "+t _(s);

   IF stack==1 THEN RETURN t _(s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;  
  
 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==4 THEN
  CHOOSE(ch1,"s = [(v₀+v)/2]*t"," ❰❰❰ BACK ❰❰❰ ","  Solve → s ",   
             "  Solve → v₀ ","  Solve → v ","  Solve → t ");

 CASE


IF ch1==1 THEN
 kinematics();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{v₀,[0],{30,40,1}},{v,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Displacemnet",{"v₀: ","v: ","t: ","Stack ? "},
        {"Enter 'Initial Velocity'_(m/s).","Enter 'Final Velocity'_(m/s).",
         "Enter 'Time'_(s).","Put 'Displacement'_(m) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 s:=((v₀+v)/2)*t;
 S0:="s = "+s _(s);

 IF stack==1 THEN RETURN s _(s); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{s,[0],{30,40,1}},{t,[0],{30,40,2}},{v,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Initial Velocity",{"s: ","t: ","v: ","Stack ? "},
        {"Enter 'Displacement'_(m).","Enter 'Time'_(s).","Enter 'Final Velocity'_(m/s).",
         "Put 'Initial Velocity'_(m/s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S1:=±∞ _(m/s);
S2:=0 _(m/s);
 
 IF (2*s)==0 AND t==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("v₀ = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF t==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("v₀ = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   v₀:=((2*s)/t)-v;
   S0:="v₀ = "+v₀ _(m/s);

   IF stack==1 THEN RETURN v₀ _(m/s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;  
  
 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{s,[0],{30,40,1}},{t,[0],{30,40,2}},{v₀,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Final Velocity",{"s: ","t: ","v₀: ","Stack ? "},
        {"Enter 'Displacement'_(m).","Enter 'Time'_(s).","Enter 'Initial Velocity'_(m/s).",
         "Put 'Final Velocity'_(m/s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S1:=±∞ _(m/s);
S2:=0 _(m/s);
 
 IF (2*s)==0 AND t==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("v = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF t==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("v = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   v:=((2*s)/t)-v₀;
   S0:="v = "+v _(m/s);

   IF stack==1 THEN RETURN v _(m/s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;  
  
 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{s,[0],{30,40,1}},{v₀,[0],{30,40,2}},{v,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Time",{"s: ","v₀: ","v: ","Stack ? "},
        {"Enter 'Displacement'_(m).","Enter 'Initial Velocity'_(m/s).",
         "Enter 'Final Velocity'_(m/s).","Put 'Time'_(s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S1:=±∞ _(s);
S2:=0 _(s);
 
 IF (2*s)==0 AND (v₀+v)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("t = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF (v₀+v)==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("t = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   t:=(2*s)/(v₀+v);
   S0:="t = "+t _(s);

   IF stack==1 THEN RETURN t _(s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;  
  
 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==5 THEN
  CHOOSE(ch1,"s = (v₀*t)+1/2*(a*t²)"," ❰❰❰ BACK ❰❰❰ ","  Solve → s ",   
             "  Solve → v₀ ","  Solve → t ","  Solve → a ");

 CASE


IF ch1==1 THEN
 kinematics();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{v₀,[0],{30,40,1}},{t,[0],{30,40,2}},{a,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Displacement",{"v₀: ","t: ","a: ","Stack ? "},
        {"Enter 'Initial Velocity'_(m/s).","Enter 'Time'_(s).","Enter 'Acceleration'_(m/s²).",
         "Put 'Displacement'_(m) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 s:=(v₀*t)+1/2*(a*t²);
 S0:="s = "+s _(m);

 IF stack==1 THEN RETURN s _(m); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{s,[0],{30,40,1}},{t,[0],{30,40,2}},{a,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Initial Velocity",{"s: ","t: ","a: ","Stack ? "},
        {"Enter 'Displacement'_(m).","Enter 'Time'_(s).","Enter 'Acceleration'_(m/s²).",
         "Put 'Initial Velocity'_(m/s) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(m/s);
S2:=0 _(m/s);
 
 IF (2*s-t²*a)==0 AND (2*t)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("v₀ = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF (2*t)==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("v₀ = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   v₀:=(2*s-t²*a)/(2*t);
   S0:="v₀ = "+v₀ _(m/s);

   IF stack==1 THEN RETURN v₀ _(m/s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{s,[0],{30,40,1}},{a,[0],{30,40,2}},{v₀,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Time",{"s: ","a: ","v₀: ","Stack ? "},
        {"Enter 'Displacement'_(m).","Enter 'Acceleration'_(m/s²).","Enter 'Initial Velocity'_(m/s).",
         "Put 'Time'_(s) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(s);
S2:=0 _(s);
S3:="Result is not real!";

 IF (2*s*a+v₀²)<0 THEN

  IF MSGBOX("t = "+S3,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";
     
  END;
 
 ELSE
 
  IF (√(2*s*a+v₀²)-v₀)==0 AND (a)==0 THEN

   IF stack==1 THEN RETURN S2; ELSE
   
     IF MSGBOX("t = "+S2,1)==1 THEN

      kinematics(); ELSE

      RETURN "GOOD BYE";

     END;

    END;

  ELSE

   IF (a)==0 THEN   
    
    IF stack==1 THEN RETURN S1; ELSE
   
     IF MSGBOX("t = "+S1,1)==1 THEN

      kinematics(); ELSE

      RETURN "GOOD BYE";

     END;

    END;

   ELSE
    
    t:=(√(2*s*a+v₀²)-v₀)/a;
    S0:="t = "+t _(s);

    IF stack==1 THEN RETURN t _(s); ELSE
     
     IF MSGBOX(S0,1)==1 THEN

      kinematics(); ELSE

      RETURN "GOOD BYE";

     END;

    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{s,[0],{30,40,1}},{v₀,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Acceleration",{"s: ","v₀: ","t: ","Stack ? "},
        {"Enter 'Displacement'_(m).","Enter 'Initial Velocity'_(m/s).","Enter 'Time'_(s).",
         "Put 'Acceleration'_(m/s²) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(m/s²);
S2:=0 _(m/s²);
 
 IF (2*(s-v₀*t))==0 AND t²==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("a = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF t²==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("a = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   a:=(2*(s-v₀*t))/t²;
   S0:="a = "+a _(m/s²);

   IF stack==1 THEN RETURN a _(m/s²); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==6 THEN
  CHOOSE(ch1,"v² = v₀²+2*a*s"," ❰❰❰ BACK ❰❰❰ ","  Solve → v ",   
             "  Solve → v₀ ","  Solve → a ","  Solve → s ");

 CASE


IF ch1==1 THEN
 kinematics();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{v₀,[0],{30,40,1}},{a,[0],{30,40,2}},{s,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Final Velocity",{"v₀: ","a: ","s: ","Stack ? "},
        {"Enter 'Initial Velocity'_(m/s).","Enter 'Acceleration'_(m/s²).",
         "Enter 'Displacement'_(m).","Put 'Final Velocity'_(m/s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S3:="Result is not real!";

 IF (v₀²+2*a*s)<0 THEN
   
  IF MSGBOX(S3,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";

  END;
 
 ELSE

  v:=√(v₀²+2*a*s);
  S0:="v = "+v _(m/s);

  IF stack==1 THEN RETURN v _(m/s); ELSE
   
   IF MSGBOX(S0,1)==1 THEN

    kinematics(); ELSE

    RETURN "GOOD BYE";

   END;

  END;
 
 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{v,[0],{30,40,1}},{a,[0],{30,40,2}},{s,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Initial Velocity",{"v: ","a: ","s: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s).","Enter 'Acceleration'_(m/s²).",
         "Enter 'Displacement'_(m).","Put 'Initial Velocity'_(m/s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S3:="Result is not real!";

 IF (v²-2*a*s)<0 THEN
         
  IF MSGBOX(S3,1)==1 THEN

   kinematics(); ELSE

   RETURN "GOOD BYE";

  END;

 ELSE

  v₀:=√(v²-2*a*s);
  S0:="v₀ = "+v₀ _(m/s);

  IF stack==1 THEN RETURN v₀ _(m/s); ELSE
   
   IF MSGBOX(S0,1)==1 THEN

    kinematics(); ELSE

    RETURN "GOOD BYE";

   END;

  END;
 
 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{v,[0],{30,40,1}},{v₀,[0],{30,40,2}},{s,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Acceleration",{"v: ","v₀: ","s: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s).","Enter 'Initial Velocity'_(m/s).",
         "Enter 'Displacement'_(m).","Put 'Acceleration'_(m/s²) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(m/s²);
S2:=0 _(m/s²);
 
 IF (v²-v₀²)==0 AND s==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("a = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF s==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("a = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   a:=(v²-v₀²)/(2*s);
   S0:="a = "+a _(m/s²);

   IF stack==1 THEN RETURN a _(m/s²); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{v,[0],{30,40,1}},{v₀,[0],{30,40,2}},{a,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Displacement",{"v: ","v₀: ","a: ","Stack ? "},
        {"Enter 'Final Velocity'_(m/s).","Enter 'Initial Velocity'_(m/s).",
         "Enter 'Acceleration'_(m/s²).","Put 'Displacement'_(m) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(m);
S2:=0 _(m);
 
 IF (v²-v₀²)==0 AND a==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("s = "+S2,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF a==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("s = "+S1,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   s:=(v²-v₀²)/(2*a);
   S0:="s = "+s _(m);

   IF stack==1 THEN RETURN s _(m); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     kinematics(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************


DEFAULT
  RETURN "GOOD BYE";

END;

END;
//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#-----------------------------------------------------  END KINEMATICS PROGRAM  ----------------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################



//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#--------------------------------------------------------- BEGIN ATOMS PROGRAM -----------------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################
atom()
BEGIN

LOCAL ch0,ch1,stack,unit;
LOCAL m,q,r,n,v,μ;
LOCAL En,a₀,me,e,z,eV;
LOCAL S0,S1,S2,S3,S4;

LOCAL k:=9.0*10^9;
LOCAL h:=6.62606957*10^-34;
LOCAL ε₀:=8.854187817*10^-12;

CHOOSE(ch0,"Atoms"," ❰❰❰ BACK ❰❰❰ "," k*(q²/r²) = m*(v²/r) "," a₀ = (ε₀*h²)/(π*me*e²) ",
           " En = -(μ*e⁴*z²)/(8*ε₀²*h²*n²) ");

CASE

//*************************************************************************************************************************************
IF ch0==1 THEN physicscat01(); END; //*************************************************************************************************
//*************************************************************************************************************************************

//*************************************************************************************************************************************
IF ch0==2 THEN
  CHOOSE(ch1,"k*q²/r² = m*v²/r"," ❰❰❰ BACK ❰❰❰ ","  Solve → m ",   
             "  Solve → q ","  Solve → r ","  Solve → v ");

 CASE


  
IF ch1==1 THEN
atom();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{q,[0],{30,40,1}},{r,[0],{30,40,2}},{v,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Mass",{"q: ","r: ","v: ","Stack ? "},
        {"Enter 'Electric Charge'_(C).","Enter 'Radius'_(m).","Enter 'Centripetal Velocity'_(m/s).",
         "Put 'Mass'_(kg) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S1:=±∞ _(kg);
S2:=0 _(kg);

 IF (k*q²)==0 AND (r*v²)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("m = "+S2,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF (r*v²)==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("m = "+S1,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE

   m:=(k*q²)/(r*v²);
   S0:="m = "+m _(kg);
   
   IF stack==1 THEN RETURN m _(kg); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;
   
   END;
  
  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{m,[0],{30,40,1}},{r,[0],{30,40,2}},{v,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Electric Charge",{"m: ","r: ","v: ","Stack ? "},
        {"Enter 'Mass'_(kg).","Enter 'Radius'_(m).","Enter 'Centripetal Velocity'_(m/s).",
         "Put 'Electric Charge'_(C) on the stack ?"},{0,0,0,0},{0,0,0,0});
 
S2:=0 _(C);
S3:="Result is not real!";

 IF v==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
   IF MSGBOX("q = "+S2,1)==1 THEN

    atom(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE

  IF ((m*r*v²)/k)<0 THEN

   IF stack==1 THEN RETURN S3; ELSE
   
    IF MSGBOX("q = "+S3,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;
 
  ELSE  
    
   q:=√((m*r)/k)*v;
   S0:="q = "+q _(C);
  
   IF stack==1 THEN RETURN q _(C); ELSE
     
    IF MSGBOX(S0,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{q,[0],{30,40,1}},{m,[0],{30,40,2}},{v,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Radius",{"q: ","m: ","v: ","Stack ? "},
        {"Enter 'Electric Charge'_(C).","Enter 'Mass'_(kg).","Enter 'Centripetal Velocity'_(m/s).",
         "Put 'Radius'_(m) on the stack ?"},{0,0,0,0},{0,0,0,0});
 
S1:=±∞ _(m);
S2:=0 _(m);

 IF (k*q²)==0 AND (m*v²)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("r = "+S2,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF (m*v²)==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("r = "+S1,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE

   r:=(k*q²)/(m*v²);
   S0:="r = "+r _(m);
   
   IF stack==1 THEN RETURN r _(m); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;
   
   END;
  
  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{q,[0],{30,40,1}},{m,[0],{30,40,2}},{r,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Centripetal Velocity",{"q: ","m: ","r: ","Stack ? "},
        {"Enter 'Electric Charge'_(C).","Enter 'Mass'_(kg).","Enter 'Radius'_(m).",
         "Put 'Centripetal Velocity'_(m/s) on the stack ?"},{0,0,0,0},{0,0,0,0});
 
S1:=±∞ _(m/s);
S2:=0 _(m/s);
S3:="Result is not real!";

 IF q==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
   IF MSGBOX("v = "+S2,1)==1 THEN

    atom(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE

  IF ((k*q²)/(m*r))<0 THEN

   IF stack==1 THEN RETURN S3; ELSE
   
    IF MSGBOX("v = "+S3,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;
 
  ELSE  
 
   IF (m*r)==0 THEN
   
    IF stack==1 THEN RETURN S1; ELSE
   
     IF MSGBOX("v = "+S1,1)==1 THEN

      atom(); ELSE

      RETURN "GOOD BYE";

     END;

    END;

   ELSE
   
    v:=q*√(k/(m*r));
    S0:="v = "+v _(m/s);
  
    IF stack==1 THEN RETURN v _(m/s); ELSE
     
     IF MSGBOX(S0,1)==1 THEN

      atom(); ELSE

      RETURN "GOOD BYE";

     END;

    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==3 THEN
  CHOOSE(ch1,"a₀ = (ε₀*h²)/(π*me*e²)"," ❰❰❰ BACK ❰❰❰ ","  Solve → a₀ ",   
             "  Solve → me ","  Solve → e ");

 CASE


IF ch1==1 THEN
 atom();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{me,[0],{30,40,1}},{e,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Borh Radius",{"me: ","e: ","Stack ? "},
        {"Enter 'Electron Mass'_(kg)","Enter 'Electronic Charge'_(C).",
         "Put 'Borh Radius'_(m) on the stack ?"},{0,0,0},{0,0,0});

S2:=±∞ _(m);

 IF (π*me*e²)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE

   IF MSGBOX("a₀ = "+S2,1)==1 THEN

    atom(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE
 
  a₀:=(ε₀*h²)/(π*me*e²);
  S0:="a₀ = "+a₀ _(m);

  IF stack==1 THEN RETURN a₀ _(m); ELSE
   
   IF MSGBOX(S0,1)==1 THEN

    atom(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{a₀,[0],{30,40,1}},{e,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electron Mass",{"a₀: ","e: ","Stack ? "},
        {"Enter 'Borh Radius'_(m)","Enter 'Electronic Charge'_(C).",
         "Put 'Electron Mass'_(kg) on the stack ?"},{0,0,0},{0,0,0});
  
S1:=±∞ _(kg);

 IF (a₀*π*e²)==0 THEN

  IF stack==1 THEN RETURN S1; ELSE

   IF MSGBOX("me = "+S1,1)==1 THEN

    atom(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE
  
  me:=(ε₀*h²)/(a₀*π*e²);
  S0:="me = "+me _(kg);

  IF stack==1 THEN RETURN me _(kg); ELSE
   
   IF MSGBOX(S0,1)==1 THEN

    atom(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 END; 
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{a₀,[0],{30,40,1}},{me,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electronic Charge",{"a₀: ","me: ","Stack ? "},
        {"Enter 'Borh Radius'_(m)","Enter 'Electron Mass'_(kg).",
         "Put 'Electronic Charge'_(C) on the stack ?"},{0,0,0},{0,0,0});

S1:=±∞ _(C);
S3:="Result is not real!";
 
 IF a₀==0 AND me==0 THEN

  IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("e = "+S1,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF ((ε₀*h²)/(a₀*π*me))<0 THEN   
       
   IF MSGBOX("e = "+S3,1)==1 THEN

    atom(); ELSE

    RETURN "GOOD BYE";

   END;

  ELSE
    
   e:=√(ε₀/(a₀*π*me))*h;
   S0:="e = "+e _(C);

   IF stack==1 THEN RETURN e _(C); ELSE

    IF MSGBOX(S0,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;  
  
 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==4 THEN
  CHOOSE(ch1,"En = -(μ*e⁴*z²)/(8*ε₀²*h²*n²)","  ❰❰❰ BACK ❰❰❰ ","  Solve → En ",   
             "  Solve → μ ","  Solve → e ");

 CASE


IF ch1==1 THEN
 atom();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{μ,[0],{30,40,0}},{e,[0],{30,40,1}},{z,[0],{30,40,2}},{n,[0],{30,40,3}},
        {unit,{"Joule _(J)","Electron•Volt _(eV)"},{15,45,5}},{stack,0,{85,0,5}}},
         "Solving → Total Energy",{"μ: ","e: ","z: ","n: ","Unit: ","Stack ? "},
        {"Enter 'Reduced Mass'_(kg).","Enter 'Electronic Charge'_(C).",
         "Enter 'Atomic Number' ( Integers  z≥1 ).","Enter 'Principal Quantum Number' ( Integers n≥1 ).",
         "Select the Unit Type!","Put 'Total Energy' on the stack ?"},{0,0,0,0,0,0},{0,0,0,0,0,0});

eV:=6.241509*10^18;
S3:="Restriction: The Pricipal Quantum Number 'n' and Atomic Number 'z' need to be ( Integers n,z ≥ 1 ).";

 IF n<1 OR z<1 THEN 
   
  IF MSGBOX(S3,1)==1 THEN

   atom(); ELSE

   RETURN "GOOD BYE";

  END;

 ELSE 

  IF unit==1 THEN
    
   En:=-(μ*e^4*z²)/(8*ε₀²*h²*n²);
   S0:="En = "+En _(J);
 
   IF stack==1 THEN RETURN En _(J); ELSE
  
    IF MSGBOX(S0,1)==1 THEN

     atom(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE

   En:=(-(μ*e^4*z²)/(8*ε₀²*h²*n²))*eV;
   S0:="En = "+En _(eV);
 
   IF stack==1 THEN RETURN En _(eV); ELSE
  
    IF MSGBOX(S0,1)==1 THEN

     atom(); ELSE
  
     RETURN "GOOD BYE";
 
    END;

   END;
  
  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{En,[0],{30,40,0}},{e,[0],{30,40,1}},{z,[0],{30,40,2}},{n,[0],{30,40,3}},
        {stack,0,{85,0,5}}},"Solving → Reducded Mass",{"En: ","e: ","z: ","n: ","Stack ? "},
        {"Enter 'Total Energy'_(J).","Enter 'Electronic Charge'_(C).","Enter 'Atomic Number' ( Integers  z≥1 ).",
         "Enter 'Principal Quantum Number' ( Integers n≥1 ).","Put 'Reduced Mass'_(kg) on the stack ?"},{0,0,0,0,0},{0,0,0,0,0});

S3:="Restriction: The Pricipal Quantum Number 'n' and Atomic Number 'z' need to be ( Integers n,z ≥ 1 ).";

 IF n<1 OR z<1 THEN 
   
  IF MSGBOX(S3,1)==1 THEN

   atom(); ELSE

   RETURN "GOOD BYE";

  END;

 ELSE

  IF En==0 AND e==0 THEN μ:=0; END;
  IF En≠0 AND e==0 THEN μ:=±∞; END;
  IF e≠0 THEN μ:=-(8*En*ε₀²*h²*n²)/(e^4*z²); END;
 
 END; 

 S0:="μ = "+μ _(kg);

 IF stack==1 THEN RETURN μ _(kg); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   atom(); ELSE

   RETURN "GOOD BYE";

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{En,[0],{30,40,0}},{μ,[0],{30,40,1}},{z,[0],{30,40,2}},{n,[0],{30,40,3}},
        {stack,0,{85,0,5}}},"Solving → Electronic Charge",{"En: ","μ: ","z: ","n: ","Stack ? "},
        {"Enter 'Total Energy'_(J).","Enter 'Reduced Mass'_(kg).","Enter 'Atomic Number' ( Integers  z≥1 ).",
         "Enter 'Principal Quantum Number' ( Integers n≥1 ).","Put 'Electronic Charge'_(C) on the stack ?"},{0,0,0,0,0},{0,0,0,0,0});

S2:="Result is not real!";    
S3:="Restriction: The Pricipal Quantum Number 'n' and Atomic Number 'z' need to be ( Integers n,z ≥ 1 ).";
 
 IF n<1 OR z<1 THEN 
   
  IF MSGBOX(S3,1)==1 THEN

   atom(); ELSE

   RETURN "GOOD BYE";

  END;

 ELSE

  IF En==0 AND μ==0 THEN e:=0; END;
  IF En≠0 AND μ==0 THEN e:=±∞; END;
  IF En>0 AND μ>0 THEN IF MSGBOX(S2,1)==1 THEN atom(); ELSE RETURN "GOOD BYE"; END; END;
  IF μ≠0 THEN e:=(((-En/μ)^(1/4))*√(ε₀)*√(h)*√(n)*(2^(3/4)))/√(z); END;
 
 END; 

 S0:="e = "+e _(C);

 IF stack==1 THEN RETURN e _(C); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   atom(); ELSE

   RETURN "GOOD BYE";

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************

DEFAULT
  RETURN "GOOD BYE";

END;

END;
//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#--------------------------------------------------------- END ATOMS PROGRAM -------------------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################






//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#------------------------------------------------------- BEGIN CIRCUITS PROGRAM ----------------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################
circuits()
BEGIN

LOCAL ch0,ch1,stack;
LOCAL I,V,R,V₀,R₁;
LOCAL R₂,R₃,V₁,V₂,V₃;
LOCAL S0,S1,S2;

CHOOSE(ch0,"Circuits"," ❰❰❰ BACK ❰❰❰ ","  I = V/R ","  V₀ = (V*R₂)/(R₁+R₂) ",
           "  R = R₁+R₂+R₃ ","  V = V₁+V₂+V₃ ","  R = R₁+R₂+R₃ ");

CASE

//*************************************************************************************************************************************
IF ch0==1 THEN physicscat01(); END; //*************************************************************************************************
//*************************************************************************************************************************************

//*************************************************************************************************************************************
IF ch0==2 THEN
  CHOOSE(ch1,"I = V/R"," ❰❰❰ BACK ❰❰❰ ","  Solve → I ",   
             "  Solve → V ","  Solve → R ");

 CASE


  
IF ch1==1 THEN
circuits();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{V,[0],{30,40,1}},{R,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Current",{"V: ","R: ","Stack ? "},
        {"Enter 'Voltage'_(V).","Enter 'Resistence'_(Ohm).",
         "Put 'Current'_(A) on the stack ?"},{0,0,0},{0,0,0});

S1:=±∞ _(A);
S2:=0 _(A); 

 IF V==0 AND R==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("I = "+S2,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

  ELSE

   IF R==0 THEN

    IF stack==1 THEN RETURN S1; ELSE
    
     IF MSGBOX("I = "+S1,1)==1 THEN

      circuits(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   ELSE
    
    I:=V/R;
    S0:="I = "+I _(A);
   
    IF stack==1 THEN RETURN I _(A); ELSE
    
     IF MSGBOX(S0,1)==1 THEN

      circuits(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   END;

  END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{R,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Voltage",{"R: ","I: ","Stack ? "},
        {"Enter 'Resistence'_(Ohm).","Enter 'Current'_(A).",
         "Put 'Voltage'_(V) on the stack ?"},{0,0,0},{0,0,0});
    
 V:=R*I;
 S0:="V = "+V _(V);
   
 IF stack==1 THEN RETURN V _(V); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{V,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Resistence",{"V: ","I: ","Stack ? "},
        {"Enter 'Voltage'_(V).","Enter 'Current'_(A).",
         "Put 'Resistence'_(Ohm) on the stack ?"},{0,0,0},{0,0,0});
    
S1:=±∞ _(Ohm);
S2:=0 _(Ohm); 

 IF V==0 AND I==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("R = "+S2,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

  ELSE

   IF I==0 THEN

    IF stack==1 THEN RETURN S1; ELSE
    
     IF MSGBOX("R = "+S1,1)==1 THEN

      circuits(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   ELSE
    
    R:=V/I;
    S0:="R = "+R _(Ohm);
   
    IF stack==1 THEN RETURN R _(Ohm); ELSE
    
     IF MSGBOX(S0,1)==1 THEN

      circuits(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   END;

  END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==3 THEN
 CHOOSE(ch1,"V₀ = (V*R₂)/(R₁+R₂)"," ❰❰❰ BACK ❰❰❰ ","  Solve → V₀ ",   
            "  Solve → V ","  Solve → R₁ ","  Solve → R₂ ");

 CASE


IF ch1==1 THEN
 circuits();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{V,[0],{30,40,1}},{R₁,[0],{30,40,2}},{R₂,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Output Voltage",{"V: ","R₁: ","R₂: ","Stack ? "},
        {"Enter 'Input Voltage'_(V)","Enter 'Resistence 1'_(Ohm).",
         "Enter 'Resistence 2'_(Ohm).","Put 'Output Voltage'_(V) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(V);
S2:=0 _(V); 

 IF (V*R₂)==0 AND (R₁+R₂)==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("V₀ = "+S2,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

  ELSE

   IF (R₁+R₂)==0 THEN

    IF stack==1 THEN RETURN S1; ELSE
    
     IF MSGBOX("V₀ = "+S1,1)==1 THEN

      circuits(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   ELSE
    
    V₀:=(V*R₂)/(R₁+R₂);
    S0:="V₀ = "+V₀ _(V);
   
    IF stack==1 THEN RETURN V₀ _(V); ELSE
    
     IF MSGBOX(S0,1)==1 THEN

      circuits(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   END;

  END; 
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{V₀,[0],{30,40,1}},{R₁,[0],{30,40,2}},{R₂,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Input Voltage",{"V₀: ","R₁: ","R₂: ","Stack ? "},
        {"Enter 'Output Voltage'_(V)","Enter 'Resistence 1'_(Ohm).",
         "Enter 'Resistence 2'_(Ohm).","Put 'Input Voltage'_(V) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(V);
S2:=0 _(V); 

 IF (V₀*(R₂+R₁))==0 AND R₂==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("V = "+S2,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

  ELSE

   IF R₂==0 THEN

    IF stack==1 THEN RETURN S1; ELSE
    
     IF MSGBOX("V = "+S1,1)==1 THEN

      circuits(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   ELSE
    
    V:=V₀*(R₂+R₁)/R₂;
    S0:="V = "+V _(V);
   
    IF stack==1 THEN RETURN V _(V); ELSE
    
     IF MSGBOX(S0,1)==1 THEN

      circuits(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   END;

  END;
 
 END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{V,[0],{30,40,1}},{V₀,[0],{30,40,2}},{R₂,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence 1",{"V: ","V₀: ","R₂: ","Stack ? "},
        {"Enter 'Input Voltage'_(V)","Enter 'Output Voltage'_(V).",
         "Enter 'Resistence 2'_(Ohm).","Put 'Resistence 1'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});

IF V==0 AND V₀==0 AND R₂==0 THEN R₁:=0; END;
IF V≠0 AND V₀==0 AND R₂==0 THEN R₁:=0; END;
IF V≠0 AND V₀==0 AND R₂≠0 THEN R₁:=±∞; END;
IF V==0 AND V₀==0 AND R₂≠0 THEN R₁:=R₂; END;
IF V==0 AND V₀≠0 AND R₂≠0 THEN R₁:=R₂; END;
IF V≠0 AND V₀≠0 AND R₂≠0 THEN R₁:=((V*R₂)/V₀)-R₂; END;
IF V≠0 AND V₀≠0 AND R₂==0 THEN R₁:=((V*R₂)/V₀)-R₂; END;
IF V==0 AND V₀≠0 AND R₂==0 THEN R₁:=((V*R₂)/V₀)-R₂; END;

 S0:="R₁ = "+R₁ _(Ohm);
   
 IF stack==1 THEN RETURN R₁ _(Ohm); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{V,[0],{30,40,1}},{V₀,[0],{30,40,2}},{R₁,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence 2",{"V: ","V₀: ","R₁: ","Stack ? "},
        {"Enter 'Input Voltage'_(V)","Enter 'Output Voltage'_(V).",
         "Enter 'Resistence 1'_(Ohm).","Put 'Resistence 2'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});

S1:=±∞ _(Ohm);
S2:=0 _(Ohm);
 
 IF (-V₀*R₁)==0 AND (V₀-V)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("R₂ = "+S2,1)==1 THEN

     circuits(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

 ELSE

  IF (V₀-V)==0 THEN   
    
   IF stack==1 THEN RETURN S1; ELSE
   
    IF MSGBOX("R₂ = "+S1,1)==1 THEN

     circuits(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE
    
   R₂:=(-V₀*R₁)/(V₀-V);
   S0:="R₂ = "+R₂ _(Ohm);

   IF stack==1 THEN RETURN R₂ _(Ohm); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     circuits(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;  
  
 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==4 THEN
  CHOOSE(ch1,"R = R₁+R₂+R₃"," ❰❰❰ BACK ❰❰❰ ","  Solve → R ",   
             "  Solve → R₁ ","  Solve → R₂ ","  Solve → R₃ ");

 CASE


IF ch1==1 THEN
 circuits();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{R₁,[0],{30,40,1}},{R₂,[0],{30,40,2}},{R₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Total Resistence",{"R₁: ","R₂: ","R₃: ","Stack ? "},
        {"Enter 'Resistence 1'_(Ohm).","Enter 'Resistence 2'_(Ohm).",
         "Enter 'Resistence 3'_(Ohm).","Put 'Total Resistence'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S2:=0 _(Ohm); 

 IF (R₁*R₂*R₃)==0 AND (R₁*R₂+R₁*R₃+R₂*R₃)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
  
   IF MSGBOX("R = "+S2,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE

  R:=(R₁*R₂*R₃)/(R₁*R₂+R₁*R₃+R₂*R₃);
  S0:="R = "+R _(Ohm);

  IF stack==1 THEN RETURN R _(Ohm); ELSE
  
   IF MSGBOX(S0,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 END;   

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{R,[0],{30,40,1}},{R₂,[0],{30,40,2}},{R₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence 1",{"R: ","R₂: ","R₃: ","Stack ? "},
        {"Enter 'Total Resistence'_(Ohm).","Enter 'Resistence 2'_(Ohm).",
         "Enter 'Resistence 3'_(Ohm).","Put 'Resistence 1'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S2:=0 _(Ohm); 

 IF (-R*R₂*R₃)==0 AND (R*R₂+R*R₃-R₂*R₃)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
  
   IF MSGBOX("R₁ = "+S2,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE

  R₁:=(-R*R₂*R₃)/(R*R₂+R*R₃-R₂*R₃);
  S0:="R₁ = "+R₁ _(Ohm);

  IF stack==1 THEN RETURN R₁ _(Ohm); ELSE
  
   IF MSGBOX(S0,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 END;   

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{R,[0],{30,40,1}},{R₁,[0],{30,40,2}},{R₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence 2",{"R: ","R₁: ","R₃: ","Stack ? "},
        {"Enter 'Total Resistence'_(Ohm).","Enter 'Resistence 1'_(Ohm).",
         "Enter 'Resistence 3'_(Ohm).","Put 'Resistence 2'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S2:=0 _(Ohm); 

 IF (-R*R₁*R₃)==0 AND (R*R₁+R*R₃-R₁*R₃)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
  
   IF MSGBOX("R₂ = "+S2,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE

  R₂:=(-R*R₁*R₃)/(R*R₁+R*R₃-R₁*R₃);
  S0:="R₂ = "+R₂ _(Ohm);

  IF stack==1 THEN RETURN R₂ _(Ohm); ELSE
  
   IF MSGBOX(S0,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 END;   

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{R,[0],{30,40,1}},{R₁,[0],{30,40,2}},{R₂,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence 3",{"R: ","R₁: ","R₂: ","Stack ? "},
        {"Enter 'Total Resistence'_(Ohm).","Enter 'Resistence 1'_(Ohm).",
         "Enter 'Resistence 2'_(Ohm).","Put 'Resistence 3'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S2:=0 _(Ohm); 

 IF (-R*R₁*R₂)==0 AND (R*R₁+R*R₂-R₁*R₂)==0 THEN

  IF stack==1 THEN RETURN S2; ELSE
  
   IF MSGBOX("R₃ = "+S2,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE

  R₃:=(-R*R₁*R₂)/(R*R₁+R*R₂-R₁*R₂);
  S0:="R₃ = "+R₃ _(Ohm);

  IF stack==1 THEN RETURN R₃ _(Ohm); ELSE
  
   IF MSGBOX(S0,1)==1 THEN

    circuits(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 END;   

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==5 THEN
  CHOOSE(ch1,"V = V₁+V₂+V₃"," ❰❰❰ BACK ❰❰❰ ","  Solve → V ",   
             "  Solve → V₁ ","  Solve → V₂ ","  Solve → V₃ ");

 CASE


IF ch1==1 THEN
 circuits();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{V₁,[0],{30,40,1}},{V₂,[0],{30,40,2}},{V₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Total Voltage",{"V₁: ","V₂: ","V₃: ","Stack ? "},
        {"Enter 'Voltage 1'_(V).","Enter 'Voltage 2'_(V).","Enter 'Voltage 3'_(V).",
         "Put 'Total Voltage'_(V) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 V:=V₁+V₂+V₃;
 S0:="V = "+V _(V);

 IF stack==1 THEN RETURN V _(V); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{V,[0],{30,40,1}},{V₂,[0],{30,40,2}},{V₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Voltage 1",{"V: ","V₂: ","V₃: ","Stack ? "},
        {"Enter 'Total Voltage'_(V).","Enter 'Voltage 2'_(V).","Enter 'Voltage 3'_(V).",
         "Put 'Voltage 1'_(V) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 V₁:=V-V₂-V₃;
 S0:="V₁ = "+V₁ _(V);

 IF stack==1 THEN RETURN V₁ _(V); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{V,[0],{30,40,1}},{V₁,[0],{30,40,2}},{V₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Voltage 2",{"V: ","V₁: ","V₃: ","Stack ? "},
        {"Enter 'Total Voltage'_(V).","Enter 'Voltage 1'_(V).","Enter 'Voltage 3'_(V).",
         "Put 'Voltage 2'_(V) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 V₂:=V-V₁-V₃;
 S0:="V₂ = "+V₂ _(V);

 IF stack==1 THEN RETURN V₂ _(V); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{V,[0],{30,40,1}},{V₁,[0],{30,40,2}},{V₂,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Voltage 3",{"V: ","V₁: ","V₂: ","Stack ? "},
        {"Enter 'Total Voltage'_(V).","Enter 'Voltage 1'_(V).","Enter 'Voltage 2'_(V).",
         "Put 'Voltage 3'_(V) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 V₃:=V-V₁-V₂;
 S0:="V₃ = "+V₃ _(V);

 IF stack==1 THEN RETURN V₃ _(V); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
    
END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==6 THEN
  CHOOSE(ch1,"R = R₁+R₂+R₃"," ❰❰❰ BACK ❰❰❰ ","  Solve → R ",   
             "  Solve → R₁ ","  Solve → R₂ ","  Solve → R₃ ");

 CASE


IF ch1==1 THEN
 circuits();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{R₁,[0],{30,40,1}},{R₂,[0],{30,40,2}},{R₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Total Resistence",{"R₁: ","R₂: ","R₃: ","Stack ? "},
        {"Enter 'Resistence 1'_(Ohm).","Enter 'Resistence 2'_(Ohm).",
         "Enter 'Resistence 3'_(Ohm).","Put 'Total Resistence'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 R:=R₁+R₂+R₃;
 S0:="R = "+R _(Ohm);

 IF stack==1 THEN RETURN R _(Ohm); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{R,[0],{30,40,1}},{R₂,[0],{30,40,2}},{R₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence 1",{"R: ","R₂: ","R₃: ","Stack ? "},
        {"Enter 'Total Resistence'_(Ohm).","Enter 'Resistence 2'_(Ohm).",
         "Enter 'Resistence 3'_(Ohm).","Put 'Resistence 1'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 R₁:=R-R₂-R₃;
 S0:="R₁ = "+R₁ _(Ohm);

 IF stack==1 THEN RETURN R₁ _(Ohm); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{R,[0],{30,40,1}},{R₁,[0],{30,40,2}},{R₃,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence 2",{"R: ","R₁: ","R₃: ","Stack ? "},
        {"Enter 'Total Resistence'_(Ohm).","Enter 'Resistence 1'_(Ohm).",
         "Enter 'Resistence 3'_(Ohm).","Put 'Resistence 2'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 R₂:=R-R₁-R₃;
 S0:="R₂ = "+R₂ _(Ohm);

 IF stack==1 THEN RETURN R₂ _(Ohm); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{R,[0],{30,40,1}},{R₁,[0],{30,40,2}},{R₂,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence 3",{"R: ","R₁: ","R₂: ","Stack ? "},
        {"Enter 'Total Resistence'_(Ohm).","Enter 'Resistence 1'_(Ohm).",
         "Enter 'Resistence 2'_(Ohm).","Put 'Resistence 3'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 R₃:=R-R₁-R₂;
 S0:="R₃ = "+R₃ _(Ohm);

 IF stack==1 THEN RETURN R₃ _(Ohm); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   circuits(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************


DEFAULT
  RETURN "GOOD BYE";

END;

END;
//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#-------------------------------------------------------- END CIRCUITS PROGRAM -----------------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################






//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#------------------------------------------------- BEGIN ELECTRICAL CURRENTS PROGRAM -----------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################
currents()
BEGIN

LOCAL ch0,ch1,stack;
LOCAL P,E,t,I,V,R;
LOCAL S0,S1,S2,S3;

CHOOSE(ch0,"Electrical Currents"," ❰❰❰ BACK ❰❰❰ ","  P = V*I ","  P = E/t ",
           "  R = V/I ","  P = I²*R ","  E = I²*R*t ");

CASE

//*************************************************************************************************************************************
IF ch0==1 THEN physicscat01(); END; //*************************************************************************************************
//*************************************************************************************************************************************

//*************************************************************************************************************************************
IF ch0==2 THEN
  CHOOSE(ch1,"P = V*I"," ❰❰❰ BACK ❰❰❰ ","  Solve → P ",   
             "  Solve → V ","  Solve → I ");

 CASE


  
IF ch1==1 THEN
currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{V,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Power",{"V: ","I: ","Stack ? "},
        {"Enter 'Voltage'_(V).","Enter 'Electric Current'_(A).",
         "Put 'Electric Power'_(W) on the stack ?"},{0,0,0},{0,0,0});
    
 P:=V*I;
 S0:="P = "+P _(W);
   
 IF stack==1 THEN RETURN P _(W); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{P,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Voltage",{"P: ","I: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Electric Current'_(A).",
         "Put 'Voltage'_(V) on the stack ?"},{0,0,0},{0,0,0});

S1:=±∞ _(V);
S2:=0 _(V); 

 IF P==0 AND I==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("V = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF I==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("V = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
    
   V:=P/I;
   S0:="V = "+V _(V);
   
   IF stack==1 THEN RETURN V _(V); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{P,[0],{30,40,1}},{V,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Current",{"P: ","V: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Voltage'_(V).",
         "Put 'Electric Current'_(A) on the stack ?"},{0,0,0},{0,0,0});

S1:=±∞ _(A);
S2:=0 _(A); 

 IF P==0 AND V==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("I = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF V==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("I = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
    
   I:=P/V;
   S0:="I = "+I _(A);
   
   IF stack==1 THEN RETURN I _(A); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==3 THEN
 CHOOSE(ch1,"P = E/t"," ❰❰❰ BACK ❰❰❰ ","  Solve → P ",   
            "  Solve → E ","  Solve → t ");

 CASE


IF ch1==1 THEN
 currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{E,[0],{30,40,1}},{t,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Power",{"E: ","t: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Enter 'Time'_(s).",
         "Put 'Electric Power'_(W) on the stack ?"},{0,0,0},{0,0,0});
 
S1:=±∞ _(W);
S2:=0 _(W); 

 IF E==0 AND t==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("P = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF t==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("P = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
   
   P:=E/t;
   S0:="P = "+P _(W);
   
   IF stack==1 THEN RETURN P _(W); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{P,[0],{30,40,1}},{t,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Energy Consumption",{"P: ","t: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Time'_(s).",
         "Put 'Energy Consumption'_(J) on the stack ?"},{0,0,0},{0,0,0});
    
 E:=P*t;
 S0:="E = "+E _(J);
   
 IF stack==1 THEN RETURN E _(J); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{E,[0],{30,40,1}},{P,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Time",{"E: ","P: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Electric Power'_(W).",
         "Put 'Time'_(s) on the stack ?"},{0,0,0},{0,0,0});
 
S1:=±∞ _(s);
S2:=0 _(s); 

 IF E==0 AND P==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("t = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF P==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("t = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
   
   t:=E/P;
   S0:="t = "+t _(s);
   
   IF stack==1 THEN RETURN t _(s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==4 THEN
  CHOOSE(ch1,"R = V/I"," ❰❰❰ BACK ❰❰❰ ","  Solve → R ",   
             "  Solve → V ","  Solve → I ");

 CASE


IF ch1==1 THEN
 currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{V,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Resistence",{"V: ","I: ","Stack ? "},
        {"Enter 'Voltage'_(V).","Electric Current'_(A).",
         "Put 'Resistence'_(Ohm) on the stack ?"},{0,0,0},{0,0,0});
 
S1:=±∞ _(Ohm);
S2:=0 _(Ohm); 

 IF V==0 AND I==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("R = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF I==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("R = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
   
   R:=V/I;
   S0:="R = "+R _(Ohm);
   
   IF stack==1 THEN RETURN R _(Ohm); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{R,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Voltage",{"R: ","I: ","Stack ? "},
        {"Enter 'Resistence'_(Ohm).","Enter 'Electric Current'_(A).",
         "Put 'Voltage'_(V) on the stack ?"},{0,0,0},{0,0,0});
    
 V:=R*I;
 S0:="V = "+V _(V);
   
 IF stack==1 THEN RETURN V _(V); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{V,[0],{30,40,1}},{R,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Current",{"V: ","R: ","Stack ? "},
        {"Enter 'Voltage'_(V).","Resistence'_(Ohm).",
         "Put 'Electric Current'_(A) on the stack ?"},{0,0,0},{0,0,0});
 
S1:=±∞ _(A);
S2:=0 _(A); 

 IF V==0 AND R==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("I = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF R==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("I = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
   
   I:=V/R;
   S0:="I = "+I _(A);
   
   IF stack==1 THEN RETURN I _(A); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==5 THEN
  CHOOSE(ch1,"P = I²*R"," ❰❰❰ BACK ❰❰❰ ","  Solve → P ",   
             "  Solve → I ","  Solve → R ");

 CASE


IF ch1==1 THEN
 currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{I,[0],{30,40,1}},{R,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Power",{"I: ","R: ","Stack ? "},
        {"Enter 'Electric Current'_(A).","Enter 'Resistence'_(Ohm).",
         "Put 'Electric Power'_(W) on the stack ?"},{0,0,0},{0,0,0});
    
 P:=I²*R;
 S0:="P = "+P _(W);
   
 IF stack==1 THEN RETURN P _(W); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{P,[0],{30,40,1}},{R,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Current",{"P: ","R: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Resistence'_(Ohm).",
         "Put 'Electric Current'_(A) on the stack ?"},{0,0,0},{0,0,0});
    

S1:=±∞ _(A);
S2:=0 _(A);
S3:="Result is not real!";

 IF (P*R)<0 THEN

  IF MSGBOX("I = "+S3,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
     
  END;
 
 ELSE
 
  IF (√(P*R))==0 AND (R)==0 THEN

   IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("I = "+S2,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE

   IF R==0 THEN   
    
    IF stack==1 THEN RETURN S1; ELSE
   
     IF MSGBOX("I = "+S1,1)==1 THEN

      currents(); ELSE

      RETURN "GOOD BYE";

     END;

    END;

   ELSE

    I:=√(P*R)/R;
    S0:="I = "+I _(A);
   
    IF stack==1 THEN RETURN I _(A); ELSE
    
     IF MSGBOX(S0,1)==1 THEN

      currents(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   END;

  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{P,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Resistence",{"P: ","I: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Electric Current'_(A).",
         "Put 'Resistence'_(Ohm) on the stack ?"},{0,0,0},{0,0,0});
    
S1:=±∞ _(Ohm);
S2:=0 _(Ohm); 

 IF P==0 AND I==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("R = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF I==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("R = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE

   R:=P/I²;
   S0:="R = "+R _(Ohm);
   
   IF stack==1 THEN RETURN R _(Ohm); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==6 THEN
  CHOOSE(ch1,"E = I²*R*t"," ❰❰❰ BACK ❰❰❰ ","  Solve → E ",   
             "  Solve → I ","  Solve → R ","  Solve → t ");

 CASE


IF ch1==1 THEN
 currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{I,[0],{30,40,1}},{R,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Energy Consumption",{"I: ","R: ","t: ","Stack ? "},
        {"Enter 'Electric Current'_(A).","Enter 'Resistence'_(Ohm).",
         "Enter 'Time'_(s).","Put 'Energy Consumption'_(J) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 E:=I²*R*t;
 S0:="E = "+E _(J);

 IF stack==1 THEN RETURN E _(J); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{E,[0],{30,40,1}},{R,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Electric Current",{"E: ","R: ","t: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Enter 'Resistence'_(Ohm).",
         "Enter 'Time'_(s).","Put 'Electric Current'_(A) on the stack ?"},{0,0,0,0},{0,0,0,0});
 
S1:=±∞ _(A);
S2:=0 _(A);
S3:="Result is not real!";

 IF (E*R*t)<0 THEN

  IF stack==1 THEN RETURN S3; ELSE
   
   IF MSGBOX("I = "+S3,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE

  IF (E*R*t)==0 AND (R*t)==0 THEN

   IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("I = "+S2,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";

    END;

   END;
 
  ELSE  
 
   I:=(√(E*R*t))/(R*t);
   S0:="I = "+I _(A);
  
   IF stack==1 THEN RETURN I _(A); ELSE
     
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{E,[0],{30,40,1}},{I,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence",{"E: ","I: ","t: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Enter 'Electric Current'_(A).",
         "Enter 'Time'_(s).","Put 'Resistence'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S1:=±∞ _(Ohm);
S2:=0 _(Ohm); 

 IF E==0 AND (I²*t)==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("R = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF (I²*t)==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("R = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE

   R:=E/(I²*t);
   S0:="R = "+R _(Ohm);
   
   IF stack==1 THEN RETURN R _(Ohm); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{E,[0],{30,40,1}},{I,[0],{30,40,2}},{R,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Time",{"E: ","I: ","R: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Enter 'Electric Current'_(A).",
         "Enter 'Resistence'_(Ohm).","Put 'Time'_(s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S1:=±∞ _(s);
S2:=0 _(s); 

 IF E==0 AND (I²*R)==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("t = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF (I²*R)==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("t = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE

   t:=E/(I²*R);
   S0:="t = "+t _(s);
   
   IF stack==1 THEN RETURN t _(s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************


DEFAULT
  RETURN "GOOD BYE";

END;

END;
//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#-------------------------------------------------- END ELECTRICAL CURRENTS PROGRAM ------------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################






//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#-------------------------------------------- BEGIN DIFFRA. & INTERF. OF LIGHT PROGRAM ---------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################
diffraction()
BEGIN

LOCAL ch0,ch1,stack;
LOCAL P,E,t,I,V,R;
LOCAL S0,S1,S2,S3;

CHOOSE(ch0,"Diffra. & Interf. of Light"," ❰❰❰ BACK ❰❰❰ ","  λ = d*x/L ","  n*λ = d*sin(θ) ",
           "  R = V/I ","  P = I²*R ","  E = I²*R*t ");

CASE

//*************************************************************************************************************************************
IF ch0==1 THEN physicscat01(); END; //*************************************************************************************************
//*************************************************************************************************************************************

//*************************************************************************************************************************************
IF ch0==2 THEN
  CHOOSE(ch1,"P = V*I"," ❰❰❰ BACK ❰❰❰ ","  Solve → P ",   
             "  Solve → V ","  Solve → I ");

 CASE


  
IF ch1==1 THEN
diffraction();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{V,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Power",{"V: ","I: ","Stack ? "},
        {"Enter 'Voltage'_(V).","Enter 'Electric Current'_(A).",
         "Put 'Electric Power'_(W) on the stack ?"},{0,0,0},{0,0,0});
    
 P:=V*I;
 S0:="P = "+P _(W);
   
 IF stack==1 THEN RETURN P _(W); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{P,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Voltage",{"P: ","I: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Electric Current'_(A).",
         "Put 'Voltage'_(V) on the stack ?"},{0,0,0},{0,0,0});

S1:=±∞ _(V);
S2:=0 _(V); 

 IF P==0 AND I==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("V = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF I==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("V = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
    
   V:=P/I;
   S0:="V = "+V _(V);
   
   IF stack==1 THEN RETURN V _(V); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{P,[0],{30,40,1}},{V,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Current",{"P: ","V: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Voltage'_(V).",
         "Put 'Electric Current'_(A) on the stack ?"},{0,0,0},{0,0,0});

S1:=±∞ _(A);
S2:=0 _(A); 

 IF P==0 AND V==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("I = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF V==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("I = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
    
   I:=P/V;
   S0:="I = "+I _(A);
   
   IF stack==1 THEN RETURN I _(A); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==3 THEN
 CHOOSE(ch1,"P = E/t"," ❰❰❰ BACK ❰❰❰ ","  Solve → P ",   
            "  Solve → E ","  Solve → t ");

 CASE


IF ch1==1 THEN
 currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{E,[0],{30,40,1}},{t,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Power",{"E: ","t: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Enter 'Time'_(s).",
         "Put 'Electric Power'_(W) on the stack ?"},{0,0,0},{0,0,0});
 
S1:=±∞ _(W);
S2:=0 _(W); 

 IF E==0 AND t==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("P = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF t==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("P = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
   
   P:=E/t;
   S0:="P = "+P _(W);
   
   IF stack==1 THEN RETURN P _(W); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{P,[0],{30,40,1}},{t,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Energy Consumption",{"P: ","t: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Time'_(s).",
         "Put 'Energy Consumption'_(J) on the stack ?"},{0,0,0},{0,0,0});
    
 E:=P*t;
 S0:="E = "+E _(J);
   
 IF stack==1 THEN RETURN E _(J); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{E,[0],{30,40,1}},{P,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Time",{"E: ","P: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Electric Power'_(W).",
         "Put 'Time'_(s) on the stack ?"},{0,0,0},{0,0,0});
 
S1:=±∞ _(s);
S2:=0 _(s); 

 IF E==0 AND P==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("t = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF P==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("t = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
   
   t:=E/P;
   S0:="t = "+t _(s);
   
   IF stack==1 THEN RETURN t _(s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==4 THEN
  CHOOSE(ch1,"R = V/I"," ❰❰❰ BACK ❰❰❰ ","  Solve → R ",   
             "  Solve → V ","  Solve → I ");

 CASE


IF ch1==1 THEN
 currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{V,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Resistence",{"V: ","I: ","Stack ? "},
        {"Enter 'Voltage'_(V).","Electric Current'_(A).",
         "Put 'Resistence'_(Ohm) on the stack ?"},{0,0,0},{0,0,0});
 
S1:=±∞ _(Ohm);
S2:=0 _(Ohm); 

 IF V==0 AND I==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("R = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF I==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("R = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
   
   R:=V/I;
   S0:="R = "+R _(Ohm);
   
   IF stack==1 THEN RETURN R _(Ohm); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{R,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Voltage",{"R: ","I: ","Stack ? "},
        {"Enter 'Resistence'_(Ohm).","Enter 'Electric Current'_(A).",
         "Put 'Voltage'_(V) on the stack ?"},{0,0,0},{0,0,0});
    
 V:=R*I;
 S0:="V = "+V _(V);
   
 IF stack==1 THEN RETURN V _(V); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{V,[0],{30,40,1}},{R,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Current",{"V: ","R: ","Stack ? "},
        {"Enter 'Voltage'_(V).","Resistence'_(Ohm).",
         "Put 'Electric Current'_(A) on the stack ?"},{0,0,0},{0,0,0});
 
S1:=±∞ _(A);
S2:=0 _(A); 

 IF V==0 AND R==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("I = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF R==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("I = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE
   
   I:=V/R;
   S0:="I = "+I _(A);
   
   IF stack==1 THEN RETURN I _(A); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==5 THEN
  CHOOSE(ch1,"P = I²*R"," ❰❰❰ BACK ❰❰❰ ","  Solve → P ",   
             "  Solve → I ","  Solve → R ");

 CASE


IF ch1==1 THEN
 currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{I,[0],{30,40,1}},{R,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Power",{"I: ","R: ","Stack ? "},
        {"Enter 'Electric Current'_(A).","Enter 'Resistence'_(Ohm).",
         "Put 'Electric Power'_(W) on the stack ?"},{0,0,0},{0,0,0});
    
 P:=I²*R;
 S0:="P = "+P _(W);
   
 IF stack==1 THEN RETURN P _(W); ELSE
    
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
  
  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{P,[0],{30,40,1}},{R,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Electric Current",{"P: ","R: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Resistence'_(Ohm).",
         "Put 'Electric Current'_(A) on the stack ?"},{0,0,0},{0,0,0});
    

S1:=±∞ _(A);
S2:=0 _(A);
S3:="Result is not real!";

 IF (P*R)<0 THEN

  IF MSGBOX("I = "+S3,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";
     
  END;
 
 ELSE
 
  IF (√(P*R))==0 AND (R)==0 THEN

   IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("I = "+S2,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  ELSE

   IF R==0 THEN   
    
    IF stack==1 THEN RETURN S1; ELSE
   
     IF MSGBOX("I = "+S1,1)==1 THEN

      currents(); ELSE

      RETURN "GOOD BYE";

     END;

    END;

   ELSE

    I:=√(P*R)/R;
    S0:="I = "+I _(A);
   
    IF stack==1 THEN RETURN I _(A); ELSE
    
     IF MSGBOX(S0,1)==1 THEN

      currents(); ELSE

      RETURN "GOOD BYE";
  
     END;

    END;

   END;

  END;

 END;
 
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{P,[0],{30,40,1}},{I,[0],{30,40,2}},{stack,0,{85,0,5}}},
         "Solving → Resistence",{"P: ","I: ","Stack ? "},
        {"Enter 'Electric Power'_(W).","Enter 'Electric Current'_(A).",
         "Put 'Resistence'_(Ohm) on the stack ?"},{0,0,0},{0,0,0});
    
S1:=±∞ _(Ohm);
S2:=0 _(Ohm); 

 IF P==0 AND I==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("R = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF I==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("R = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE

   R:=P/I²;
   S0:="R = "+R _(Ohm);
   
   IF stack==1 THEN RETURN R _(Ohm); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;

END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************
IF ch0==6 THEN
  CHOOSE(ch1,"E = I²*R*t"," ❰❰❰ BACK ❰❰❰ ","  Solve → E ",   
             "  Solve → I ","  Solve → R ","  Solve → t ");

 CASE


IF ch1==1 THEN
 currents();
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==2 THEN
 INPUT({{I,[0],{30,40,1}},{R,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Energy Consumption",{"I: ","R: ","t: ","Stack ? "},
        {"Enter 'Electric Current'_(A).","Enter 'Resistence'_(Ohm).",
         "Enter 'Time'_(s).","Put 'Energy Consumption'_(J) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
 E:=I²*R*t;
 S0:="E = "+E _(J);

 IF stack==1 THEN RETURN E _(J); ELSE
  
  IF MSGBOX(S0,1)==1 THEN

   currents(); ELSE

   RETURN "GOOD BYE";

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==3 THEN
 INPUT({{E,[0],{30,40,1}},{R,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Electric Current",{"E: ","R: ","t: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Enter 'Resistence'_(Ohm).",
         "Enter 'Time'_(s).","Put 'Electric Current'_(A) on the stack ?"},{0,0,0,0},{0,0,0,0});
 
S1:=±∞ _(A);
S2:=0 _(A);
S3:="Result is not real!";

 IF (E*R*t)<0 THEN

  IF stack==1 THEN RETURN S3; ELSE
   
   IF MSGBOX("I = "+S3,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";

   END;

  END;

 ELSE

  IF (E*R*t)==0 AND (R*t)==0 THEN

   IF stack==1 THEN RETURN S2; ELSE
   
    IF MSGBOX("I = "+S2,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";

    END;

   END;
 
  ELSE  
 
   I:=(√(E*R*t))/(R*t);
   S0:="I = "+I _(A);
  
   IF stack==1 THEN RETURN I _(A); ELSE
     
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";

    END;

   END;

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==4 THEN
 INPUT({{E,[0],{30,40,1}},{I,[0],{30,40,2}},{t,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Resistence",{"E: ","I: ","t: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Enter 'Electric Current'_(A).",
         "Enter 'Time'_(s).","Put 'Resistence'_(Ohm) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S1:=±∞ _(Ohm);
S2:=0 _(Ohm); 

 IF E==0 AND (I²*t)==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("R = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF (I²*t)==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("R = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE

   R:=E/(I²*t);
   S0:="R = "+R _(Ohm);
   
   IF stack==1 THEN RETURN R _(Ohm); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END;
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
IF ch1==5 THEN
 INPUT({{E,[0],{30,40,1}},{I,[0],{30,40,2}},{R,[0],{30,40,3}},{stack,0,{85,0,5}}},
         "Solving → Time",{"E: ","I: ","R: ","Stack ? "},
        {"Enter 'Energy Consumption'_(J).","Enter 'Electric Current'_(A).",
         "Enter 'Resistence'_(Ohm).","Put 'Time'_(s) on the stack ?"},{0,0,0,0},{0,0,0,0});
    
S1:=±∞ _(s);
S2:=0 _(s); 

 IF E==0 AND (I²*R)==0 THEN
 
  IF stack==1 THEN RETURN S2; ELSE
    
   IF MSGBOX("t = "+S2,1)==1 THEN

    currents(); ELSE

    RETURN "GOOD BYE";
  
   END;

  END;

 ELSE

  IF (I²*R)==0 THEN

   IF stack==1 THEN RETURN S1; ELSE
    
    IF MSGBOX("t = "+S1,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  ELSE

   t:=E/(I²*R);
   S0:="t = "+t _(s);
   
   IF stack==1 THEN RETURN t _(s); ELSE
    
    IF MSGBOX(S0,1)==1 THEN

     currents(); ELSE

     RETURN "GOOD BYE";
  
    END;

   END;

  END;

 END
   
END;
//-------------------------------------------------------------------------------------------------------------------------------------
 DEFAULT
 RETURN "GOOD BYE";

 END;
END;
//*************************************************************************************************************************************


DEFAULT
  RETURN "GOOD BYE";

END;

END;
//#####################################################################################################################################
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#--------------------------------------------- END DIFFRA. & INTERF. OF LIGHT PROGRAM ----------------------------------------------#
//#-----------------------------------------------------------------------------------------------------------------------------------#
//#####################################################################################################################################