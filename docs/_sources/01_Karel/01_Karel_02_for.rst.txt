Shkurtoni programet tuaja
=============================

Në kapitullin e mëparshëm kishte detyra në të cilat do të ishte e përshtatshme për ne që të kemi një mënyrë më të shkurtër për të specifikuar disa veprime përsëritëse. Për shembull, na duhej që Kareli të shkonte tre hapa përpara. Në rastin e vetëm tre hapave, është mjaft e lehtë të shkruani deklarimn ``move ()`` tri herë, por kur Karel duhet të bëjë, të themi, dymbëdhjetë hapa përpara, nëse shkruajmë:

.. activecode:: Karel_for_12_steps_manual
   :passivecode: true
   
   move(); move(); move(); move(); move()
   move(); move(); move(); move(); move()
   move(); move()

mënyra më e madhe e shkrimit të programeve është më e prirur për gabime, dhe është gjithashtu më e vështirë të lexosh programe të tilla. Nëse mendoni se edhe dymbëdhjetë përsëritjet nuk janë problem, mbani në mend se në botën e programimit, nuk është e pazakontë që një deklarim të përsëritet një milion herë.

*for*
---------------

Një mënyrë më e mirë për të specifikuar një manovër të tillë do të ishte të thoni "dymbëdhjetë herë shkoni përpara". Për të përsëritur një deklarim (ose një grup deklaratash) disa herë, ne përdorim deklarimn ``for``. Forma më e përdorur e kësaj deklarate në Python duket si kjo:

.. activecode:: Karel_for_syntax
   :passivecode: true
   
   for i in range(n):
       statement_1
       ...
       statement_k

Më vonë, do të shohim edhe disa forma të tjera të deklarimit ``for`` .

Duke përdorur deklarimn ``for``, shembulli ynë me 12 përsëritje të një hapi përpara mund të shkruhet në këtë mënyrë:
      
.. activecode:: Karel_for_12_steps_loop
   :passivecode: true
   
   for i in range(12):
       move()


Këtu ne japim një përshkrim pak më të detajuar të deklarims ``for``. Ju nuk duhet ta kuptoni plotësisht atë në këtë kohë - përdorimi dhe rregullat e shkrimit të tij do të bëhen më të qarta me shembujt e mëposhtëm. Nëse keni nevojë për më shumë detaje rreth deklarims ``for`` më vonë, mund të ktheheni në këtë shpjegim (por kini kujdes që nuk përshkruan format e tjera të deklarims *for*).

.. infonote ::

   Sipas rregullave të programeve të shkrimit në Python, fjalët "for" dhe "in", si dhe ``:`` në fund të rreshtit, janë të gjitha pjesët e detyrueshme të *for*.
   
   - Shkronja ``i`` këtu shërben si emër për vendin ku mbajmë numrin e përsëritjeve. Në vend të ``i``, një emër tjetër mund të përdoret për këtë (ne do të kthehemi në këtë më në detaje kur të kemi nevojë).
  
   - ``range (n)`` paraqet një gamë të numrave të plotë duke filluar me 0, dhe ``n`` tregon se sa numra përmban kjo diapazonë. Për shembull, ``range(3)`` është varg që përmban numrat: kodin: ` 0, 1, 2``, dhe ``range(7)`` është varg i numrave: kodi: `0, 1, 2, 3, 4, 5, 6`.

   - deklarimet në rreshtat e mëposhtëm bëjnë të ashtuquajturin **trupin e deklarims for**. Këto mund të jenë çdo deklarim në Python, duke përfshirë funksione për administrimin e Karelit, deklarime të tjera `` për``, ose disa deklarim që ne nuk kemi përmendur ende. Mund të ketë një ose më shumë deklarime të tilla në trupin e deklarims.

   ``for i in range(3)`` interpretohet si: " vlera e *i* në rangun [0, 1, 2]". Kjo do të thotë që deklarimet në trupin e deklarims do të ekzekutohen një herë për i = 0, për i = 1, dhe për i = 2, pra gjithsej tre herë. Tani nuk do ta përdorim vlerën e *i* në trupin e deklarims, kështu që duhet të dimë vetëm sa vlera ka në rang (kjo është numri në kllapa pas fjalës ``varg``), sepse deklarimet në trup do të ekzekutohen atë numër herë.
   
   Për të sqaruar se cilat janë deklarimet në trupin e deklarims *for*, këto deklarim shkruhen në pah (zhvendosur në të djathtë), të gjitha për të njëjtin numër hapësirash. Ne mund të zgjedhim numrin e hapësirave për vendosje për secilën deklarim *for*. Sidoqoftë, është një praktikë e mirë të zgjedhim gjithmonë të njëjtin numër, sepse në këtë mënyrë, do të mësohemi me planin e caktuar të programit dhe kodi do të jetë më i lexueshëm. Zgjedhja më e zakonshme për vendosje është 4 hapësira, kështu që ne do ta pranojmë gjithashtu.
   
*for* është e njohur edhe si një loop, sepse duke ndjekur deklarimet që ekzekutojmë, kur të vijmë te deklarim *for*, ne mbështesim disa herë përmes deklaratave në trupin e saj. Termi "loop" është më pak i saktë (krahasuar me "for"), sepse siç do të shohim së shpejti, deklarim *for* nuk është e vetmja lak që ekziston. Fjala "loop" zakonisht përdoret kur është e qartë (ose e parëndësishme) për cilën thënie të saktë të loop për të cilën po flasim, sepse është më lehtë të thuash, për shembull, "trup loop", sesa "për trupin e deklarims".

Detyra
------------------

Zhvendosni 15 kuti përpara dhe merrni topin
''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Shkruaj një program mbi bazën e të cilit Karel do të zhvendoset në kutinë (16, 1) dhe do të marr topin.

Një program më i gjatë (dhe më i shëmtuar) është duke pritur për ju në zonën e zgjidhjes. Provoni ta zëvendësoni atë me deklarimn *for*. Në rast se zgjidhja juaj me deklarimn *for* nuk funksionon (gjë që shpesh ndodh në fillim), mund ta shihni zgjidhjen tonë duke klikuar në butonin "Solution" më poshtë.

.. karel:: Karel_for_15_steps_and_take
   :blockly:

   {
      setup:function() {
          var world = new World(16, 1);
          world.setRobotStartAvenue(1);
          world.setRobotStartStreet(1);
          world.setRobotStartDirection("E");
          world.putBall(16, 1);
      
         var robot = new Robot();
      
         var code = ["from karel import *",
                     "move(); move(); move(); move(); move()",
                     "move(); move(); move(); move(); move()",
                     "move(); move(); move(); move(); move()",
                     "pick_ball()"];
                  
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() === 1;
      }
   }

.. reveal:: Karel_for_15_steps_and_take_reveal
   :showtitle: Zgjidhja
   :hidetitle: Fshih zgjidhjen
   
   .. activecode:: Karel_for_15_steps_and_take_solution
      :passivecode: true
      
      from karel import *
      for i in range(15):
          move()
      pick_ball()

Shko një kuti para dhe mblidh 10 topa
''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

  Ka një kuti para Karelit, dhe ka 14 topa mbi të. Kareli duhet të marr saktësisht dhjetë topa.
  
.. karel:: Karel_for_one_square_take_10_balls
   :blockly:

   {
        setup:function() {
           var world = new World(2, 1);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           
           world.putBalls(2, 1, 14);

           var robot = new Robot();

           var code = ["from karel import *",
                       "move()",
                       "# Complete the program",
                       ""];
           return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() == 10;
        },
   }
   
.. reveal:: Karel_for_one_square_take_10_balls_reveal
   :showtitle: Zgjidhja
   :hidetitle: Fshih Zgjidhjen

   .. activecode:: Karel_for_one_square_take_10_balls_solution
      :passivecode: true
      
      from karel import *
      move()
      for i in range(10):
          pick_ball()


Merrni një top në 6 kutitë e ardhshme
'''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

  Ka tetë kuti para Karelit, dhe në secilën prej tyre ka një top. Karel duhet të marr të gjitha topat.
  
Vini re se dy gjëra duhet të bëhen në loop: të ecni përpara dhe të merrni topin.

.. karel:: Karel_for_EightSquaresOneBallEach_TakeAllBalls
   :blockly:

   {
        setup:function() {
           var numAvenues = 9;
           var world = new World(numAvenues, 1);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           
         for (var k = 2; k <= numAvenues; k++)
            world.putBall(k, 1);

           var robot = new Robot();

           var code = ["from karel import *",
                       "# Complete the program",
                       ""];
           return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() == world.getAvenues() - 1;
        },
   }
   
.. reveal:: Karel_for_EightSquaresOneBallEach_TakeAllBalls_reveal
   :showtitle: Solution
   :hidetitle: Hide solution

   .. activecode:: Karel_for_EightSquaresOneBallEach_TakeAllBalls_solution
      :passivecode: true
      
      from karel import *
      for i in range(8):
          move()
          pick_ball()


Merrni 5 topa nga secila nga 3 kutitë
'''''''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

    Ka tre kuti para Karelit, dhe në secilën prej tyre ka pesë topa. Karel duhet të marr të gjitha topat.
  
.. karel:: Karel_for_Take_5_5_5
   :blockly:

   {
        setup:function() {
           var world = new World(4, 1);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           
           world.putBalls(2, 1, 5);
           world.putBalls(3, 1, 5);
           world.putBalls(4, 1, 5);
           
           var robot = new Robot();

           var code = ["from karel import *",
                       "# Complete the program",
                       ""];
           return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() == 15;
        },
   }
   
.. reveal:: Karel_for_Take_5_5_5_reveal
   :showtitle: Zgjidhja
   :hidetitle: Fshih zgjidhjen
   
   .. activecode:: Karel_for_Take_5_5_5_solution
      :passivecode: true
      
      from karel import *
      move()
      for i in range(5):
          pick_ball()
      move()
      for i in range(5):
          pick_ball()
      move()
      for i in range(5):
          pick_ball()
