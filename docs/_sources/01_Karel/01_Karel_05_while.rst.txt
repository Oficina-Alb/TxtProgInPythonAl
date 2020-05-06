Zgjidhen detyra të shumta menjëherë
======================================

Duke gjykuar nga programet që kemi parë deri më tani, mund të mendohet se duhet të shkruhet një program special për secilin, madje edhe një detyrë paksa e ndryshme. Nëse do të ishte kështu, programimi do të ishte një punë shumë e lodhshme.

Për të zbatuar një program në një grup detyrash të ngjashme, na duhet që ai program të sillet ndryshe në situata të ndryshme. Kjo do të thotë që ne kemi nevojë për një mënyrë që programi të kuptojë situatën aktuale dhe pastaj të zgjedhim cilat komanda do të ekzekutohen, në varësi të situatës. Për nga situata, nënkuptojmë numrin e topave në një kuti ose me Karelin, pozicionin e mureve rreth Karelit etj. Një program që mund të marrë përgjigje në pyetjet në lidhje me Karel dhe rrethinat e tij gjithashtu mund të zgjidhë disa detyra të ngjashme, ose (me fjalë të tjera) një detyrë të përgjithshme.

Pyetje rreth Karelit
---------------------

Në fillim të kapitullit hyrës, ne pamë komanda për Karelin, me anë të të cilave ne e udhëzojmë atë të kryejë disa veprime (duke ecur përpara, duke u kthyer majtas dhe djathtas, duke marrë dhe hedhur topa). Përmendëm atëherë se ekzistojnë pesë funksione të tjera që lidhen me Karelin. Këto pesë funksione janë të ndryshme nga ato të mëparshmet, pasi që, duke përdorur këto funksione, bëjmë disa pyetje dhe marrim përgjigjet rreth Karelit ose kutisë në të cilin ndodhet. Këtu janë këto funksione:

- ``front_is_clear ()`` - ne pyesim nëse Kareli mund të shkojë përpara (a ka mure para tij). Ne marrim përgjigjen "po" ose "jo".
- ``num_balls_on_square ()`` - ne pyesim se sa topa ka në kutinë Karel është i ndezur. Ne marrim numrin e topave në kuti.
- ``is_ball_on_square ()`` - ne pyesim nëse ka të paktën një top në kutinë e Karelit. Ne marrim përgjigjen "po" ose "jo".
- ``num_balls_with_karel()`` - ne pyesim sa topa ka aktualisht Karel me të. Ne marrim numrin e topave që mban Karel.
- ``any_balls_with_karel()`` - ne pyesim nëse Karel ka të paktën një top me të. Ne arrim përgjigjen "po" ose "jo".

Ne nuk mund t'i shkruajmë këto funksione që japin përgjigje si deklarime të veçanta, siç kemi bërë deri më tani. Në vend të kësaj, ne i shkruajmë këto funksione si pjesë e disa deklaratave të Python. Le t'i hedhim një vështrim në shembujt.

Për sa kohë që është e nevojshme (*while*)
-------------------------------------------

Një mënyrë për të përdorur funksionet që japin përgjigje është t’i shkruani ato në deklarimn ``while``. Deklarimi *while* ekziston pothuajse në të gjitha gjuhët e programimit dhe është e shkruar shumë në mënyrë të ngjashme në gjuhë të ndryshme. Në Python duket kështu:

.. activecode:: while_syntax
   :passivecode: true

   while condition:
       statement_1
       ...
       statement_k

.. infonote::

    Kuptimi i ``while`` është: për sa kohë që "kushti" është përmbushur, ekzekutoni thënien ose deklarimet që shkruhen në pah poshtë. Fjala `kusht`` më lart nënkupton çdo gjë që është shkruar saktë në Python, dhe zbret në **po** ose **jo** (termi teknik për atë "asgjë "është një shprehje logjike**).

    Rregullat e shkrimit *while* deklarim kërkojnë shkrimin e karakterit ``:`` pas kushtit. Pas kësaj, ne shkruajmë deklarim që duam të përsërisim për sa kohë që kushti plotësohet, d.m.th., ndërsa përgjigja e pyetjes brenda gjendjes është **po** (ose **e vërtetë**) . Këto thënie përsëritëse bëjnë trupin e deklarims ndërsa, dhe shkruhen në mënyrë të theksuar në rreshtat vijues (numri i njëjtë i hapësirave shtohet para secilës prej deklaratave të përsëritura).

Gjendja shqyrtohet para çdo ekzekutimi të deklaratave në trupin e deklarims *while*. Herën e parë kur kushti nuk plotësohet, *while* ekzekutimi i deklarims (së bashku me deklarimet në trupin e tij) është i plotë, dhe deklarim tjetër që duhet ekzekutuar është ajo e shënuar nën trupin e *while*. Për shembull, nëse ekzekutojmë:

.. activecode:: while_example
   :passivecode: true

   while front_is_clear():
       move()
   pick_ball()

Kareli do të ecë përpara aq sa mundet, domethënë, derisa të marrim përgjigjen "jo" për pyetjen front_is_clear (), që do të thotë se Kareli ka hasur në një mur. Kur ai përfundon lëvizjen, Karel do të marrë topin. Në rast se Karel është tashmë para murit, lëvizja e komandës () nuk do të ekzekutohet fare dhe Karel menjëherë do të marrë topin.

~~~~

Secili nga shembujt dhe detyrat e mëposhtme është një i përgjithshëm. Kjo do të thotë që, për secilën detyrë, në nisjet e programeve të ndryshme, detyra do të duket e ngjashme, por pak më ndryshe. Programi duhet të shkruhet për të zgjidhur detyrën në secilën nga këto raste të ngjashme.

Shkoni para sa të mundeni dhe kapni topin
'''''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Ka një ose më shumë kuti para Karelit, dhe në kutinë e fundit ka një top. Shkruaj një program që do të bëjë që Karel të marrë topin nga kutia e fundit.
    
    **Programi duhet të zhvillohet shumë herë**, sepse në lançime të ndryshme, bota e Karel do të ketë numër të ndryshëm të kutive. Këtu janë disa shembuj se si mund të duket detyra:
     
   .. image:: ../../_images/Karel/While_01.jpg
      :width: 600px   
      :align: center

Ne do të përdorim while për të lëvizur karwl, dhe pastaj do ti themi të marrëë topin.

.. karel:: Karel_while__many_squares_and_ball_at_the_end
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var N = 2 + random(14);
         var world = new World(N, 1);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");
         world.putBall(N, 1);
      
         var robot = new Robot();
      
         var code = ["from karel import *",
                     "while front_is_clear():",
                     "    move()",
                     "pick_ball()"];
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() === 1;
      }
   }

.. infonote::
    
    Mund të ndodhë që një program shpesh prodhon një rezultat të mirë, herë pas here duke dhënë një rezultat të keq ose duke u ndërprerë për shkak të një gabimi. **Një program i tillë duhet të konsiderohet i gabuar (i dëmtuar)**. Programi i saktë gjithmonë duhet të japë rezultatin e saktë.

Ushtime
------------------

Shkoni një katror përpara dhe kapni të gjitha topat
''''''''''''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Ekziston saktësisht një kuti përpara Karelit, dhe mbi të ka ndonjë numër topash. Karl duhet t'i marrë ato.
  
Pas udhëzimeve në programin e mëposhtëm, Karel do të përpiqet të përsërisë pafundësisht komandën ``pick_ball ()``. Sidoqoftë, kur Karel merr të gjitha topat nga kutia, ne do të marrim një mesazh gabimi sepse i thamëm Karelit të marrë një top nga kuti e zbrazët (mos ngurroni ta provoni këtë dhe të shihni se si duket mesazhi i gabimit). Mundohuni të rregulloni programin në mënyrë që Karel të marrë topat vetëm ndërsa ka disa në kuti.

.. karel:: Karel_while__one_square_many_balls
   :blockly:

   {
        setup:function() {
           function random(n) {
              return Math.floor(n * Math.random());
           }
           
           var world = new World(2, 1);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           
           var N = random(14);
           world.putBalls(2, 1, N);

           var robot = new Robot();

           var code = ["from karel import *",
                       "move()",
                       "while True: # instead of True use the function is_ball_on_square()",
                       "    pick_ball()",
                       ""];
           return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           var N = world.getAvenues();
           for (var k = 1; k <= N; k++)
              if (world.getBalls(k, 1) > 0)
                 return false;
               
           return true;
        },
   }

.. commented out
   .. reveal:: Karel_while__one_square_many_balls_reveal
      :showtitle: Zgjdhja
      :hidetitle: Fshih zjgidhjen
   
      .. activecode:: Karel_while__one_square_many_balls_solution
         :passivecode: true
         
         from karel import *
         move()
         while is_ball_on_square():
             pick_ball()

Shko sa larg të mundesh, merr top ne çdo kuti
'''''''''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Ka një ose më shumë kuti përpara Karelit, dhe në secilin kuti ka një top. Shkruaj një program që e bën Karel të mbledhë topat nga të gjitha sheshet.
   
    **Drejtojeni këtë program disa herë,** për t'u siguruar që ajo zgjidh detyrën, pavarësisht nga gjatësia e rrugës së Karel.
   
Një deklarim *while* duhet të përdoret si për lëvizjen e Karelit ashtu edhe për marrjen e topave.

.. karel:: Karel_while__many_squares_and_ball_at_each
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var N = 2 + random(8);
         var world = new World(N, 1);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");
         for (var k = 2; k <= N; k++)
             world.putBall(k, 1);

         var robot = new Robot();
      
         var code = ["from karel import *",
                     "# complete the program",
                     ];
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return (robot.getBalls() == world.getAvenues() - 1);
      }
   }

Lëviz të gjitha topat nga kutia e fundit në të parën
'''''''''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Ka një ose më shumë kuti para Karelit, dhe ka disa topa në kutinë e fundit. Kareli duhet të marrë të gjitha topat nga kutia e fundit dhe t'i lërë ata në kutinë e parë.
   
    (Drejtoni programin disa herë.)
   
Në këtë detyrë, katër loops janë të nevojshme njëra pas tjetrës (jo njëra brenda tjetrës):

- Në loop e parë, Kareli arrin në kutinë e fundit
- Në loop e dytë, Karel merr topat
- Në loop e tretë, Kareli kthehet në kutinë fillestare
- Në loop e fundit, Karl lë të gjitha topat që ka me vete

Sigurisht, pas loops të parë ose të dytë, Karel duhet të kthehet në loops fillestar (dy herë në të majtë ose dy herë në të djathtë).

.. karel:: Karel_while__bring_balls_to_front_square
    :blockly:

    {
        setup:function() {
            function random(n) {
                return Math.floor(n * Math.random());
            }

            var N = 2 + random(5);
            var world = new World(N, 1);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.putBalls(N, 1, 2 + random(4));

            var robot = new Robot();
      
            var code = ["from karel import *",
                        "# go forward while you can",
                        "# take all the balls",
                        "turn_right()",
                        "turn_right()",
                        "# go forward while  you can",
                        "# drop all the balls",
                       ];
            return {robot:robot, world:world, code:code};
        },
      
        isSuccess: function(robot, world) {
            var N = world.getAvenues();
            for (var k = 2; k <= N; k++) {
                if (world.getBalls(k, 1) > 0)
                    return false;
            }
            if (robot.getBalls() > 0)
                return false;

            return true;
        }
    }
    
.. commented out
   .. reveal:: Karel_while__bring_balls_to_front_square_reveal
       :showtitle: Solution
       :hidetitle: Hide solution
   
       .. activecode:: Karel_while__bring_balls_to_front_square_solution
           :passivecode: true
         
           from karel import *
           while front_is_clear():
               move()
           while is_ball_on_square():
               pick_ball()
           turn_right()
           turn_right()
           while front_is_clear():
               move()
           while any_balls_with_karel():
               drop_ball()

Vendos topin në rreshtin e parë
''''''''''''''''''''''''''''''''''

.. questionnote::

  Bota e Karel kësaj here përbëhet nga dy rreshta me gjatësi të njëjtë, por të panjohur. Kareli është në këndin e poshtëm të majtë, përballë lindjes. Të gjitha kutinë e rreshtit të sipërm janë bosh, dhe çdo katror i rreshtit të parë përmban një top, **duke përfshirë kutinë ku Karel është**. Detyra e Karel është të vendosë një top të vetëm në secilin katror të rreshtit të lartë.
  
  (Lanëo programin disa herë.)
  
.. karel:: Karel_while__put_balls_in_upper_row
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var N = 2 + random(4);
         var world = new World(N, 2);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");
         for (var k = 1; k <= N; k++)
             world.putBall(k, 1);

         var robot = new Robot();
      
         var code = ["from karel import *",
                     "# complete the program",
                     ];
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
          var N = world.getAvenues();
          for (var k = 1; k <= N; k++) {
              if (world.getBalls(k, 1) > 0)
                  return false;
              if (world.getBalls(k, 2) != 1)
                  return false;
          }
          if (robot.getBalls() > 0)
              return false;

          return true;
      }
   }

.. reveal:: Karel_while__put_balls_in_upper_row_reveal
    :showtitle: Hint
    :hidetitle: Hide hint
    
    Ne japim intruksione që ndërtojnë programin:

    .. activecode:: Karel_while__put_balls_in_upper_row_solution
        :passivecode: true
        
        pick up the ball
        while you can go forward:
            go forward
            pick up the ball
        turn towards the top row
        get in the top row
        turn towards the beginning of the row
        drop the ball
        while you can go forward:
            go forward
            drop the ball

.. commented out
    .. reveal:: Karel_while__put_balls_in_upper_row_reveal
        :showtitle: Zgjidhja
        :hidetitle: Fshih zjgidhjen

        .. activecode:: Karel_while__put_balls_in_upper_row_solution
            :passivecode: true
          
            from karel import *
            pick_ball()
            while front_is_clear():
                move()
                pick_ball()
            turn_left()
            move()
            turn_left()
            drop_ball()
            while front_is_clear():
                move()
                drop_ball()
