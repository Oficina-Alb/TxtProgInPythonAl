Kombinimi i loops
===============

Ne kemi parë që në trupin e një deklarate *for*, ne mund të vendosim disa deklarime të ndryshme. Ngjashëm me deklarimn *for*, në fjalinë ``while`` ne gjithashtu (përveç komandave të tjera) mund të vendosim një deklarim të re të loop, dhe ajo mund të jetë ose një *loop* ose një loop *for*. Në atë mënyrë, ne mund të ndërtojmë kombinime të ndryshme të sytheve të futura.

Kur të dy sytloophe futen në njëra-tjetrën, ne i quajmë ato një loop të dyfishtë, ndërsa tre loop quhen një loop i trefishtë. Në mënyrë të ngjashme, ne mund të fole çdo numër loop/esh në njëri-tjetrin, thjesht rrallë kemi nevojë për një numër të madh të sythe të foleve.

Në këtë mësim do të praktikojmë shkrime të kombinimeve të sytheve *while* dhe *for*.

Rrathë të ndryshëm të dyfishtë dhe të shumëfishtë - detyra
-----------------------------------------

Merrni 4 topa në çdo katror deri në fund të një rreshti
''''''''''''''''''''''''''''''''''''''''''''''''''


.. questionnote ::

  Ka një ose më shumë sheshe përpara Karelit, dhe në secilën nga këto sheshe ka katër topa (nuk ka topa në sheshin fillestar). Kareli duhet t'i marrë të gjitha.

Tani, derisa të arrijë në mur, Kareli duhet të përsërisë duke ecur përpara dhe të marrë 4 topa. Provoni të plotësoni programin.

Kujtoni, si në shembujt e mëparshëm të sytheve loops, pohimi në trupin e lakit të brendshëm (këtu do të jetë ``pick_ball ()``) duhet të indentifikohet më tej.

.. karel:: Karel_while__many_squares_four_bals_per_square
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var N = 2 + random(9);
         var world = new World(N, 1);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");
         for (var k = 2; k <= N; k++)
             world.putBalls(k, 1, 4);
      
         var robot = new Robot();
      
         var code = ["from karel import *",
                     "while front_is_clear():",
                     "    move()",
                     "    # add missing statements",
                     ""];
                     //from karel import *
                     //while front_is_clear():
                     //    move()
                     //    for i in range(4):
                     //        pick_ball()
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         var N = world.getAvenues();
         for (var k = 1; k <= N; k++)
            if (world.getBalls(k, 1) > 0)
               return false;
               
         return true;
      }
   }
   
..  commented out
    .. reveal:: Karel_while__many_squares_four_bals_per_square_reveal
       :showtitle: Solution
       :hidetitle: Hide solution
    
       .. activecode:: Karel_while__many_squares_two_bals_per_square_solution
          :passivecode: true
          
          from karel import *
          while front_is_clear():
              move()
              for i in range(4):
                  pick_ball()
   
   
Kapni topat
'''''''''''''''''''''

.. questionnote::

  Ka të paktën një kuti para Karelit, dhe mund të ketë ndonjë numër prej tyre. Në secilën nga katrorët **përballë** Karel ka zero ose më shumë topa (kutia fillestare është bosh). Karel duhet të marr të gjitha topat.

Kjo detyrë është përgjithësimi i një të mëparshmi, kështu që programi që zgjidh këtë detyrë mund të përdoret edhe në atë paraprak. Dallimi është se tani lak i brendshëm duhet të jetë një loop *while*, ndërsa në detyrën e mëparshme mund të ketë qenë një loop *for* gjithashtu.

Përsëri, thënia ``pick_ball ()`` duhet të përfshihet më tej. Në këtë mënyrë, ajo do të përsëritet ndërsa gjendja e brendshme *while* mban deklarim, d.m.th., ndërsa ekziston një top në shesh Karel është në atë moment. Marrja e të gjitha topave, së bashku me fjalinë ``move`` përsëritet në lakin e jashtëm ``ndërsa`` për aq kohë sa ka sheshe para Karelit. Efekti i përgjithshëm i sytheve loops është se të gjitha topat nga çdo katror do të merren.

.. karel:: Karel_while__many_squares_many_balls
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var N = 2 + random(9);
         var world = new World(N, 1);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");
         
         for (var k = 2; k <= N; k++) {
            let B = random(7);
            world.putBalls(k, 1, B);
         }
      
         var robot = new Robot();
      
         var code = ["from karel import *",
                     "while front_is_clear():",
                     "    # go forward",
                     "    while ... # finish the program",
                     ""];
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         var N = world.getAvenues();
         for (var k = 1; k <= N; k++)
            if (world.getBalls(k, 1) > 0)
               return false;
               
         return true;
      }
   }

Sillni topat
'''''''''''''''''''

.. questionnote::

  Ka një shteg me gjatësi të panjohur para Karelit. Kareli duhet të mbledhë të gjitha topat nga të gjitha kutitë dhe t'i sjellë ato në sheshin fillestar.

Programi është ndarë në pjesë më të vogla nga komentet. Shtoni deklarim që mungojnë.

.. karel:: Karel_while__bring_all_balls
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var N = 2 + random(9);
         var world = new World(N, 1);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("E");
         
         for (var k = 1; k <= N; k++) {
            let B = random(7);
            world.putBalls(k, 1, B);
         }
      
         var robot = new Robot();
         
         var code = ["from karel import *",
                     "# use double loop to take all balls from all squares",
                     "",
                     "",
                     "turn_left(); turn_left()                # turn back",
                     "# tell Karel to go back to the starting square ",
                     "# (that is, to move forward while he can)",
                     "",
                     "while any_balls_with_karel():",
                     "    # drop one ball",
                     ""];

           return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           var N = world.getAvenues();
           for (var k = 2; k <= N; k++)
              if (world.getBalls(k, 1) > 0)
                 return false;
               
           if (robot.getBalls() > 0)
                 return false;
                 
           return true;
        },
   }

..  commented out
    .. reveal:: Karel_while__bring_all_balls_reveal
       :showtitle: Solution
       :hidetitle: Hide solution

       .. activecode:: Karel_while__bring_all_balls_solution
          :passivecode: true
          
          from karel import *
          while front_is_clear():          # bring all balls from all squares
              move()
              while is_ball_on_square():
                  pick_ball()
                
          turn_left(); turn_left()         # turn back
          
          while front_is_clear():          # go back to the starting square
              move()
              
          while any_balls_with_karel():    # drop all the balls
              drop_ball()


Lart dhe poshtë
'''''''''''

.. questionnote::

  Karel është në një tabelë drejtkëndëshe me madhësi të panjohur (numri i kolonave është gjithmonë i çuditshëm), pa asnjë top në kuti. Qëllimi është që Karel të arrijë në kutinë e djathtë të poshtëm. Për ta arritur këtë, Kareli do të duhet të lëvizë nëpër kolonat në mënyrë alternative lart e poshtë.

Këto janë disa nga pamjet e mundshme të labirintit:

   .. image:: ../../_images/Karel/While_UpDown.jpg
      :width: 600px   
      :align: center

.. karel:: Karel_while__up_col_down_col
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var X2 = 1 + random(4);
         var Y = 2 + random(5);
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
                     "# add the missing statements",
                     ""];
                     //from karel import *
                     //while front_is_clear():        # while you are not in the bottom right corner
                     //    move(); turn_left()            # enter the next column and turn north
                     //    while front_is_clear():        # go to the top edge
                     //        move()
                     //
                     //    turn_right(); move(); turn_right() # move to the next column and turn south
                     //    while front_is_clear():        # go to the bottom edge
                     //        move()
                     //
                     //    turn_left()                    # turn east
    
         return {robot:robot, world:world, code:code};
      },
    
      isSuccess: function(robot, world) {
         return robot.getAvenue() == world.getAvenues() &&
            robot.getStreet() == 1;
      },
   }

.. reveal:: Karel_while__up_col_down_col_reveal
   :showtitle: Hint
   :hidetitle: Hide hint

   .. activecode:: Karel_while__up_col_down_col_solution
      :passivecode: true
      
      from karel import *
      while front_is_clear(): # while you are not in the bottom right corner
          move(); turn_left()     # enter the next column and turn north
          ... # finish this part  # go to the top edge

          turn_right(); move()    # move to the next column
          turn_right()            # turn south
          ... # finish this part  # go to the bottom edge

          turn_left()             # turn east

Shkallë
''''''

.. questionnote::

  Kareli duhet të ngjitet në shkallët e para, pastaj të zbresë ato të tjera dhe të përfundojë në këndin e poshtëm të djathtë. Madhësia e tabelës nuk dihet, por numri i kolonave gjithmonë do të jetë i rastësishëm. Tabela mund të duket si kjo:
  
   .. image:: ../../_images/Karel/While_Stairs.jpg
      :width: 600px   
      :align: center

.. karel:: Karel_while__stairs
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var Y = 2 + random(6);
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
                     "# add missing statements",
                     ""];
                     //from karel import *
                     //turn_left()                       # northwards
                     //while front_is_clear():           # while there are stairs up
                     //    move(); turn_right(); move(); turn_left() #    climb up one stair
                     //
                     //turn_right(); turn_right()        # southwards
                     //
                     //while front_is_clear():           # while there are srairs down
                     //    move(); turn_left(); move(); turn_right() #    come down one stair 
    
         return {robot:robot, world:world, code:code};
      },
    
      isSuccess: function(robot, world) {
         return robot.getAvenue() == world.getAvenues() &&
            robot.getStreet() == 1;
      },
   }

.. reveal:: Karel_while__stairs_reveal
   :showtitle: Hint
   :hidetitle: Hide hint

   .. activecode:: Karel_while__stairs_solution
      :passivecode: true
      
      from karel import *
      turn_left()                        # northwards
      while front_is_clear():            # while there are stairs up
          move(); turn_right(); move(); turn_left() # climb up one stair

      turn_right(); turn_right()         # southwards
      
      while ... # add the condition      # while there are srairs down
          ... # add 4 statements             # come down one stair


Spirale në të majtë
''''''''''''''''''

.. questionnote::

  Në të gjitha rastet e shfaqura, Kareli duhet të vijë në një kuti të shënuar me një rreth të kuq (nuk ka topa në këtë detyrë).
   
   .. image:: ../../_images/Karel/While_SpiralLeft.jpg
      :width: 600px   
      :align: center


.. karel:: Karel_while__spiral_left
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

      var N = 1 + random(7);
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
                  "# finish the incomplete statements",
                  "while front_is_clear():",
                  "    while ... ",
                  "        ... ",
                  "    turn_left()",
                  ""];

        return {robot:robot, world:world, code:code};
     },
 
     isSuccess: function(robot, world) {
        var N = world.getAvenues();
        return robot.getStreet() === Math.floor((N+2)/2) &&
           robot.getAvenue() === Math.floor((N+1)/2);
     },
   }

.. reveal:: Karel_while__spiral_left_reveal
   :showtitle: Solution
   :hidetitle: Hide solution

   .. activecode:: Karel_while__spiral_left_solution
      :passivecode: true
      
      from karel import *
      while front_is_clear():
          while front_is_clear():
              move()
          turn_left()

