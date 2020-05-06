Krijo një grup deklaratash
============================

Le të kujtojmë detyrën *Merrni topin në kutinë fqinje*. Detyra ishte që në çdo drejtim, Kareli duhej të përpiqej të shkonte në kutine fqinje dhe (nëse ai mund të shkonte në kutinë fqinje) të provonte të merrte topin atje. Për ta bërë më të lehtë provimin e drejtimit tjetër, ne zgjodhëm që pas çdo përpjekjeje ta kthenim Karelin në kutinë fillestare.

Një program që zgjidh këtë detyrë është:

.. activecode:: Karel_functions__take_neighboring_ball_1
    :passivecode: true

    from karel import *
    for i in range(4):   # in each of the 4 directions
        if front_is_clear(): # search the square in that direction
            move()
            if is_ball_on_square():
                pick_ball()
            turn_left()          # come back to the starting square
            turn_left()
            move()
            turn_left()          # turn towards the square you just tried
            turn_left()
        turn_left()          # next direction

Pjesa e programit nga rreshti i shtatë në të njëmbëdhjeti duket pak më i ashpër për t’u ndjekur. Në atë pjesë, ju mund të duhet të imagjinoni deklarimet e ekzekutimit të Karel për të kuptuar plotësisht se çfarë po ndodh atje.

Komentet disi ndihmojnë në bërjen më të lehtë të kësaj pjese të programit. Përveç komenteve, do të ishte edhe më mirë nëse do të kishte një funksion *back ()*, i cili do ta lëvizte Karel një hap prapa. Atëherë programi do të ishte më i shkurtër dhe më i kuptueshëm:

.. activecode:: Karel_functions__take_neighboring_ball_2
    :passivecode: true

    from karel import *
    for i in range(4):          # in each of the 4 directions
        if front_is_clear():       # seek a free square in that direction
            move()
            if is_ball_on_square():
                pick_ball()
            back()                     # come back to starting square
        turn_left()                # next direction

Funksioni *back ()* nuk është pjesë e bibliotekës së Karelit, por ne mund ta shkruajmë shumë lehtë këtë funksion vetë. Kur të kemi mbaruar, ne do të jemi në gjendje të përdorim funksionin *back ()* në mënyrë të barabartë me funksionet e tjera të bibliotekës *Karel*, siç janë *move ()* ose *turn_right ()*.

Si të shkruajmë funksione
----------------------------

Për momentin, do te mesojmë menyra të thjeshta për te shkruar një funksion në Python dhe do të shohim me vonë forma të tjera më komplekse.

.. activecode:: Karel_functions__function_def
    :passivecode: true

    def function_name():
        statement_1
        ...
        statement_k

.. infonote::
   
   Kur shkruani ndonjë funksion në Python, fjala ``def`` në fillim, kllapat ``()`` dhe karakteri ``:`` në fund të rreshtit të parë janë të detyrueshme. Për *function_name* ne mund të përdorim çdo emër të shkruar saktë që zgjedhim. deklarimet e mëposhtme janë shkruar me theks, dhe ato formojnë trupin e funksionit (nëse më shumë se një komandë është shkruar me radhë, atëherë këto komanda ndahen me një pikëpresjes ``;`` ). deklarimet në trupin e funksionit do të ekzekutohen sa herë që emri i funksionit haset gjatë ekzekutimit të programit, domethënë kur quhet ky funksion.

Në përputhje me këto rregulla, funksioni *back ()* mund të shkruhet si më poshtë:   

.. activecode:: Karel_functions__backwards_def
    :passivecode: true

    def back():
        turn_left(); turn_left()
        move()
        turn_left(); turn_left()

Programi ka këtë pamje:
   
.. karel:: Karel_functions__take_neighboring_ball_final
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
                     "def back():",
                     "    turn_left(); turn_left()",
                     "    move()",
                     "    turn_left(); turn_left()",
                     "",    
                     "for i in range(4):",
                     "    if front_is_clear():",
                     "        move()",
                     "        if is_ball_on_square():",
                     "            pick_ball()",
                     "        back()",
                     "    turn_left()  # next direction",
                     ""];
                     
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() > 0;
      }
   }

.. infonote::
    Kur nxjerrim disa deklarim (që kanë një kuptim si grup) në një funksion, mund të shkruajmë programe që janë më të shkurtër dhe më të qartë, sepse e kemi zbërthyer problemin në pjesë më pak komplekse.
    
     Një avantazh tjetër i funksioneve të shkrimit është se ne mund t'i përdorim lehtë ato në programe të tjera (këtu, herë pas here do të kopjojmë funksionet e shkruara më parë, por, në programimin real, ekziston një mënyrë më e mirë dhe më e thjeshtë për të ripërdorur funksionet e shkruara dikur).


Nxerrja e funksionit nga loop
-------------------------------------------

.. infonote ::
    
  **Kur duam të ndërpresim një ekzekutim të loop**, shkruajmë një deklarim të veçantë ``break``. Efekti i deklarims *break* është që të dali nga loop dhe të vazhdojë ekzekutimin e programit nga deklarim e parë pas loop.
    
     Duke përdorur një deklarim *break*, ne do të hidhemi nga lidhja më e afërt (më e ngushtë) *for* ose *while* me loop që përmban deklarimn *break*. Nëse një deklarim *break* ndodhet brenda dy ose më shumë lidhjeve loops, ekzekutimi vazhdon me deklarimn që ndjek loop/in më të brendshëm (më të ngushtë).
    
Duke përdorur deklarimn *break*, ne mund të modifikojmë pjesën kryesore të programit:

.. activecode:: Karel_functions__break_intro_1
    :passivecode: true

    for i in range(4):
        if front_is_clear():
            move()
            if is_ball_on_square():
                pick_ball()
            back()
        turn_left()  # next direction

into:

.. activecode:: Karel_functions__break_intro_2
    :passivecode: true

    for i in range(4):
        if front_is_clear():
            move()
            if is_ball_on_square():
                pick_ball()
                break
            back()
        turn_left()  # next direction

Në këtë mënyrë, loop përfundon sa më shpejt që topi të gjendet dhe të merret. Pasi që nuk ka deklarime të tjera pas këtij loop, në këtë rast, duke ekzekutuar deklarimn *break*, funksionimi i programit përfundon.

~~~~

Në mënyrë të ngjashme me daljen nga loop, ne gjithashtu mund të dalim nga funksioni para se të ekzekutohen të gjitha deklarimet e tij.

.. infonote::
    **Kur duam të ndërpresim ekzekutimin e një funksioni**, shkruajmë një deklarim të veçantë `` Return``. Efekti i deklarims *return* është të dalë jashtë funksionit dhe të vazhdojë ekzekutimin e programit nga deklarim e parë pas vendit nga u thirr funksioni.
    
     Me një deklarim *return* hedhim jashtë funksionit pa marrë parasysh sa sythe ka rreth deklarims *return* brenda funksionit.

Ne mund ta kthejmë programin për marrjen e topit në një kuti fqinje në një funksion. Në atë rast, ne mund të shkruanim:

.. activecode:: Karel_functions__return_intro
    :passivecode: true

    def take_at_neighboring_square():
        for i in range(4):
            if front_is_clear():
                move()
                if is_ball_on_square():
                    pick_ball()
                    return # exit the function
                back()
            turn_left()  # next direction
            
    take_at_neighboring_square()
    
Ushtrim
------------------

Lësho tipin për sa kohë që ka topa dhe kuti
'''''''''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Fillimisht, Kareli ka disa topa dhe duhet t'i rregullojë ato përgjatë rrugës një në çdo kuti (duke filluar nga kutis ku ai qëndron) sa më shumë që të jetë e mundur. Kareli ndalon vendosjen e topave kur godet një pengesë ose kur i mbaron topat (çfarëdo që të ndodhë më parë). Nuk ka rëndësi nëse Kareli do të ndalet në kutinë e fundit të mbushur, apo në kutinë e parë bosh.
        
Këshillë: Vendosni njërën nga këto dy kushte në një loop *while*, në mënyrë që loop të përfundojë kur gjendja të mos plotësohet më. Për më tepër, përdorni deklarimn *break* për të dalë nga loop nëse kushti tjetër nuk plotësohet.

.. karel:: Karel_functions__put_balls_until_wall_or_no_more_balls
   :blockly:

    {
        setup:function() {
            function random(n) {
                return Math.floor(n * Math.random());
            }
            var choice = random(3); // need initial world to get rid of 'choice'
            var N = [3, 4, 5];
            var world = new World(N[choice], 1);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            
            var robot = new Robot();
            if (choice == 0) robot.setBalls(3);
            if (choice == 1) robot.setBalls(6);
            if (choice == 2) robot.setBalls(2);
           
            var code = ["from karel import *",
                        " # write the program",
                        ""];
                        
            //var code = ["from karel import *",
            //            "while any_balls_with_karel():",
            //            "    drop_ball()",
            //            "    if not front_is_clear():",
            //            "        break",
            //            "    move()",
            //            ""];
                        
            return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
            var X = world.getAvenues();
            var zeroBallsFound = false;
            for (var x = 1; x <= X; x++) {
                var b = world.getBalls(x, 1);
                if (b > 1) return false;
                if (b == 1 && zeroBallsFound) return false;
                if (b == 0) zeroBallsFound = true;
            }
           
           if (robot.getBalls() > 0 && zeroBallsFound)
               return false;
                 
           return true;
        },
    }

Lëviz të gjithë topat një kuti mbrapa
'''''''''''''''''''''''''''''''''''''''

.. questionnote::

     Ka një rrugë me gjatësi të panjohur para Karelit. Nuk ka topa në kutinë fillestare. Kareli duhet të zhvendosë çdo top një katror në drejtim perëndim.
  
Ju mund ta zgjidhni këtë detyrë duke përsëritur hapat e mëposhtëm për sa kohë që ka kuti para Karel:

- shkoni në kutinë tjetër
- Merrni të gjitha topat nga ajo kuti
- shkoni një hap prapa (domethënë, kthehu dhe shkoni një hap përpara)
- hedhin të gjitha topat
- kthehu në kutinë nga i cili morët topat

Duke vepruar kështu, ju mund të përdorni funksionin e shkruar më parë *back ()* për t'u kthyer në kutinë në të cilin Karel lëviz topat. Thjesht duhet ta kopjoni (ose ri-shkruani atë) në zonën për zgjidhjen tuaj.

.. karel:: Karel_functions__all_balls_one_square_back
   :blockly:

    {
        setup:function() {
           function random(n) {
              return Math.floor(n * Math.random());
           }
           var choice = random(3); // need initial world to get rid of 'choice'
           var N = [3, 4, 5];
           var world = new World(N[choice], 1);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           
           var B = 0;
           if (Math.random() > 0.8) B = random(3);
           if (choice == 0) {
              world.putBalls(2, 1, B);
              world.putBalls(3, 1, B + 2);
           }
           if (choice == 1) {
              world.putBalls(2, 1, B);
              world.putBalls(3, 1, B + 3);
              world.putBalls(4, 1, B + 1);
           }
           if (choice == 2) {
              world.putBalls(2, 1, B);
              world.putBalls(3, 1, B + 2);
              world.putBalls(4, 1, B + 1);
              world.putBalls(5, 1, B + 0);
           }

           var robot = new Robot();

           var code = ["from karel import *",
                       "",
                       "# copy the function 'back()'",
                       "",
                       "while front_is_clear():  # while there are squares in fornt of Karel, repeat",
                       "    move();                  # go forward",
                       "    # complete the line      # pick up all the balls from this square",
                       "    # complete the line      # go one step back",
                       "    # complete the line      # drop all the balls",
                       "    # complete the line      # go forward once more to the emptied square",
                       ""];
                       
           return {robot:robot, world:world, code:code};
        },
    
        isSuccess: function(robot, world) {
           var N = world.getAvenues();
           var B = world.getBalls(1, 1);
           if (N == 3) {
              if (world.getBalls(2, 1) != B + 2)
                return false;              
           }
           if (N == 4) {
              if (world.getBalls(2, 1) != B + 3)
                return false;
              if (world.getBalls(3, 1) != B + 1)
                return false;              
           }
           if (N == 5) {
              if (world.getBalls(2, 1) != B + 2)
                return false;
              if (world.getBalls(3, 1) != B + 1)
                return false;
              if (world.getBalls(4, 1) != B + 0)
                return false;
           }
           
           if (world.getBalls(N, 1) != 0) 
              return false;

           if (robot.getBalls() > 0)
                 return false;
                 
           return true;
        },
    }
   
.. reveal:: Karel_functions__all_balls_one_square_back_reveal
    :showtitle: Solution
    :hidetitle: Hide solution

    .. activecode:: Karel_functions__all_balls_one_square_back_solution
        :passivecode: true
      
        from karel import *
        def back():      # go one step back, and maintain the same orientation
            turn_left(); turn_left();
            move(); 
            turn_left(); turn_left();

        while front_is_clear():       # while there are squares in fornt of Karel, repeat
            move();                       # go to a new square
            while is_ball_on_square():    # take all the balls from this square
                pick_ball()            
            back()                        # step back
            while any_balls_with_karel(): # drop all the balls
                drop_ball()
            move()                        # go to the emptied square


Ndiq topin
''''''''''''''''

.. questionnote::

    Çdo katror përmban një top ose asnjë. Katrorat me topat mbi to formojnë një shteg, i cili fillon në kutinë ngjitur me Karel. Kareli duhet të ndjekë këtë rrugë dhe të marr të gjitha topat.

Këshillë: Për të zgjidhur këtë detyrë, ju mund të shkruani funksionin *go_to_neighboriz_nonempty_square ()*, i cili duhet vetëm të lëvizë Karel në kutinë fqinj, i cili ka një top mbi të (deklarim *return* mund të jetë e dobishme atje). Funksioni *go_to_neighboring_nonempty_square ()* duhet të ndryshojë nga funksioni i shkruar më parë *take_at_ne cîran_square ()* vetëm në kuptimin që nuk e merr topin.

Kur Karel mbledh të gjitha topat, thirrja tjetër e këtij funksioni do ta vendosë atë në një kuti të zbrazët (kjo do të jetë kutia ku Karel mori topin e fundit). Kur nuk ka top në kutinë në të cilin ndodhet Karel, kjo do të thotë që Karel tashmë i ka marrë të gjitha topat.

.. karel:: Karel_functions__follow_the_balls
   :blockly:

    {
        setup:function() {
            function random(n) {
                return Math.floor(n * Math.random());
            }
         
            var ww = [
                [
                   '███████████',
                   '█0.0.1.1.0█',
                   '█.........█',
                   '█0.N.0.1.0█',
                   '█.........█',
                   '█0.1.1.1.0█',
                   '███████████'
                ],
                [
                   '███████████',
                   '█1.1.1.1.1█',
                   '█.........█',
                   '█1.0.0.0.1█',
                   '██........█',
                   '█S.1.1.1.1█',
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
                        "def back():",
                        "    turn_left(); turn_left()",
                        "    move()",
                        "    turn_left(); turn_left()",
                        "",    
                        "def go_to_neighboring_nonempty_square():", 
                        "    # write the function",
                        "",
                        "go_to_neighboring_nonempty_square()",
                        "while ??? # add the condition",
                        "    pick_ball()",
                        "    ??? # complete the program",
                        ""];
                     
            //var code = ["from karel import *",
            //            "def back():",
            //            "    turn_left(); turn_left()",
            //            "    move()",
            //            "    turn_left(); turn_left()",
            //            "",
            //            "def go_to_neighboring_nonempty_square():",
            //            "    for i in range(4):",
            //            "        if front_is_clear():",
            //            "            move()",
            //            "            if is_ball_on_square():",
            //            "                return",
            //            "            back()",
            //            "        turn_left()  # next direction",
            //            "",
            //            "go_to_neighboring_nonempty_square()",
            //            "while is_ball_on_square():",
            //            "    pick_ball()",
            //            "    go_to_neighboring_nonempty_square()",
            //            ""];
            
            return {robot:robot, world:world, code:code};
        },
      
        isSuccess: function(robot, world) {
            var X = world.getAvenues();
            var Y = world.getStreets();
            for (var y = 1; y <= Y; y++)
                for (var x = 1; x <= X; x++)
                    if (world.getBalls(x, y) > 0)
                        return false;
               
            return true;
        },
    }

Merr të gjithe topat nga e gjithë tavolina
'''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

   Karel fillimisht përballet në veri (lart) dhe ai është vendosur në këndin e poshtëm të majtë të një tryeze drejtkëndëshe me madhësi të panjohur, pa mure të brendshme. Mund të ketë ndonjë numër topash në çdo katror. Kareli duhet të marrë të gjitha topat nga të gjitha kutitë në tabelë.
  
Këshillë: Shkruaj një funksion *vac_one_row ()*, i cili e bën Karel:

- kthehu majtas (në lindje), duke kërkuar përgjatë rreshtit në të cilin është
- kaloni nëpër të gjithë rreshtin dhe merrni të gjitha topat nga secila katror në atë rresht, **përfshirë edhe kutinë që ai filloi**
- kthehu në fillim të rreshtit (d.m.th. në perëndim)
- kthehu në fillim të rreshtit dhe kthehu në veri (lart), pasi ai qëndronte para thirrjes së funksionit

Programi që zgjidh detyrën duke përdorur këtë funksion nuk është i gjatë. Duhet të bëjë sa më poshtë:

- zbraz rreshtin e parë
- ndërsa ka rreshta para Karelit, shkoni tek tjetra dhe zbrazini

.. karel:: Karel_functions_take_all_balls_2D
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }

         var sizes = [1, 2, 3, 3, 4, 4, 4];
         var numBalls = [0, 0, 1, 1, 1, 3];
         var X = sizes[random(sizes.length)];
         var Y = sizes[random(sizes.length)];
         var world = new World(X, Y);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(1);
         world.setRobotStartDirection("N");
         
         for (var col = 1; col <= X; col++) {
             for (var row = 1; row <= Y; row++) {
                 let B = numBalls[random(numBalls.length)];
                 world.putBalls(col, row, B);
             }
         }
      
         var robot = new Robot();
         
         var code = ["from karel import *",
                     "# write the program",
                     ""];
        //var code = ["from karel import *
        //            "def empty_one_row():",
        //            "    turn_right()                # turn towards end of the row (eastwards)",
        //            "    while is_ball_on_square():  # empty first square in the row",
        //            "        pick_ball()",
        //            "    while front_is_clear():     # while there are unvisited squares",
        //            "        move()                      # go to a new square",
        //            "        while is_ball_on_square():  # emtpy the new square",
        //            "            pick_ball()",
        //            "        ",
        //            "    turn_right(); turn_right()  # turn towards beginning of the row (westwards)",
        //            "    while front_is_clear():     # come back to the first square in that row",
        //            "        move()",
        //            "    turn_right()                # turn towards next row (northwards)",
        //            "",
        //            "empty_one_row()             # pick up the balls from the first row",
        //            "while front_is_clear():     # while there are new rows",
        //            "    move(); empty_one_row()     # go to the next row and empty it",
        //            ""];

         return {robot:robot, world:world, code:code};
        },

        isSuccess: function(robot, world) {
           var X = world.getAvenues();
           var Y = world.getStreets();
           for (var col = 1; col <= X; col++) {
              for (var row = 1; row <= Y; row++) {
                 if (world.getBalls(col, row) > 0)   
                    return false;
              }
           }
                 
           return true;
      },
   }
