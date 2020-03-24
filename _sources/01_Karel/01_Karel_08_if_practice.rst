*if*  - Praktikë
===========================

Në këtët seksion do të praktikojmë vëtëm përdorimin e deklarims *if* dhe kombinimin me loops.

Ushtrime
------------------

Shko në fund të rrugës dhe merr vetëm një top
''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Kareli duhet të arrijë në fund të korridorit, dhe të marrë vetëm topin e parë në rrugë. Kutia fillestarenuk ka asnjë top mbi të, dhe Karel fillimisht nuk mban topa.
   
.. karel:: Karel_if__take_first_ball_only
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }
         
         var ww = [
            [
               '█████████████',
               '█E.0.1.0.3.0█',
               '█████████████'
            ],
            [
               '█████████',
               '█E.0.2.2█',
               '█████████'
            ],
            [
               '███████',
               '█E.1.0█',
               '███████'
            ]
         ];
         let choice = random(ww.length);
         var w = ww[choice];
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
                     "# write the program",
                     ""];
                     
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() > 0;
      }
   }

.. reveal:: Karel_if__take_first_ball_only_reveal
    :showtitle: Hint
    :hidetitle: Hide hint
    
    Ne kemi filluar një zgjidhje këtu. Ju pritet të plotësoni deklarimet *if* me kushte të përshtatshme.
    
     Karel duhet të marrë topin vetëm nëse plotësohen dy kushte:
    
     - kushti i parë është ai që ne kontrollojmë sa herë që Karel përpiqet të marrë topin (pa këtë kusht programi mund të përfundojë për shkak të një operacioni të pakalueshëm).
     - kushti i dytë është i imponuar nga kërkesat e kësaj detyre, që është se Karel merr topin vetëm nëse ai nuk e ka marrë një më parë.
    
     Rendi i kontrollit të këtyre dy kushteve nuk është i rëndësishëm, pasi që të dy duhet të përmbushen në mënyrë që të marrin topin sidoqoftë.
    .. activecode:: Karel_if__take_first_ball_only_solution
        :passivecode: true
      
        from karel import *
        while front_is_clear():  # while there are squares in front of Karel
            move()                    
            if ???
                if ???
                    pick_ball()

Dërgo topin në kutinë ngjitur
'''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Ka vetëm një top në tabelë. Karel dhe topi janë të vendosura në dy shekutishe ngjitur pa mur ndërmjet tyre (Karel është vetëm një hap hap nga topi, nëse ai kthehet në top para). Mund të jetë ose nuk mund të ketë një mur midis kutive të tjera. Kareli duhet të marrë topin dhe ai mund të përfundojë në çdo kuti në fund.

   Si zakonisht, drejtojeni programin disa herë për ta provuar atë në shembuj të ndryshëm.

Një ide e mundshme është që në secilën nga katër drejtimet, ne përpiqemi ta bëjmë Karel të shkojë një hap përpara dhe të marr topin. Skenarë të ndryshëm mund të ndodhin në secilën nga katër përpjekjet:

- është e mundur që nuk ka kuti para Karel në atë drejtim
- është e mundur që të ketë një kuti para Karelit, por nuk ka topa mbi të
- është e mundur që ka një kuti dhe se ka një top në të


Kur provoni drejtimin tjetër, është shumë më e thjeshtë nëse nuk duhet të marrim parasysh nëse Karel ka gjetur një kuti pa top në drejtimin e mëparshëm që ai provoi, ose nuk e gjeti fare një kuti. Për të thjeshtuar përpjekjen tjetër, është e përshtatshme për ne që Karel të përfundojë përpjekjen e mëparshme kur ai ishte në një kuti të zbrazët në të njëjtin gjëndje si kur nuk kishte kuti. Kur nuk ka kuti në drejtim të përpjekjes, Karel do të mbetet në kutinë fillestare, përballë drejtimit të tentuar. Për të lehtësuar vazhdimin e kërkimit, ne mund të lëmë Karel në të njëjt[n kuti përballë të njëjtit drejtim kur ai të kthehet nga një kuti e zbrazët ngjitur. Në fakt, nuk do të dëmtojë nëse e bëjmë edhe kur Karel merr topin (është e mundur që Karel pa nevojë të vazhdojë të kërkojë, por kjo nuk do të shkaktojë gabime).
Për shkak se e kemi sjellë Karelin në të njëjtin gjëndje (pozicion dhe orientim) pas secilit prej tre rasteve më lart, ne e dimë saktësisht gjendjen tonë fillestare, për secilën përpjekje pasuese. Pas secilit drejtim të përpjekjes, ne vetëm duhet ta kthejmë Karel drejt drejtimit tjetër, ne do të përpiqemi të gjejmë topin në (ose në të majtë ose në të djathtë).

.. karel:: Karel_if__take_neighboring_ball
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }
         
         var ww = [
            [
               '█████',
               '█0.0█',
               '███.█',
               '█1.N█',
               '███.█',
               '█0.0█',
               '█████'
            ],
            [
               '█████',
               '█1.0█',
               '█...█',
               '█E.0█',
               '█████'
            ],
            [
               '███████',
               '█0█0█0█',
               '█.█.█.█',
               '█0.W.0█',
               '█.█.█.█',
               '█0█1█0█',
               '███████'
            ]
         ];
         let choice = random(ww.length);
         var w = ww[choice];
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
                     "for i in range(4):",
                     "    if front_is_clear():",
                     "        move()",
                     "        # tell Karel to try to take the ball",
                     "        # tell Karel to go back to the starting square...",
                     "        # ... and turn towards the square at which he just tried",
                     "        # (as if he had not gone to that square at all)",
                     "    # tell Karel to prepare for the next attempt",
                     ""];
                     
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() > 0;
      }
   }

.. commented out
   .. reveal:: Karel_if__take_neighboring_ball_reveal
       :showtitle: Solution
       :hidetitle: Hide solution
       
       Solution can look like this:
       
       .. activecode:: Karel_if__take_neighboring_ball_solution
           :passivecode: true
         
           from karel import *
           for i in range(4):          # in each of the 4 directions
               if front_is_clear():        # look for a square in that direction
                   move()                    
                   if is_ball_on_square():
                       pick_ball()
                   turn_left()                 # go back to starting square
                   turn_left()
                   move()
                   turn_left()                 # face the square you just tried
                   turn_left()
               turn_left()                 # next direction

Ndiq rrugën
'''''''''''''''

.. questionnote::

  Ka vetëm një top në tryezë, dhe Karel duhet ta marrë atë. Rruga për në top nuk është e drejtë, por nuk ka kryqëzime (gjithmonë ekziston vetëm një mënyrë për të vazhduar lëvizjen, edhe nga kutia fillestare).
  
.. karel:: Karel_if__take_ball_no_branches
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }
         
         var ww = [
            [
               '███████████',
               '█N█0.0.0.0█',
               '█.█.█████.█',
               '█0█0█0.1█0█',
               '█.█.█.███.█',
               '█0.0█0.0.0█',
               '███████████'
            ],
            [
               '█████████',
               '█0.0.0.0█',
               '█.█████.█',
               '█0█0.0.0█',
               '█.█.█████',
               '█0█E█0.0█',
               '█.███.█.█',
               '█0.0.0█1█',
               '█████████'
            ],
            [
               '█████████████',
               '█W.0.0█0.0.0█',
               '█████.█.███.█',
               '█0.0.0█0█0.0█',
               '█.█████.█.███',
               '█0.0.0.0█0.1█',
               '█████████████'
            ],
            [
               '███████████',
               '█0.0█0.0█S█',
               '█.█.█.█.█.█',
               '█0█0.0█0.0█',
               '█.█████████',
               '█0█0.0█0.0█',
               '█.█.█.█.█.█',
               '█0.0█0.0█1█',
               '███████████'
            ]
         ];
         let choice = random(ww.length);
         var w = ww[choice];
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
                     "... # write the program",
                     ""];
                     
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() > 0;
      }
   }

.. reveal:: Karel_if__take_ball_no_branches_reveal
    :showtitle: Ndihma
    :hidetitle: Fshih ndihmën
    
    Ne japim intruksione për një zgjidhje të mundshme:

    .. activecode:: Karel_if__take_ball_no_branches_solution
        :passivecode: true
      
        # First, turn towards the (only) free square
        
        while you can't move forward: 
            turn left
            
        while you can go forward:
            move forward
            if there is no free square in front of you: # if there is no straight path
                turn left
                if there is no free square in front of you: # if no path to the left either
                    turn right twice
        
        take the ball

.. commented out
   .. reveal:: Karel_if__take_ball_no_branches_reveal
       :showtitle: Solution
       :hidetitle: Hide solution
       
       One possible solution is:
   
       .. activecode:: Karel_if__take_ball_no_branches_solution
           :passivecode: true
         
           from karel import *
           while not front_is_clear(): # turn towards the (only) free square
               turn_left()
               
           while front_is_clear():
               move()
               
               # turn towards the next free square
               if not front_is_clear():   # if there is no straight path,
                   turn_left()                # try left
               if not front_is_clear():   # if there is no path to the left
                   turn_right(); turn_right() # try right
           
           if is_ball_on_square():
               pick_ball()

Devijim
'''''''''

.. questionnote::

  Ka vetëm një top në tryezë dhe Karel duhet ta marrë atë. Për të arritur në top, Kareli duhet të shkojë drejt, vetëm kur ai nuk mund të kthehet majtas ose djathtas (nuk do të ketë një udhëkryq të paqartë ku ka një shteg në të majtë dhe të djathtë).
  
.. karel:: Karel_if__p1_left_p2_right_p3_forward
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }
         
         var ww = [
            [
               '███████████',
               '█1.0█0.0.0█',
               '███.█.█████',
               '█0.0.0█0.0█',
               '█████.███.█',
               '█S.0.0.0.0█',
               '███████████'
            ],
            [
               '███████████',
               '█0.0.0█0.0█',
               '█████.█.███',
               '█0.0.0█0.0█',
               '█.█.█.█.█.█',
               '█0█0█E█0█1█',
               '█.█.███.███',
               '█0█0.0.0.0█',
               '███████████'
            ],
            [
               '█████████████',
               '█E.0.0█0.0.0█',
               '███.█.█.█████',
               '█0.0█0█0.0.0█',
               '█.█.███.███.█',
               '█0█0█0.0.0█0█',
               '█.███.█████.█',
               '█0.0.0.0.0█1█',
               '█████████████'
            ],
            [
               '█████████',
               '█0.0.0█S█',
               '█.█████.█',
               '█0.0.0.0█',
               '███.███.█',
               '█0█0.0█0█',
               '█.█.█.███',
               '█0.0█0.1█',
               '█████████'
            ]
         ];
         let choice = random(ww.length);
         var w = ww[choice];
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
                     "... # write the program",
                     ""];
                     
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() > 0;
      }
   }
   
.. reveal:: Karel_if__p1_left_p2_right_p3_forward_reveal
    :showtitle: Ndihma
    :hidetitle: FSHIH NDIHMËN

    Instruksione për një zgjidhje të mundshme:
    
    .. activecode:: Karel_if__p1_left_p2_right_p3_forward_solution
        :passivecode: true
      
        # turn towards the only free square
        
        while you can move forward:
            move forward
            # try going left (turn left and try going forward)
            # if you can't go left:
                # try going right
                # if you can't go right either
                    # prepare to try going straight in the next iteration
        
        take the ball

.. commented out
    .. reveal:: Karel_if__p1_left_p2_right_p3_forward_reveal
        :showtitle: Solution
        :hidetitle: Hide solution

        .. activecode:: Karel_if__p1_left_p2_right_p3_forward_solution
            :passivecode: true
          
            from karel import *
            for i in range(3):        # turn towards the only fre square
                if not front_is_clear():
                    turn_left()
            
            while front_is_clear():
                move()
                turn_left()                # try going left
                if not front_is_clear():   # if you can't go left
                    turn_right(); turn_right()     # try going right
                if not front_is_clear():   # if you can't go right either
                    turn_left() # prepare to try going straight in the next iteration
            
            pick_ball()

Shko majtas sa herë të mundesh
''''''''''''''''''''''''

.. questionnote::

  Ka vetëm një top në tryezë dhe Karel duhet ta marrë atë. Karel do ta arrijë gjithmonë topin duke u kthyer majtas kur të mundet, dhe të shkojë drejt, kur ai nuk mund të shkojë majtas (kur ai nuk mund të shkojë ose majtas ose drejt, kjo do të thotë se ai ka arritur). Karel fillimisht është kthyer ashtu siç duhet, dhe hapi i tij i parë është gjithmonë drejt përpara.

.. karel:: Karel_if_p1_left_p2_forward
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }
         
         var ww = [
            [
               '█████████████',
               '█0.0.0.0.0.0█',
               '█.███████.█.█',
               '█0.0.0.1█0█0█',
               '█████.███...█',
               '█0.0.0.0█0.0█',
               '█████████.███',
               '█E.0.0.0.0.0█',
               '█████████████'
            ],
            [
               '█████████████',
               '█0.0.0.0.0█0█',
               '█..██████.█.█',
               '█0.0█0.0.0█0█',
               '█████..██.█.█',
               '█0.0.0.1█0█0█',
               '█████████..██',
               '█E.0.0.0.0.0█',
               '█████████████'
            ],
            [
               '█████████████',
               '█0.0.0.0.0█0█',
               '█.█.........█',
               '█0█0.0.0.0.0█',
               '█.█.███████.█',
               '█0█0.0.1█0█0█',
               '█.█.█████.█.█',
               '█0.0.0.0.0█N█',
               '█████████████'
            ],
            [
               '█████████████',
               '█S█0.0.0.0█0█',
               '█.███.███...█',
               '█0█0.1█0█..0█',
               '█.███████.█.█',
               '█0.0.0.0.0█0█',
               '█.███████████',
               '█0.0.0.0.0.0█',
               '█████████████'
            ]
         ];
         let choice = random(ww.length);
         var w = ww[choice];
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
                     "... # write the program",
                     ""];
                     
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() > 0;
      }
   }

.. reveal:: Karel_if_p1_left_p2_forward_reveal
    :showtitle: Ndihma
    :hidetitle: Fshih ndihmën

     Instruksione për nje zgjidhje të mundshme:
    
    .. activecode:: Karel_if_p1_left_p2_forward_solution
        :passivecode: true
      
        while you can go forward:
            move forward
            # if there is no path to the left
                # stay turned straight

        take the ball

.. commented out
    .. reveal:: Karel_if_p1_left_p2_forward_reveal
        :showtitle: Solution
        :hidetitle: Hide solution

        .. activecode:: Karel_if_p1_left_p2_forward_solution
            :passivecode: true
          
            from karel import *
            while front_is_clear():
                move()
                turn_left()
                if not front_is_clear():
                    turn_right()

            if is_ball_on_square():
                pick_ball()
