Instruksione shtesë për funksionet
=====================================

Ne përmendëm se ekzistojnë disa mënyra për të shkruar funksione në Python, dhe se funksionet që kemi shkruar dhe përdorur deri më tani kanë formën më të thjeshtë. Funksione të tilla janë, për shembull, *move ()*, *turn_left ()*, *turn_right ()*, *pick_ball ()* dhe *drop_ball ()* nga Biblioteka Karel, si dhe funksionet *back ()*, *take_at_in сосеuese_square ()* dhe *go_to_neighboriz_nonempty_square ()*, të cilat i kemi shkruar vetë. Të gjitha këto funksione kryejnë një punë specifike, gjithmonë në të njëjtën mënyrë.

Funksionet mund të shkruhen në mënyrë që në ekzekutime të ndryshme ata jo gjithmonë të bëjnë të njëjtën gjë saktësisht, por ata kryejnë një detyrë pak më të përgjithshme. Kur i quajmë funksione të tilla, u themi atyre saktësisht se si duam që ata të kryejnë detyrën e tyre. Për shembull, një funksion që do të lëvizte Karel për një numër të caktuar të kutive përpara ose prapa mund të jetë shpesh i dobishëm. Për këtë funksion, ne duam të specifikojmë kërkesën kur e thërrasim atë - sa kuti Karel duhet të lëvizë dhe në cilën anë.

Funksionet me parametra
-------------------------

.. infonote::

    Informacioni shtesë që ne i japim një funksioni shkruhet midis kllapave pas emrit të funksionit në rreshtin e parë të përkufizimit të tij. Midis kllapave mund të specifikojmë një vlerë, ose vlera të shumta të ndara me presje. Këto vlera quhen **arguments** ose **parameters** në një funksion. Fjalët "argumente" dhe "parametra" janë sinonime në programim dhe ne do t'i përdorim ato në mënyrë të barabartë.
    
.. activecode:: Karel_functions__function_with_args_def
    :passivecode: true

    def function_name(parameter1, ... parameterN):
        statement_1
        ...
        statement_k

Funksioni që lëviz Karel numër të caktuar të shesheve përpara ose prapa, mund të emërtohet *go* dhe ai mund të ketë një parametër të plotë. Nëse ky parametër është pozitiv, Karel do të lëvizë atë shumë sheshe përpara, dhe nëse është negativ, Karel do të kthejë një numër korrespondues (të kundërt) të shesheve përsëri. Për shembull, thirrja *go (5)* do të thoshte "shkoni 5 sheshe përpara", ndërsa *go (-2)* do të thoshte "shkoni 2 sheshe mbrapa". Ja se si mund të shkruajmë një funksion të tillë:

.. activecode:: Karel_functions__function_go_def
    :passivecode: true

    def go(n):
        if n > 0:
            for i in range(n):
                move()
        else:
            turn_left();turn_left()
            for i in range(-n):
                move()
            turn_left();turn_left()
 
Ky funksion mund te thjeshtojë shumë programe që supozohet ti tregojnë të lëvizë disa herë një rrugë në disa drejtime. Shembull:

Performoni lëvizje të specifikuara
''''''''''''''''''''''''''''''''''''''

.. questionnote::

    Karel ndodhet në kutinë fillestare të një shtegu me një gjatësi të mjaftueshme, dhe duhet të kryejë zhvendosjet e mëposhtme të topave:

     - 3 topa nga sheshi 3 tek sheshi 4
     - 4 topa nga sheshi 5 në sheshin 1

Në zgjidhjen e kësaj detyre ne do të përdorim funksionin e përshkruar *go*. Për të thjeshtuar më tej zgjidhjen, mund të prezantojmë edhe funksionin *displace*, i cili zhvendos numrin e specifikuar të topave për një numër të caktuar të shesheve përpara ose prapa. Ky përshkrim tregon se funksioni *displace* duhet të ketë dy argumente.

Për ta bërë më të qartë qëllimin e secilit parametër, do t'u japim atyre emra që përshkruajnë rolin e tyre:

.. activecode:: Karel_functions__function_displace_def
    :passivecode: true

    def displace(num_balls, num_squares):
        for i in range(num_balls):
            pick_ball()
        go(num_squares)
        for i in range(num_balls):
            drop_ball()

Funksioni *displace* përdor funksionin e shkruar më parë *go*. Thirrja e një funksioni nga një funksion tjetër si kjo mund të shkojë në thellësi aq sa kemi nevojë. Importantshtë vetëm e rëndësishme që çdo funksion të përcaktohet përpara se të thirret për ekzekutim.

Tani që kemi këto dy funksione në dispozicion, zgjidhja e detyrës fillestare është shumë e lehtë:

.. karel:: Karel_functions__displace_balls
    :blockly:

    {
        setup:function() {
            function random(n) {
                return Math.floor(n * Math.random());
        }
         
        var ww = [
            [
               '███████████',
               '█E.0.4.0.6█',
               '███████████'
            ],
            [
               '█████████████',
               '█E.1.3.0.4.0█',
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
                  world.setRobotStartDirection(c);
               }
               let d = w[wy].charCodeAt(wx);
               if (d >= 48 && d < 58) world.putBalls(x, y, d - 48);
            }
         }
         
            var robot = new Robot();
         
            var code = ["from karel import *",
                     "# replace each word 'pass' with an appropriate function body",
                     "",
                     "def go(n):",
                     "    pass",
                     "",
                     "def displace(num_balls, num_squares):",
                     "    pass",
                     "",
                     "go(2) # to square 3",
                     "displace(3, 1) # displace 3 balls one square forward",
                     "go(1) # to the square 5",
                     "displace(4, -4) # displace 4 balls 4 squares back",
                     ""];
                     
            return {robot:robot, world:world, code:code};
        },
      
        isSuccess: function(robot, world) {
            var X = world.getAvenues();
            if (X == 5) {var tagret_layout = [4,0,1,3,2]}
            if (X == 6) {var tagret_layout = [4,1,0,3,0,0]}
           
            for (let x = 1; x <= X; x++)
                if (world.getBalls(x, 1) != tagret_layout[x-1]) return false;
           
            if (robot.getBalls() > 0)
                return false;
                 
            return true;
        }
    }

Detyra pëer tu ushtruar
------------------------------

Jepet një numër topash
''''''''''''''''''''''''''''

.. questionnote::
   Shkruani funksionin *take_up_to (n)*, i cili i thotë Karelit të marrë maksimumin e *n* topave nga kutia në të cilin qëndron. Më saktësisht, nëse ka *n* ose më shumë topa në kuti, Karel merr *n* prej tyre, dhe nëse ka më pak topa, Karel merr aq sa mundet.
    
     Karel, i cili është në kutinë e parë, duhet të marrë deri në 4 topa nga kutia e dytë, pastaj deri në 2 topa nga kutia e tretë, dhe deri në 3 topa nga sheshi i katërt, dhe pastaj të sjellë të gjitha topat e mbledhur në kutinë e parë. Sigurisht, funksioni *take_up_to (n)*, i shkruar në pjesën e parë të detyrës, duhet të përdoret për këtë qëllim.

.. karel:: Karel_functions__take_balls_up_to
    :blockly:

    {
        setup:function() {
            function random(n) {
                return Math.floor(n * Math.random());
        }
         
        var ww = [
            [
               '███████████',
               '█E.3.4.1.2█',
               '███████████'
            ],
            [
               '█████████',
               '█E.2.5.3█',
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
                  world.setRobotStartDirection(c);
               }
               let d = w[wy].charCodeAt(wx);
               if (d >= 48 && d < 58) world.putBalls(x, y, d - 48);
            }
         }
         
            var robot = new Robot();
         
            var code = ["from karel import *",
                     "def take_up_to(n):",
                     "    pass # write the function",
                     "",
                     "move(); take_up_to(4)",
                     "# complete collecting the balls as specified",
                     "",
                     "turn_left(); turn_left() # come back",
                     "# complete Karel's return to the starting square and the dropping of the balls",
                     ""];
                     
            // from karel import *
            // def take_up_to(n):
            //     for i in range(n):
            //         if is_ball_on_square():
            //             pick_ball()
            // 
            // move(); take_up_to(4)
            // move(); take_up_to(2)
            // move(); take_up_to(3)
            //
            // turn_left(); turn_left()
            // move();move();move()
            // while any_balls_with_karel():
            //     drop_ball()
                     
            return {robot:robot, world:world, code:code};
        },
      
        isSuccess: function(robot, world) {
            var X = world.getAvenues();
            if (X == 5) {var tagret_layout = [6,0,2,0,2]} // = 0,3,4,1,2 - *,4,2,3
            if (X == 4) {var tagret_layout = [7,0,3,0]}   // = 0,2,5,3   - *,4,2,3
           
            for (let x = 1; x <= X; x++)
                if (world.getBalls(x, 1) != tagret_layout[x-1]) return false;
           
            if (robot.getBalls() > 0)
                return false;
                 
            return true;
        }
    }
    

Driving according to instructions
'''''''''''''''''''''''''''''''''''

.. questionnote::
    Jepen funksionet *face_left_at_intersection ()* dhe *go_left (n)*.
    
    - Funksioni *face_left_at_intersection ()* pozicionet Karel për t'u përballur me rrugën e parë që ai haset në anën e majtë. Në ekzekutimin e këtij funksioni, Kareli shkon përpara derisa të hasë në një kuti ku mund të shkojë majtas, por në të vërtetë ai nuk shkon majtas, ai mbetet në kryqëzim në vend të kësaj, kthehet në të majtë. Nëse Karel mund të shkojë majtas para thirrjes së funksionit, ai nuk do të lëvizë nga kutia e tij gjatë ekzekutimit të këtij funksioni, por do të kthehet vetëm në të majtë;
    - Funksioni *go_left (n)* zhvendos Karel një kuti në rrugën *n* në të majtë. Nëse Karel tashmë është në udhëkryq, rruga në të majtë të tij llogaritet si e para;
        
    Shkruaj funksione të ngjashme *face_left_at_intersection ()* dhe *go_right (n)* duke përdorur funksione të dhëna si model.
    
    Shkruaj një program që (duke përdorur funksionet e dhëna dhe të shkruara) e çon Karelin në rrugën e tretë në të majtë, pastaj të dytin në të djathtë dhe në fund, të dytin në të majtë. Kareli duhet të arrijë në fundin e asaj rruge dhe të marrë topin e vetëm në tryezë.

.. karel:: Karel_functions__travel_instructions_1
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }
         
         var ww = [
            [
               '█████████████',
               '█0.0.0█0█1█0█',
               '█████.█.█.█.█',
               '█0.0█0.0.0.0█',
               '███.█.███████',
               '█0█0█0.0.0.0█',
               '█.█.█.█████.█',
               '█E.0.0.0.0.0█',
               '█████████████'
            ],
            [
               '███████████████',
               '█0.0.0.0.0.0█1█',
               '███████.█████.█',
               '█0.0.0.0.0.0█0█',
               '███████.███.█.█',
               '█0.0█0.0.0.0.0█',
               '███.███.███████',
               '█0█0█0.0.0.0█0█',
               '█.█.███.█████.█',
               '█E.0.0.0.0.0.0█',
               '███████████████'
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
                     "def face_left_at_intersection():",
                     "    turn_left()",
                     "    while not front_is_clear():",
                     "        turn_right()",
                     "        move()",
                     "        turn_left()",
                     "    ",
                     "def go_left(n):",
                     "    for i in range(n-1):",
                     "        face_left_at_intersection()",
                     "        turn_right()",
                     "        move()",
                     "    face_left_at_intersection()",
                     "    move()",
                     "",
                     "def face_right_at_intersection():",
                     "    # ...",
                     "    ",
                     "def go_right(n):",
                     "    # ...",
                     "",
                     
                     "go_left(3) # third street to the left",
                     "# second to the right",
                     "# second to the left",
                     "# go until end of the street",
                     "# take the ball",
                     ""];
                     
         //var code = ["from karel import *",
         //            "def face_left_at_intersection():",
         //            "    turn_left()",
         //            "    while not front_is_clear():",
         //            "        turn_right()",
         //            "        move()",
         //            "        turn_left()",
         //            "    ",
         //            "def go_left(n):",
         //            "    for i in range(n-1):",
         //            "        face_left_at_intersection()",
         //            "        turn_right()",
         //            "        move()",
         //            "    face_left_at_intersection()",
         //            "    move()",
         //            "",
         //            "def face_right_at_intersection():",
         //            "    turn_right()",
         //            "    while not front_is_clear():",
         //            "        turn_left()",
         //            "        move()",
         //            "        turn_right()",
         //            "    ",
         //            "def go_right(n):",
         //            "    for i in range(n-1):",
         //            "        face_right_at_intersection()",
         //            "        turn_left()",
         //            "        move()",
         //            "    face_right_at_intersection()",
         //            "    move()",
         //            "",
         //            
         //            "go_left(3)",
         //            "go_right(2)",
         //            "go_left(2)",
         //            "while front_is_clear():",
         //            "    move()",
         //            "if is_ball_on_square():",
         //            "    pick_ball()",
         //            ""];
                     
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return robot.getBalls() > 0;
      }
   }
