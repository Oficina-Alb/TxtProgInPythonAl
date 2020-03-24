Menaxhimi i Karel
==============

Për të parë se si duket programimi, ne do t'ju prezantojmë me Karel. Karel është një robot i animuar që lëviz përgjatë një tryeze si labirint duke ndjekur udhëzimet tona në formën e një programi. Përmes administrimit të Karelit, ne do të adoptojmë një logjikë që është shumë e rëndësishme për të shkruar një program, dhe gjithashtu mund të argëtohemi gjatë rrugës.

.. infonote::

    Ideja e të mësuarit të programimit përmes kontrollit të një roboti daton që nga vitet 1970, kur Richard E. Pattis, si student i diplomuar në Universitetin Stanford, krijoi mjedisin e parë të tillë me një gjuhë programimi të krijuar posaçërisht për këtë qëllim. Gjuha, si roboti, u quajt Karel, pas Karel Čapek, shkrimtarit çek që filloi së pari përdorimin e fjalës robot. Libri i Patis *Karel Robot: Një Prezantim në Artin e Programimit* u botua në vitin 1981 dhe u bë shpejt libri më i shitur në kurset e programimit.T
Do të përdorim këto funksione për të menaxhuar Karel:

- ``move()`` - lëviz nje kuti përpara,
- ``turn_left()`` - kthehet 90 gradë në të majtë,
- ``turn_right()`` - kthehet 90 gradë në të djathtë,
- ``pick_ball()`` - zgjedh një top në kutinë ku jeni vendosur,
- ``drop_ball()`` - lëshon një top në kutinë ku jeni vendosur.

Duke përdorur këto pesë funksione, ne deklarojmë atë që duam të bëjmë Karel, kështu që do t'i quajmë "komanda për Karel", ose "deklarim". Kareli kupton edhe pesë funksione të ndryshme, të cilat do t’i shohim së shpejti. Përveç këtyre komandave drejtuar drejtpërdrejtë në Karel, ne gjithashtu mund të përdorim të gjitha komandat e gjuhës programuese Python, të cilat do t'i mësojmë gjatë kursit.

Le të shikojmë shembujt dhe si komandat e sipëer pëmendura mund të përdoren të udhezojmë Karel në botën e tij:

Shembuj
--------

Lëviz 1 kuti përpara dhe merr topin
'''''''''''''''''''''''''''''''''''''''''

.. questionnote::

    Shkruaj nje program qe leviz Karel në fushë (2, 1) dhe bëje atë të marrë topin.

Ky program konsistion në dy komanda, E para i tregon Karel të lëvizë një fushë përpara, dhe tjetra të marrë topin.
   
.. karel:: Karel_intro_two_squares_one_ball
   :blockly:

   {
        setup:function() {
            var world = new World(2, 1);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.putBall(2, 1);

        var robot = new Robot();

        var code = ["from karel import *",
                    "move()",
                    "pick_ball()"];
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() === 1;
        },
   }

**Përfshirja e librarisë** *karel* 
'''''''''''''''''''''''''''''''''

.. infonote::

    Funksionet që ne përdorim për të menaxhuar Karel janë përcaktuar në bibliotekë *karel*. Prandaj, në fillim të secilit program, duhet t'i tregojmë kompjuterit (më saktë, programit që ekzekuton programin tonë) që së pari të bashkëngjitni përkufizimet e këtyre funksioneve për menaxhimin e Karelit. Kjo arrihet me rreshtin e parë të programit: ``from karel import``. Programo program që merret me Karel që ne shkruajmë duhet të fillojë në këtë mënyrë.

     Mbani në mend se biblioteka *karel* mund të përdoret vetëm në këtë mjedis tani për tani. Ju mund të drejtoni programet tuaja të tjera në mënyra të tjera, por ne do t'ju kujtojmë atë kur koha është e duhur.

Mund të ketë më shumë se një top në një katror, dhe detyra jonë mund të jetë t'i themi Karelit të marrë disa, ose të gjithë ata.

Zhvendosuni një katror përpara dhe merrni tre topa
''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

    Shkruaj një program që i thotë Karelit të zhvendoset në kuti (2, 1) dhe të marr tre nga pesë topat që janë atje.
    
Në këtë program, pas komandës ``move ()``, komanda ``pick_ball ()``duhet të shkruhet tre herë, pasi ne kemi nevojë për Karel që të marr tre topa. Kushtojini vëmendje numrit që shfaqet në top. Ajo tregon se sa topa ka në atë shesh. Përveç kësaj, numri në të majtë të kokës së Karelit (gjë që mund të keni vërejtur edhe në shembullin e mëparshëm) tregon se sa topa ka Kareli me të.
   
.. karel:: Karel_intro_two_squares_five_balls
   :blockly:

   {
        setup:function() {
            var world = new World(2, 1);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.putBalls(2, 1, 5);

        var robot = new Robot();

        var code = ["from karel import *",
                    "move()",
                    "pick_ball()",
                    "pick_ball()",
                    "pick_ball()"];
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() === 3;
        },
   }
   

Detyra tjeter [sht[ e ngjashme. por më e nderlikuar.
   
Shko te topi dhe merre
'''''''''''''''''''''''''''

.. questionnote::

   Shkruaj një program që i thotë Karelit të dalë në fushë (4, 1) dhe të marr topin.

Detyra nuk ndryshon në thelb nga ajo e mëparshmja. Ende është e domosdoshme për ta sjellë Karelin në kutinë e synuar dhe t’i thoni që të marrë topin. Dallimi është se tani rruga për në kutinë e synuar është më e gjatë, dhe po kështu është edhe programi ynë:

.. karel:: Karel_intro_take_ball_on_square_4_1
   :blockly:

   {
        setup:function() {
            var world = new World(5,5);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.putBall(4, 1);
            world.addEWWall(1, 1, 2);
            world.addNSWall(2, 2, 2);
            world.addEWWall(2, 3, 3);
            world.addNSWall(3, 1, 2);
            world.addNSWall(3, 4, 1);
            world.addNSWall(1, 5, 1);
            world.addEWWall(4, 1, 1);
            
        var robot = new Robot();

        var code = ["from karel import *",
                    "move()       # go to (2, 1)",
                    "move()       # go to (3, 1)",
                    "turn_left()  # turn north (^)",
                    "move()       # go to (3, 2)",
                    "move()       # go to (3, 3)",
                    "turn_right() # turn east (>)",
                    "move()       # go to (4, 3)",
                    "move()       # go to (5, 3)",
                    "turn_right() # turn south (v)",
                    "move()       # go to (5, 2)",
                    "move()       # go to (5, 1)",
                    "turn_right() # turn west (<)",
                    "move()       # go to (4, 1)",
                    "pick_ball()  # take the ball at (4, 1)"];
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() === 1;
        },
   }

Duke lexuar këtë program, është duke u bërë e vështirë të ndiqeni se cila komandë e sjell Karelin në cilin shesh. Ky nuk është rasti vetëm për fillestarët, është e vështirë për këdo sepse çdo deklarim ``veprim ()`` duket e njëjtë. Për të ndihmuar vetveten dhe veten, pas çdo komande kemi shtuar shenjën # dhe disa tekst që na ndihmon të ndjekim atje ku kemi sjellë Karelin.

**Komentet**
''''''''''''

.. infonote::

    Pjesë e çdo programi Python nga karakteri ``#`` deri në fund të rreshtit quhet një ``koment``. Komentet nuk ndikojnë në ekzekutimin e programit, programi bën të njëjtën gjë me ose pa ato. Komentet kanë për qëllim vetëm njerëzit që lexojnë dhe shkruajnë programe, për t'i ndihmuar ata t'i kuptojnë më mirë këto programe dhe t'i trajtojnë më lehtë.
    
     Kur mendojmë të shkruajmë komente në programet tona, duhet t'i shkruajmë ato si për veten tonë ashtu edhe për njerëzit e tjerë që do të lexojnë programet tona. Nga ana tjetër, komentet që njerëzit e tjerë shkruajnë në programet e tyre do të na ndihmojnë të kuptojmë programet e tyre.
    
     Nuk ka rregulla të sakta për të shkruar komente. Në komentet tuaja, duhet të shkruani gjithçka që besoni se ndihmon të tjerët (dhe veten tuaj) ta kuptojnë më mirë programin tuaj.
   
Mblidh të gjithë topat
'''''''''''''''''''''

Në këtë shembull, topat janë në kuti të ndryshme dhe ne kemi nevojë ta sjellim Karelin në secilën prej këtyre topave.

.. questionnote::

   Shkruaj një program për t’i thënë Karelit të marrë të katër topat.

Ne mund të zgjedhim shtegun për Karelin në shumë mënyra, por sa më e shkurtër të jetë rruga që ne zgjedhim, programi ynë më i shkurtër (dhe më i shpejtë). Kështu, për shembull, së pari mund ta merrnim topin në katrorin (5, 2), pastaj të dy topat në (5, 5) dhe në fund topin në (4, 4).

.. karel:: Karel_intro_collect_three_balls
   :blockly:

   {
        setup:function() {
            var world = new World(5,5);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.putBall(5, 2);
            world.putBalls(5, 5, 2);
            world.putBall(4, 4);
            world.addEWWall(1, 1, 2);
            world.addNSWall(2, 2, 2);
            world.addEWWall(2, 3, 3);
            world.addNSWall(3, 1, 2);
            world.addNSWall(3, 4, 1);
            world.addNSWall(1, 5, 1);
            world.addEWWall(4, 1, 1);
            
        var robot = new Robot();

        var code = ["from karel import *",
                    "move(); move(); turn_left()  # go to square (3, 1) and turn north",
                    "move(); move(); turn_right() # go to square (3, 3) and turn east",
                    "move(); move(); turn_right() # go to square (5, 3) and turn south",
                    "move(); pick_ball()          # come to square (5, 2) and take the ball",
                    "turn_left(); turn_left()     # turn north",
                    "move(); move(); move()       # come to square (5, 5)",
                    "pick_ball(); pick_ball()     # take two balls",
                    "turn_left(); move();         # go to square (4, 5)",
                    "turn_left(); move();         # go to square (4, 4)",
                    "pick_ball()                  # take the last ball at (4, 4)"];
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() === 4;
        },
   }

**Grupimi i komandave**
'''''''''''''''''''''

Meqenëse ky program është edhe më i gjatë se ai i mëparshmi, për ta bërë më të lehtë lundrimin në program dhe për të ndjekur pozicionin e Karel, ne kemi bërë grupe komandash që përbëjnë një fazë të udhëtimit dhe vendosëm secilin grup në një rresht të program. Në fund të secilës rresht, ka një koment që shpjegon grupin e komandave në atë rresht.

Vini re se, kur shkruani një program në këtë mënyrë, karakteri ``;`` duhet të shkruhet ndërmjet komandave (pas urdhrit të fundit në rresht, pikëpresja nuk është e nevojshme).

Komandat mund të grupohen ndryshe, për shembull duke ndarë një grup komandash (shkruar një poshtë tjetrit) nga grupi tjetër me një linjë boshe. Kjo mënyrë e grupimit përdoret shumë më shpesh, pasi komandat zakonisht nuk janë aq të shkurtra sa ato për menaxhimin e Karelit. Ja se si do të dukej:

.. code::

    from karel import *
    
    # go to square (3, 1) and turn north"
    move()
    move()
    turn_left()
    
    # go to square (3, 3) and turn east
    move()
    move()
    turn_right()
    
    # go to square (5, 3) and turn south
    move()
    move()
    turn_right()
    
    # come to square (5, 2) and take the ball
    move()
    pick_ball()
    
    # turn north
    turn_left()
    turn_left()
    
    # come to square (5, 5)
    move()
    move()
    move()
    
    # take two balls
    pick_ball()
    pick_ball()
    
    # go to square (4, 4)
    turn_left()
    move()
    turn_left()
    move()
    
    # take the last ball at (4, 4)
    pick_ball()
    
~~~~

Karel mund te hedhi topin ne kuti. Ja si:

Lëviz topin
'''''''''''''

.. questionnote::

   Shkruani një program i cili e bën Karel të lëviz topin në kutinë (2, 2) (vini re se në fillim Karel **nuk është i orientuar** siç duhet).
   

.. karel:: Karel_intro_move_ball_in_2x2
   :blockly:

   {
        setup:function() {
            var world = new World(2, 2);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("S");
            world.putBall(2, 1);
            world.addEWWall(2, 1, 1);

        var robot = new Robot();

        var code = ["from karel import *",
                    "turn_left(); move(); pick_ball();  # take the ball at (2, 1)",
                    "turn_right(); turn_right(); move() # go back to (1, 1)",
                    "turn_right(); move()               # go to (1, 2)",
                    "turn_right(); move()               # go to (2, 2)",
                    "drop_ball()                        # place the ball at (2, 2)"];
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return world.getBalls(2, 2) === 1;
        },
   }

**Gabime në ekzekutim**
'''''''''''''''''''''''

.. infonote::

    Ju lutemi vini re se **Karel nuk mund të ekzekutojë asnjë komandë në çdo kohë**. Më konkretisht, Karel nuk mund të shkojë përpara nëse është përpara një muri, ai nuk mund të marrë një top ku nuk ka një, dhe ai nuk mund të lëshojë një top nëse nuk ka topa me të.
    
    Provoni të fshini komandën e parë ``turn_left ()`` në programin e kaluar, dhe pastaj drejtojeni programin për të parë se çfarë ndodh.
    
    Kur programi që ekzekuton programin tonë vjen në një komandë që nuk mund të ekzekutohet, ekzekutimi i programit tonë ndërpritet dhe marrim një mesazh gabimi. Mesazhe të tilla janë normale dhe ne do t'i shohim ato sa herë që Karel nuk është në gjendje të bëjë atë që ne i thamë atij, ose kur deklarim jonë është e paqartë (më saktë, kur nuk është shkruar siç duhet). Në situata të tilla, ne duhet të përpiqemi të kuptojmë se cili është problemi, për të rregulluar programin dhe rifillimin e tij.
    
Më poshtë janë disa detyra për punë të pavarur. Me secilën detyrë, ofrohet një zgjidhje, të cilën mund ta shihni duke klikuar në butonin "Solution". Ju mund të kopjoni zgjidhjen e shfaqur në zonë për punën tuaj dhe ta provoni duke ekzekutuar programin. Vini re se zgjidhja juaj mund të ndryshojë nga e jona dhe të jetë akoma në rregull.

Ushtrime
------------------

Afrohu te kutia (3, 3)
'''''''''''''''''''''

.. questionnote::

   Në këtë detyrë nuk ka top, duhet të afroni Karel te kutia (3, 3).
   
.. karel:: Karel_intro_task_go_to_3_3
   :blockly:

   {
        setup:function() {
            var world = new World(3, 3);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("N");
            world.addNSWall(1, 1, 2);
            world.addNSWall(2, 2, 2);

        var robot = new Robot();

        var code = ["from karel import *",
                    "# Add missing commands"];
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getStreet() === 3 &&
           robot.getAvenue() === 3;
        },
   }
   
.. reveal:: Karel_intro_task_go_to_3_3_reveal
   :showtitle: Solution
   :hidetitle: Hide solution

   .. activecode:: Karel_intro_task_go_to_3_3_solution
      :passivecode: true
      
      from karel import *
      move(); move()               # to square (1, 3)
      turn_right(); move()         # to square (2, 3)
      turn_right(); move(); move() # to square (2, 1)
      turn_left(); move()          # to square (3, 1)
      turn_left(); move(); move()  # to square (3, 3)

Kapni topat
'''''''''''''''''

.. questionnote::

   Shkruani nje program në Karel që kap topat.
   
.. karel:: Karel_intro_task_collect_balls_in_2x2
   :blockly:

   {
        setup:function() {
            var world = new World(2, 2);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.putBall(2, 1);
            world.putBall(2, 2);
            world.putBall(1, 2);
            world.addEWWall(2, 1, 1);

        var robot = new Robot();

        var code = ["from karel import *",
                    "# Add missing commands",
                    "pick_ball()"];
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() === 3;
        },
   }
   
.. reveal:: Karel_intro_task_collect_balls_in_2x2_reveal
   :showtitle: Solution
   :hidetitle: Hide solution
  
   .. activecode:: Karel_intro_task_collect_balls_in_2x2_solution
      :passivecode: true
       
      from karel import *
      move(); pick_ball()                 # take the ball at square (2, 1)
      turn_right(); turn_right(); move()  # go back to square (1, 1)
      turn_right(); move(); pick_ball()   # pick the ball at square (1, 2)
      turn_right(); move(); pick_ball()   # pick the ball at square (2, 2)

Zig-zag
'''''''

.. questionnote::

  Karel duhet të jetë në kutinë (5, 1).

.. karel:: Karel_intro_task_stairs_fixed
   :blockly:

   {
      setup:function() {

         var Y = 3;
         var X = 2 * Y - 1;
         var world = new World(X, Y);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");

         // Vertical walls
         for (let y = 1; y < Y; y++) world.addNSWall(y, y, 1); // low left
         for (let y = 1; y < Y; y++) world.addNSWall(X - 1 - y, y, 1); // low right
         for (let y = 3; y <= Y; y++) world.addNSWall(y - 2, y, 1); // high left
         for (let y = 2; y <= Y; y++) world.addNSWall(X + 1 - y, y, 1); // high right
         
         // Horizontal walls
         for (let y = 1; y < Y - 1; y++) world.addEWWall(y + 1, y, 1); // low left
         for (let y = 2; y < Y; y++) world.addEWWall(y - 1, y, 1); // high left
         for (let y = 1; y < Y - 1; y++) world.addEWWall(X - 1 - y, y, 1); // low right
         for (let y = 1; y < Y; y++) world.addEWWall(X + 1 - y, y, 1); // high right

         var robot = new Robot();
         
         var code = ["from karel import *",
                     "# Add missing commands ",
                     ""];
    
         return {robot:robot, world:world, code:code};
      },
    
      isSuccess: function(robot, world) {
         return robot.getAvenue() == world.getAvenues() &&
            robot.getStreet() == 1;
      },
   }

.. reveal:: Karel_intro_task_stairs_fixed_reveal
   :showtitle: Solution
   :hidetitle: Hide solution

   .. activecode:: Karel_intro_task_stairs_fixed_solution
      :passivecode: true
      
      from karel import *
      turn_left(); move()     # to (1, 2)
      turn_right(); move()    # to (2, 2)
      turn_left(); move()     # to (2, 3)
      turn_right(); move()    # to (3, 3)
      turn_right(); move()    # to (3, 2)
      turn_left(); move()     # to (4, 2)
      turn_right(); move()    # to (4, 1)
      turn_left(); move()     # to (5, 1)


P, majtas, përsërit
''''''''''''''''''''''''''''''

.. questionnote::

  Karel duhet të jetë në kutinë (2, 3).
   

.. karel:: Karel_intro_task_spiral_left_fixed
   :blockly:

   {
      setup:function() {

         var N = 4;
         var world = new World(N, N);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");
         
         var i = 1;
         for (let d = N - 1; d > 0; d -= 2) { world.addEWWall(i, i, d); i++; }
         i = 2;
         for (let d = N - 2; d > 0; d -= 2) { world.addEWWall(i, N+1-i, d); i++; }
         i = 2;
         for (let d = N - 2; d > 0; d -= 2) { world.addNSWall(N+1-i, i, d); i++; }
         i = 1;
         for (let d = N - 3; d > 0; d -= 2) { world.addNSWall(i, i+2, d); i++; }
   
         var robot = new Robot();
      
         var code = ["from karel import *",
                     "# Add missing commands",
                     ""];
      
         return {robot:robot, world:world, code:code};
      },
 
      isSuccess: function(robot, world) {
         var N = world.getAvenues();
         return robot.getStreet() === Math.floor((N+2)/2) &&
           robot.getAvenue() === Math.floor((N+1)/2);
      },
   }

.. reveal:: Karel_intro_task_spiral_left_fixed_reveal
   :showtitle: Solution
   :hidetitle: Hide solution

   .. activecode:: Karel_intro_task_spiral_left_fixed_solution
      :passivecode: true
      
      from karel import *
      move(); move(); move(); turn_left() # to (4, 1)
      move(); move(); move(); turn_left() # to (4, 4)
      move(); move(); move(); turn_left() # to (1, 4)
      move(); move(); turn_left()         # to (1, 2)
      move(); move(); turn_left()         # to (3, 2)
      move(); turn_left()                 # to (3, 3)
      move();                             # to (2, 3)
