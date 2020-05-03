Programe të shkurtra
=====================

Le të kthehemi në programin e fundit të mësimit të mëparshëm. Ne kishim nevojë për Karel që të merrnim pesë topa nga secila nga tre sheshet në para të tij.

.. image:: ../../_images/Karel/nested_for_3x5.png
    :width: 300px
    :align: center

Programi që zgjidh detyrën mund të duket si ky:

.. activecode:: Karel_nested_for__intro_1
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
        
Ne shohim që, në këtë program, grupi i mëposhtëm i deklaratave përsëritet tri herë:

.. activecode:: Karel_nested_for__intro_2
   :passivecode: true

    move()
    for i in range(5):
        pick_ball()

Kjo na lejon të shkurtojmë programin më tej. Në shpjegimin e thënies *for*, ne përmendëm se sythe të tjerë mund të gjenden në trupin e lakut. Tani kemi mundësinë që ta përdorim.
 
Sythe fole *for* 
------------------

Kur ka një loop të dytë në trupin e njërit loop, atëherë lak i parë quhet një lak i jashtëm dhe tjetri quhet një loop i brendshëm. Së bashku ne i quajmë ata sythe të loop ose të futur. Në shembullin vijues, do të shohim sesi shkruhen sythe *for*.

Kap 5 topa tre herë
''''''''''''''''''''''''''''''

.. questionnote::

  Ka tre sheshe përpara Karelit, dhe ka secila prej tyre 5 topa. Karel duhet të marr të gjitha topat.

Detyra përsëritet, por tani ne do ta zgjidhim atë në një mënyrë tjetër.

.. infonote::
    Ne përmendëm se ``i`` në shembujt e mëparshëm të deklaratave *for* është një emër për banakun e përsëritjes. Tani, për herë të parë duhet të numërojmë gjëra të tjera (topa) gjatë llogaritjes së një gjëje (kutie). Kjo do të thotë, për shembull, që do të na duhet ta dimë saktësisht kur jemi në kutinë e tretë, duke marrë topin e dytë. Prandaj, ne nuk mund të përdorim të njëjtin emër për të dy sportelet, kështu që kemi futur emra të rinj për sportelet në vend të `` i`` të mëparshëm. Në programin vijues, ne e quajmë banak katror ``i_square``, dhe emri për banakun e topit është ``i_ball``.
   
.. karel:: Karel_for_TakeMxN
   :blockly:

   {
        setup:function() {
           var numAvenues = 4;
           var numBalls = 5;
           var world = new World(numAvenues, 1);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           
           for (var k = 2; k <= numAvenues; k++)
              world.putBalls(k, 1, numBalls);
           
           var robot = new Robot();

           var code = ["from karel import *",
                       "for i_square in range(3):",
                       "    move()",
                       "    for i_ball in range(5):",
                       "        pick_ball()",
                       ""];
           return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           return robot.getBalls() == 15; // 3 x 5 balls
        },
   }

Në zgjidhjen e dhënë, thënia *pick_ball ()* është e theksuar gjithashtu, sepse ekzekutohet ato për secilin ``i_ball`` nga diapazoni [0, 1, 2, 3, 4]. Për më tepër, e gjithë deklarim ``për i_ball në varg (5):`` (së bashku me trupin e saj dhe thënia *move()* mbi të), përsëritet 3 herë, ato për secilin ``i_square`` nga diapazoni [0, 1, 2]. Kjo do të thotë që komanda *pick_ball()* ekzekuton gjithsej 3 x 5 = 15 herë (në secilën nga tre sheshet pesë herë).

.. infonote ::
    Me sythe të loops, është e nevojshme t'i kushtohet vëmendje shtesë theksit të saktë të deklaratave, sepse bëhet disi më e ndërlikuar. Shënimi i gabuar i disa komandave mund të çojë në rezultatin e gabuar, ose në një program që nuk funksionon fare.
   
Ushtrime
------------------

Evito
''''

.. questionnote::

  Përpara Karelit, ka një top në çdo kuti të tretë, dhe Kareli duhet t'i marrë të dy.
  
Karl duhet të përsërisë një grup veprimesh "Leviz tre herë, dhe pastaj të marrë topin" 2 herë.

.. karel:: Karel_for_every_nth_square
    :blockly:

    {
        setup:function() {
            var everyNth = 3;
            var numRepetitions = 2;
            var numBalls = 1;
            var numAvenues = 1 + numRepetitions * everyNth;
            var world = new World(numAvenues, 1);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
           
            for (var k = 1; k <= numRepetitions; k++)
                world.putBalls(1+k*everyNth, 1, numBalls);
            
            var robot = new Robot();
         
            var code = ["from karel import *",
                        "for i_rep in range(2):  # repeat twice everything that follows",
                        "    # use for statement to tell Karel to go 3 squares forward",
                        "    pick_ball()             # take the ball",
                        ""];
    
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
            return robot.getBalls() == 2; // number of repetitions
        },
    }

.. commented out
   .. reveal:: Karel_for_every_nth_square_reveal
       :showtitle: Решење
       :hidetitle: Сакриј решење
   
       .. activecode:: Karel_for_every_nth_square_solution
           :passivecode: true
         
           from karel import *
           for i_pon in range(2):     # repeat twice everything that follows
               for i_polje in range(3):   # go 3 squares forward
                   move()
               pick_ball()            # take the ball

5 topa në çdo kuti të tretë
'''''''''''''''''''''''''''''

.. questionnote::

  Ka pesë topa në çdo shesh të tretë përballë Karelit, dhe ai duhet t'i mbledhë të gjitha.
  
Detyra është e ngjashme me të mëparshmën, thjesht duhet të përsërisësh marrjen e topit. Sigurohuni që loop për të marrë topa është nën loop për të ecur përpara, jo në të.


.. karel:: Karel_for_every_nth_square_5
    :blockly:

    {
        setup:function() {
            var everyNth = 3;
            var numRepetitions = 2;
            var numBalls = 5;
            var numAvenues = 1 + numRepetitions * everyNth;
            var world = new World(numAvenues, 1);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
           
            for (var k = 1; k <= numRepetitions; k++)
                world.putBalls(1+k*everyNth, 1, numBalls);
            
            var robot = new Robot();
         
            var code = ["from karel import *",
                        "for i_rep in range(2):      # repeat twice everything that follows",
                        "    # use for statement to tell Karel to go 3 squares forward",
                        "    # use a new for statement to tell Karel to take 5 balls",
                        ""];
    
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
            return robot.getBalls() == 10; // numRepetitions x numBalls
        },
    }

.. commented out
   .. reveal:: Karel_for_every_nth_square_5_reveal
       :showtitle: Решење
       :hidetitle: Сакриј решење
   
       .. activecode:: Karel_for_every_nth_square_5_solution
           :passivecode: true
         
           from karel import *
           for i_pon in range(2):     # repeat twice everything that follows
               for i_polje in range(3):   # go 3 squares forward
                   move()
               for i_loptica in range(5): # to take 5 balls
                   pick_ball()


Dil
''''''''

.. questionnote::

  Kap edhe një herë duhet të marr të gjitha topat.
  
Loop i jashtëm duhet të ekzekutohet 3 herë, dhe në të Karel duhet të bëjë si më poshtë:

- Përsëritni dy herë dy veprimet: "lëviz përpara" dhe "merr topin"
- Kthehu majtas

.. karel:: Karel_for_ring
    :blockly:

    {
        setup:function() {
            var w = [
               '███████',
               '█1.1.1█',
               '█.███.█',
               '█0.0█1█',
               '█████.█',
               '█E.1.1█',
               '███████'
            ];

            var ny = Math.floor(w.length / 2);
            var nx = Math.floor(w[0].length / 2);
            var world = new World(nx, ny);

            for (let y = 1; y <= ny; y++) {
                let wy = 2*(ny-y) + 1;
                for (let x = 1; x <= nx; x++) {
                    let wx = 2*x - 1;
                    if (y < ny && w[wy - 1].charAt(wx) == "█") world.addEWWall(x, y, 1);
                    if (x < nx && w[wy].charAt(wx + 1) == "█") world.addNSWall(x, y, 1);
                    let c = w[wy].charAt(wx);
                    let pos = "SWEN".indexOf(c);
                    if (pos > -1) {
                        world.setRobotStartAvenue(x);
                        world.setRobotStartStreet(y);
                        world.setRobotStartDirection("SWEN".charAt(pos));
                    }
                    let d = w[wy].charCodeAt(wx);
                    if (d >= 48 && d < 58) world.putBalls(x, y, d - 48);
                }
            }

            var robot = new Robot();
         
            var code = ["from karel import *",
                        "... # complete the program",
                        ""];
                     
            return {robot:robot, world:world, code:code};
        },
      
        isSuccess: function(robot, world) {
           return robot.getBalls() == 6;
        }
    }

.. reveal:: Karel_for_ring_reveal_1
    :showtitle: Hint
    :hidetitle: Hide hint

    Ne kemi bërë udhëzime verbale pak më të ngjashme me programin, provoni t'i ktheni ato në deklarim. Nëse ende dëshironi të shihni vetë programin, klikoni në butonin "Solution".
    
    .. activecode:: Karel_for_ring_solution_1
        :passivecode: true
      
        for each of the 3 sides:
            for each of the 2 squares:
                move forward
                pick the ball
            turn left

    .. reveal:: Karel_for_ring_reveal_2
       :showtitle: Solution
       :hidetitle: Hide solution
   
       .. activecode:: Karel_for_ring_solution_2
           :passivecode: true
         
           from karel import *
           for i_side in range(3):     # repeat three times everything that follows
               for i_square in range(2):     # two times do "move" and "pick ball"
                   move()
                   pick_ball()
               turn_left()                   # turn along the next side



Dil dhe kap 3 topa çdo herë
'''''''''''''''''''''''''''''''''''

.. questionnote::

  Shkruaj një program me të cilin Karel do të marr të gjitha 18 topat.
  
Kjo detyrë ndryshon nga ajo e mëparshmja në vetëm një gjë: tani marrja e topave duhet të jetë në një loop shtesë. Kjo do të thotë se do të kemi tre sythe loops: një që numëron anët e labirint, një që numëron sheshet përgjatë njërës anë, dhe të tretën që numëron topat në një katror.

.. karel:: Karel_for_ring_3
    :blockly:

    {
        setup:function() {
            var w = [
               '███████',
               '█3.3.3█',
               '█.███.█',
               '█0.0█3█',
               '█████.█',
               '█E.3.3█',
               '███████'
            ];

            var ny = Math.floor(w.length / 2);
            var nx = Math.floor(w[0].length / 2);
            var world = new World(nx, ny);

            for (let y = 1; y <= ny; y++) {
                let wy = 2*(ny-y) + 1;
                for (let x = 1; x <= nx; x++) {
                    let wx = 2*x - 1;
                    if (y < ny && w[wy - 1].charAt(wx) == "█") world.addEWWall(x, y, 1);
                    if (x < nx && w[wy].charAt(wx + 1) == "█") world.addNSWall(x, y, 1);
                    let c = w[wy].charAt(wx);
                    let pos = "SWEN".indexOf(c);
                    if (pos > -1) {
                        world.setRobotStartAvenue(x);
                        world.setRobotStartStreet(y);
                        world.setRobotStartDirection("SWEN".charAt(pos));
                    }
                    let d = w[wy].charCodeAt(wx);
                    if (d >= 48 && d < 58) world.putBalls(x, y, d - 48);
                }
            }

            var robot = new Robot();
         
            var code = ["from karel import *",
                        "... # complete the program",
                        ""];
                     
            return {robot:robot, world:world, code:code};
        },
      
        isSuccess: function(robot, world) {
           return robot.getBalls() == 18;
        }
    }

.. reveal:: Karel_for_ring_3_reveal
    :showtitle: Hint
    :hidetitle: Hide hint

    Again, we give instructions which look like a program (this time without the program itself).
    
    .. activecode:: Karel_for_ring_3_solution
        :passivecode: true
      
        for each of the 3 sides:
            for each of the 2 squares:
                move forward
                for each of the 3 balls:
                    pick the ball
            turn left

.. commented out
   .. reveal:: Karel_for_ring_3_reveal
       :showtitle: Solution
       :hidetitle: Hide solution
   
       .. activecode:: Karel_for_ring_3_solution
           :passivecode: true
         
           from karel import *
           for i_side in range(3):     # three times repeat everything that follows
               for i_square in range(2):   # repeat twice "move forward" and "take 3 balls"
                   move()
                   for i_ball in range(3):
                       pick_ball()
               turn_left()             # turn along the next side
