*For* praktikë
============================

Në këtë seksion do të praktikojmë përdorimin e *for*

Ushtrime
------------------

Tre herë lart dhe poshtë
'''''''''''''''''''''''''''

.. questionnote::

  Karel është në një bord drejtkëndor prej 5 rreshtave dhe 7 kolonave dhe duhet të arrijë në kutinë e poshtme të djathtë.


Kareli duhet të përsërisë një veprim kompleks tre herë, domethënë të shkojë në kolonën tjetër në të djathtë, të shkojë në krye të kolonës, të shkojë në një kolonë tjetër në të djathtë, të zbresë në rreshtin e parë dhe në fund të kthehet drejt kolona e fundit për t’u përgatitur për përsëritjen tjetër.

Përfundoni programin, duke marrë parasysh që sporteli në *for* deklarimet që shkruani nuk duhet të emërohet ``i`` (ky emër tashmë përdoret në loop/in e jashtëm).

.. karel:: Karel_for_up_col_down_col_constant
   :blockly:

   {
      setup:function() {

         var X2 = 3;
         var Y = 5;
         var world = new World(2*X2+1, Y);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");
            
         world.addEWWall(1, 1, 1);
         for (let x = 0; x < X2; x++) { 
            world.addNSWall(2*x + 1, 2, Y - 1);
            world.addNSWall(2*x + 2, 1, Y - 1);
         }
         
         var robot = new Robot();
         
         var code = ["from karel import *",
                     "for i in range(3):   # repeat everything that follows 3 times",
                     "    move(); turn_left()  # Enter the next column and turn north",
                     "    # use the for statement to tell Karel to go to the top edge",
                     "    ",
                     "    turn_right(); move() # go to the next column",
                     "    turn_right()             # turn south",
                     "    # use the for statement to tell Karel to go to the bottom edge",
                     "    ",
                     "    turn_left()          #    turn east",
                     ""];
    
         return {robot:robot, world:world, code:code};
      },
    
      isSuccess: function(robot, world) {
         return robot.getAvenue() == world.getAvenues() &&
            robot.getStreet() == 1;
      },
   }

.. reveal:: Karel_for_up_col_down_col_constant_reveal
   :showtitle: Solution
   :hidetitle: Hide solution

   .. activecode:: Karel_for_up_col_down_col_constant_solution
      :passivecode: true
      
      from karel import *
      for i in range(3):       # repeat everything that follows 3 times
          move(); turn_left()      # go to the next column and turn north
          for i_up in range(4):    # go to the top edge
              move()

          turn_right(); move()     # go to the next column
          turn_right()             # turn south
          for i_down in range(4):  # go to the bottom edge
              move()

          turn_left()              # turn east

Sill të gjithë topat nga të gjithë fushat
'''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

  Kareli duhet të sjellë të gjitha 12 topat në kutinë fillestare.

Karél duhet të përsërisë "hapin në kolonën tjetër dhe ta zbrazë" katër herë dhe përfundimisht të kthehet në kutinë fillestare dhe t’i hedhë të gjitha topat. Kareli mund ta zbrazë secilën kolonë duke përsëritur "lëviz një hap përpara dhe ta marr topin" tre herë, dhe pastaj të kthehet në fund të kolonës, përballë kolonës tjetër.

Plotëso programin.

.. karel:: Karel_for_fetch_from_matrix
   :blockly:

   {
      setup:function() {
         var X = 5;
         var Y = 4;
         var world = new World(X, Y);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");

         world.addEWWall(1, 1, 1);
         world.addNSWall(1, 2, Y - 1);
         
         for (var col = 2; col <= X; col++) {
            for (var row = 2; row <= Y; row++) {
               world.putBall(col, row);
            }
         }
         
         var robot = new Robot();
         
         var code = ["from karel import *",
                     "for i_column in range(4):      # repeat four times emptying one column",
                     "    move()                     # enter the next column",
                     "    turn_left()                # turn north",
                     "    #for ...                       # repeat 'move forward and take the ball' 3 times",
                     "",
                     "    turn_right(); turn_right() # turn south",
                     "    #for ...                   # go 3 steps forward to the bottom edge",
                     "",
                     "    turn_left()                # turn east",
                     "    ",
                     "# (Karel went through all the squares)",
                     "turn_left()                    # turn west",
                     "turn_left()",
                     "#for ...                       # come back to the starting square",
                     "    ",
                     "for i_ball in range(12):       # drop all the balls",
                     "    drop_ball()",
                     ""];
    
         return {robot:robot, world:world, code:code};
      },
    
      isSuccess: function(robot, world) {
         return world.getBalls(1, 1) == 12 &&
            robot.getAvenue() == 1 &&
            robot.getStreet() == 1;
      },
   }

.. reveal:: Karel_for_fetch_from_matrix_reveal
   :showtitle: Zgjidhja
   :hidetitle: Fshih zgjidhjen

   .. activecode:: Karel_for_fetch_from_matrix_solution
      :passivecode: true
      
      from karel import *
      for i_column in range(4):    # repeat emptying one column four times
          move()                       # enter the next column
          turn_left()                  # turn north
          for i_row in range(3):       # go to the top edge, picking the balls along
              move()
              pick_ball()

          turn_right(); turn_right()   # turn south
          for i_row in range(3):       # go to the bottom edge
              move()

          turn_left()                  # turn east (to the next column)
         
      turn_left()                  # turn west
      turn_left()
      for i_column in range(4):    # come back to the starting square
          move()
         
      for i_ball in range(12):     # drop all the balls
          drop_ball()

Loop tresh
'''''''''''''

.. questionnote::

  Tani, ka 4 topa në secilën nga 6 sheshet, të ngjashme me detyrën e mëparshme. Kareli duhet të sjellë të gjitha 24 topat në sheshin fillestar.

Dallimi i vetëm (krahasuar me detyrën e mëparshme) është se deklarim tani *pick_ball ()* duhet të jetë në një loop shtesë, e treta në thellësi. Gjithashtu, numri i topave që Karel lëshon në kutinë fillestare (në fund të programit) është i ndryshëm. Prandaj, një mënyrë pak më e lehtë për të zgjidhur detyrën është kopjimi i programit të mëparshëm dhe modifikimi i tij.

.. karel:: Karel_for_fetch_24_from_matrix
   :blockly:

   {
      setup:function() {
         var X = 3;
         var Y = 4;
         var world = new World(X, Y);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");

         world.addEWWall(1, 1, 1);
         world.addNSWall(1, 2, Y - 1);
         
         for (var col = 2; col <= X; col++) {
            for (var row = 2; row <= Y; row++) {
               world.putBalls(col, row, 4);
            }
         }
         
         var robot = new Robot();
         
         var code = ["from karel import *",
                     "# Complete the program",
                     ""];
    
         return {robot:robot, world:world, code:code};
      },
    
      isSuccess: function(robot, world) {
         return world.getBalls(1, 1) == 24 &&
            robot.getAvenue() == 1 &&
            robot.getStreet() == 1;
      },
   }

.. reveal:: Karel_for_fetch_24_from_matrix_reveal
   :showtitle: Solution
   :hidetitle: Hide solution

   .. activecode:: Karel_for_fetch_24_from_matrix_solution
      :passivecode: true
      
      from karel import *
      for i_column in range(2):   # repeat emptying one column four times
          move()                      # enter the next column
          turn_left()                 # turn north
          for i_row in range(3):      # go to the top edge, picking the balls along
              move()                   
              for i_ball in range(4): 
                  pick_ball()                  

          turn_right(); turn_right()  # turn south
          for i_row in range(3):      # go to the bottom edge
              move()                   

          turn_left()                 # turn east

      turn_left()                 # turn west
      turn_left()                           
      for i_column in range(2):   # come back to the starting square
          move()

      for i_ball in range(24):    # drop all the balls
          drop_ball()


Ngjitje dhe zbritje
'''''''''''''''''''''''

.. questionnote::

  Kareli duhet të ngjitet në grupin e parë të shkallëve, pastaj të zbresë ato të tjera dhe të përfundojë në këndin e poshtëm të djathtë.

Tani kemi nevojë për dy sythe njëra pas tjetrës (jo të loops). Në lakin e parë, Kareli duhet të ngjitet në shkallën e parë dhe të zbresë shkallën e dytë në loop e dytë. Në secilën loop, Kareli duhet të kryejë 4 veprime që përfaqësojnë një hap lart ose poshtë shkallëve.

.. karel:: Karel_for_stairs_constant
   :blockly:

   {
      setup:function() {

         var Y = 4;
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
                     "turn_left()                  # northwards",
                     "for i_stair in range(3):         # repeat 3 times",
                     "    # tell Karel to climb up one stair",
                     "",
                     "turn_right(); turn_right()   # southwards",
                     "",
                     "# tell Karel to go down the stairs",
                     ""];
    
         return {robot:robot, world:world, code:code};
      },
    
      isSuccess: function(robot, world) {
         return robot.getAvenue() == world.getAvenues() &&
            robot.getStreet() == 1;
      },
   }

.. reveal:: Karel_for_stairs_constant_reveal
   :showtitle: Zgjidhja
   :hidetitle: Fshih zgjidhjen

   .. activecode:: Karel_for_stairs_constant_solution
      :passivecode: true
      
      from karel import *
      turn_left()                # northwards
      for i_stair in range(3):   # repeat 3 times
          move(); turn_right()       # climb up one stair
          move(); turn_left() 

      turn_right(); turn_right() # southwards
      
      for i_stair in range(3):   # repeat 3 times
          move(); turn_left()        # go one stair down
          move(); turn_right() 

Merr topin në shkallë
'''''''''''''''''''''''''''''''

.. questionnote::

  Kareli duhet të përfundojë përsëri në këndin e poshtëm të djathtë, dhe gjatë rrugës ai duhet të marrë të gjitha topat.

Një mënyrë e mirë për të zgjidhur këtë detyrë është të filloni nga zgjidhja e detyrës së mëparshme. Këshillë: kopjoni zgjidhjen e detyrës së mëparshme këtu, dhe pastaj futni sythe për marrjen e topave.

.. karel:: Karel_for_stairs_and_balls_constant
   :blockly:

   {
      setup:function() {

         var Y = 4;
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
         
         // Balls
         for (let y = 2; y <= Y; y++) {
            world.putBalls(y - 1, y, 3);
            world.putBalls(y, y, 4);
         }
         for (let y = 1; y < Y; y++) {
            world.putBalls(X - y, y, 2);
            world.putBalls(X + 1 - y, y, 3);
         }

         var robot = new Robot();
         
         var code = ["from karel import *",
                     "# write a program",
                     ""];
    
         return {robot:robot, world:world, code:code};
      },
    
      isSuccess: function(robot, world) {
         return robot.getBalls() == 36 &&
            robot.getAvenue() == world.getAvenues() &&
            robot.getStreet() == 1;
      },
   }

.. reveal:: Karel_for_stairs_and_balls_constant_reveal
   :showtitle: Zgjidhja
   :hidetitle: Fshih zgjidhjen
   
   .. activecode:: Karel_for_stairs_and_balls_constant_solution
      :passivecode: true
      
      from karel import *
      turn_left()                     # northwards
      for i_stair in range(3):        # repeat 3 times
          move(); turn_right()            # climb up one stair
          for i_ball in range(3):
              pick_ball()
          move(); turn_left() 
          for i_ball in range(4):
              pick_ball()

      turn_right(); turn_right()      # southwards
      
      for i_stair in range(3):        # repeat 3 times
          move(); turn_left()             # go one stair down
          for i_ball in range(2):
              pick_ball()
          move(); turn_right() 
          for i_ball in range(3):
              pick_ball()
