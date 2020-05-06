Kontrolloni dhe vendosni
==========================

Deklarimi *while* doli shumë e dobishme, sepse duke e përdorur atë ne ishim në gjendje të zgjidhnim detyra më të larmishme. Sidoqoftë, shembulli i mëposhtëm tregon se ka detyra të thjeshta që nuk mund t'i zgjidhim me ato që kemi mësuar deri më tani.

Le të themi se në disa situata ju duhet të lëvizni Karel vetëm për një katror nëse është e mundur (nëse nuk është e mundur, Kareli duhet të mbetet aty ku është).

- Nëse shkruajmë vetëm komandën *move ()*, ne po rrezikojmë një mesazh gabimi në rast se Karel është para murit.
- Nëse vendosim komandën *move ()* nën deklarimn *while front_is_clear ():*, rrezikojmë që Karel të shkojë më tej sesa donim.
- Nëse nuk e përdorim komandën *move ()*, rrezikojmë të mos lëvizim edhe nëse është e mundur (dhe e domosdoshme).

Natyrisht, ne kemi nevojë për një deklarim të re, e cila do t'i tregojë Karelit "nëse mund të shkoni përpara, lëvizni një vend".

*If*
--------------

Deklarimi që na nevojitet në rastin e përshkruar është pohimi ``if``, i cili gjithashtu ekziston në pothuajse të gjitha gjuhët e programimit. Në Python, ajo (në formën e saj më të thjeshtë) është shkruar si kjo:

.. activecode:: Karel_if__syntax
   :passivecode: true

   if condition:
       statement_1
       ...
       statement_k


.. infonote::

   Ne shohim që shkrimi i deklarims ``if`` është shumë i ngjashëm me shkrimin e një deklarate *while*. Nën deklarimn ``if`` mund të vendosim edhe një ose më shumë deklarime të tjera, të cilat përbëjnë trupin **e deklarims if**. Të njëjtat rregulla vlejnë për shkrimin e ``:`` pas kushtit dhe për deklarimet e indentifikimit që ekzekutohen nëse plotësohet kushti. Dallimi është se deklarimet në trupin e një deklarate *if* nuk do të përsëriten - nëse plotësohet kushti, ato do të bëhen vetëm një herë.

    Deklarimi ``if`` nganjëherë quhet deklarim *branching statement* sepse rrjedhja e ekzekutimit të programit degëzohet në këtë stendë: deklarim tjetër që duhet të ekzekutohet varet nga përgjigja e pyetjes nga gjendja.

Në shembullin e mësipërm, duhet të shkruajmë:

.. activecode:: Karel_if__example
   :passivecode: true

   if front_is_clear():
       move()


Le të shohim disa detyra në të cilat (përveç deklaratave tashmë të njohura) përdoret deklarim ``if``.

Merr një top, nëse ka
'''''''''''''''''''''''''''''''

.. questionnote::

   Ka një kuti përpara Karelit, me zero ose më shumë topa. Shkruaj një program që i thotë Karelit të lëvizë në atë kuti, dhe pastaj të marrësh saktësisht një top nëse ka të paktën një top në fushë.
   
    Drejtoni programin disa herë për ta provuar atë në shembuj të ndryshëm.

Në rastin tonë, kushti do të jetë ``is_ball_on_square ()``, dhe komanda që ekzekutohet me kusht është ``pick_ball ()``.

.. karel:: Karel_if__take_one_if_any
   :blockly:

   {
      setup:function() {
          var world = new World(2, 1);
          world.setRobotStartAvenue(1);
          world.setRobotStartStreet(1);
          world.setRobotStartDirection("E");
          if (Math.random() > 0.5)
             world.putBalls(2, 1, 1 + Math.floor(7 *  Math.random()));
      
      var robot = new Robot();
      
      var code = ["from karel import *",
                  "move()",
                  "if ...         # complete the statement",
                  "    pick_ball()",
                  ""];
          return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         return world.getBalls(1, 1) === 0 &&
            (robot.getBalls() === 1 ||
            (robot.getBalls() === 0 && world.getBalls(2, 1) === 0));
      }
   }

.. commented out
   .. reveal:: Karel_if__take_one_if_any_reveal
       :showtitle: Zgjidhja
       :hidetitle: Fshih zgjidhjen
   
       .. activecode:: Karel_if__take_one_if_any_solution
           :passivecode: true
         
           from karel import *
           move()
           if is_ball_on_square():
               pick_ball()


Shko në fund te rrugës dhe merr një top nëse është e mundur
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

.. questionnote::

  Ka të paktën një shesh para Karelit, dhe mund të ketë ndonjë numër prej tyre. Çdo katror ka zero ose më shumë topa. Kareli duhet të marr saktësisht një top nga secili katror në të cilin ka një top.
  
   Drejtoni programin disa herë për ta provuar atë në shembuj të ndryshëm.

Këtu është e nevojshme të përdorni deklarimn *while* për avancimin përpara, dhe në trupin e loop *wile*, pas çdo hapi përpara, duhet të përdoret një deklarim *if* për të kontrolluar nëse Karel qëndron në një kuti me një top në ajo apo jo.

.. karel:: Karel_if__many_squares_take_one_if_any
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
             if (Math.random() > 0.5)
                world.putBalls(k, 1, 2 + random(3)); // need initial world to replace '2'->'1'
      
         var robot = new Robot();
      
         var code = ["from karel import *",
                     "while front_is_clear():",
                     "    move()",
                     "    if ... # add the condition",
                     "       ... # add the conditional statement",
                     ""];
                     
         return {robot:robot, world:world, code:code};
      },
      
      isSuccess: function(robot, world) {
         var N = world.getAvenues();
         var nonEmpty = 0;
         for (var k = 1; k <= N; k++)
            if (world.getBalls(k, 1) > 0)
               nonEmpty++;
               
         return robot.getBalls() === nonEmpty;
      }
   }

.. commented out
   .. reveal:: Karel_if__many_squares_take_one_if_any_reveal
       :showtitle: Solution
       :hidetitle: Hide solution
       
       Solution:
   
       .. activecode:: Karel_if__many_squares_take_one_if_any_solution
           :passivecode: true
         
           from karel import *
           while front_is_clear():
               move()
               if is_ball_on_square():
                   pick_ball()


Nëse nuk bën këtë, bëj atë (if-else)
---------------------------------------

Në disa detyra, një gjë duhet të bëhet nëse plotësohet një kusht i caktuar, dhe diçka tjetër nëse nuk përmbushet. Në këtë rast, ne mund të përdorim formën e zgjeruar të një deklarate *if*, e cila duket si kjo:

.. activecode:: Karel_if__else_syntax
    :passivecode: true

    if condition:
        statement_a1
        ...
        statement_ak
    else:
        statement_b1
        ...
        statement_bm


.. infonote::

   Në formën e zgjeruar të fjalisë ``if``, pjesa e parë (deri tek fjala `else`) ka të njëjtën pamje dhe kuptim si më parë. Nën atë pjesë, është shkruar fjala ``else``, në mënyrë të barabartë si fjala ``if``, e ndjekur nga një ``:``. Në rreshtat e mëposhtëm shkruajmë një ose më shumë deklarime të tjera, të cilat përbëjnë trupin **të degës tjetër**. Ky grup i dytë i deklaratave është i theksuar në një nivel më të dobët se fjala *else* më lart, dhe ekzekutohet nëse nuk përmbushet kushti i specifikuar në fjalinë "if".

Shembull - marrja dhe hedhja e topave
'''''''''''''''''''''''''''''''''''''''

.. questionnote::

    Ka 3 kuti para Karelit, dhe në secilën prej tyre mund të ketë ose një top ose pa topa. Kareli duhet të marrë topa nga kutitë që kanë topa mbi ta dhe të vendosë një top në secilin katror që fillimisht ishte i zbrazët. Karel ka topa të mjaftueshëm me të në fillim.

Duke përdorur formën e re, të zgjeruar të fjalisë ``if``, ne mund t'i themi Karelit: "Nëse ka një top në kuti, atëherë merr atë top, përndryshe hedh një top", në mënyrë që detyra të zgjidhet lehtë:

.. karel:: Karel_if__take_else_put
    :blockly:
   
    {
      setup: function() {
       var world = new World(4, 1);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
       world.balls = [];
       for (var k = 2; k <= world.getAvenues(); k++) {
          var ball = Math.random() > 0.5;
          world.balls.push(ball);
          if (ball)
                  world.putBall(k, 1);
           }
           var robot = new Robot();
       robot.setInfiniteBalls(true);
       var code = ["from karel import *",
        "for i in range(3):",
        "    move()",
        "    if is_ball_on_square():",
        "        pick_ball()",
        "    else:",
        "        drop_ball()"
       ]
       return {world: world, robot: robot, code: code};
      },

      isSuccess: function(robot, world) {
       for (var k = 2; k <= world.getAvenues(); k++)
              if (world.getBalls(k, 1) == world.balls[k-2])
             return false;
       return true;
      }
    }


Kapni topat që mund të arrini
''''''''''''''''''''''''''''''''''''


.. questionnote::

   Një labirint përbëhet nga dy rreshta. Karel është në rreshtin e sipërm, i cili është plotësisht i zbrazët dhe i kalueshëm. Në rreshtin e poshtëm mund të ketë pengesa, ose sheshe me një top. Detyra e Karel është të marr të gjitha topat.
   
.. karel:: Karel_if__take_all_from_lower_row
    :blockly:
   
    {
      setup: function() {

         function random(n) {
             return Math.floor(n * Math.random());
         }

         var world = new World(4 + random(4), 2);
         world.setRobotStartAvenue(1);
         world.setRobotStartStreet(2);
         world.setRobotStartDirection("E");

         world.addEWWall(1, 1, 1);
         var balls = 0;
         var prevBall = false;
         for (var i = 2; i <= world.getAvenues(); i++) {
             if (random(2) == 0 || (balls == 0 && i == world.getAvenues() - 1)) {
                 balls++;
                 if (!prevBall)
                    world.addNSWall(i-1, 1, 1);
                 world.putBall(i, 1);
                 prevBall = true;
             } else {
                 if (prevBall)
                    world.addNSWall(i-1, 1, 1);
                 world.addEWWall(i, 1, 1);
                 prevBall = false;
             }
         }

         var robot = new Robot();
         var code = ["from karel import *",
            "while front_is_clear():",
            "    move() # next square in upper row",
            "",
            "    # check the lower row",
            "    turn_right()           # southwards",
            "    if front_is_clear():   # if there is a square in the lower row",
            "        # tell Karel to go get the ball, ",
            "        # to come back to the upper row and turn east",
            "    # tell Karel, if he could not go to the lower row,",
            "    # to turn back to east, to be able to continue properly",
         ]
         return {world: world, robot: robot, code: code};
      },

      isSuccess: function(robot, world) {
           for (var i = 1; i <= world.getAvenues(); i++)
              for (var j = 1; j <= world.getStreets(); j++)
                 if (world.getBalls(i, j) != 0)
                    return false;
          return true;
      }
    }
   
.. commented out
   .. reveal:: Karel_if__take_all_from_lower_row_reveal
       :showtitle: Show solution
       :hidetitle: Hide solution
   
       One possible solution (not the only one) is the following:
   
       .. activecode:: Karel_if__take_all_from_lower_row_solution
           :passivecode: true
                       
           from karel import *
           while front_is_clear():
               move() # next square
               
               # check the lower row
               turn_right()  # southwards
               if front_is_clear(): # if there is a square in the lower row
                   move(); pick_ball() # go get the ball
                   
                   # go back to the upper row, and turn east
                   turn_left(); turn_left()
                   move(); turn_right() 
               else:
                   turn_left() # just turn back east


Vepro vetëm kur diçka nuk përmbushet
------------------------------------------

Le të themi që Kareli duhet të kthehet majtas nëse ai **nuk mund** të ecë përpara (nëse ai mund të shkojë përpara, ai nuk duhet të bëjë asgjë).

Sipas rregullave të shkrimit të një deklarimi *if*, pas kushtit (në trupin e degës së parë) duhet të ketë të paktën një deklaratë, dhe sipas logjikës së detyrës, ne nuk kemi nevojë për deklarata në atë vend. Në situata të tilla mund të shkruajmë:

.. activecode:: Karel_if__else_only
    :passivecode: true

    if front_is_clear():
        pass
    else:
        turn_left()

or

.. activecode:: Karel_if__not
    :passivecode: true

    if not front_is_clear():
        turn_left()

Në rastin e parë, ne përdorim deklarim të veçantë ``pass`` që nuk bën asgjë. Duke vepruar kështu, ne kënaqim sintaksën (rregullat e shkrimit) dhe marrim një program që funksionon ashtu siç dëshirojmë.

Në rastin e dytë, duke përdorur fjalën ``not``, bëjmë gjendjen e kundërt, që do të thotë se gjendja e deklarims *if* është e kënaqur kur Karel nuk mund të shkojë përpara. Në këtë rast, degët ndryshojnë role, kështu që dega *if* bëhet ajo që nuk është më e nevojshme.

Në disa detyra të ardhshme, ka diçka për të bërë vetëm kur kushti nuk plotësohet.

Shko ne një kuti bosh
'''''''''''''''''''''''


.. questionnote::

   Fillimisht, Kareli mund të përballet me secilën palë, por ai mund të fillojë të lëvizë vetëm në një drejtim. Kareli duhet të kthehet në sheshin e lirë dhe të bëjë një hap.
   
.. karel:: Karel_if__turn_to_free_square
   :blockly:

   {
      setup:function() {
         function random(n) {
            return Math.floor(n * Math.random());
         }
         
         var ww = [
            [
               '█████',
               '█N.0█',
               '█████'
            ],
            [
               '█████',
               '█S.0█',
               '█████'
            ],
            [
               '█████',
               '█E.0█',
               '█████'
            ],
            [
               '█████',
               '█W.0█',
               '█████'
            ],
            [
               '███',
               '█0█',
               '█.█',
               '█E█',
               '███'
            ],
            [
               '███',
               '█0█',
               '█.█',
               '█W█',
               '███'
            ],
            [
               '███',
               '█0█',
               '█.█',
               '█S█',
               '███'
            ],
            [
               '███',
               '█0█',
               '█.█',
               '█N█',
               '███'
            ],
            [
               '███████',
               '█0.0.N█',
               '███████'
            ],
            [
               '███████',
               '█0.0.S█',
               '███████'
            ],
            [
               '███████',
               '█0.0.W█',
               '███████'
            ],
            [
               '███████',
               '█0.0.E█',
               '███████'
            ],
            [
               '█████',
               '█0█N█',
               '█.█.█',
               '█0.0█',
               '█████'
            ],
            [
               '█████',
               '█0█S█',
               '█.█.█',
               '█0.0█',
               '█████'
            ],
            [
               '█████',
               '█0█W█',
               '█.█.█',
               '█0.0█',
               '█████'
            ],
            [
               '█████',
               '█0█E█',
               '█.█.█',
               '█0.0█',
               '█████'
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
         var X = world.getAvenues();
         var Y = world.getStreets();
         if (X == 2 && Y == 1) return robot.getAvenue() == 2 && robot.getStreet() == 1 && robot.getDirection() == "E";
         if (X == 1 && Y == 2) return robot.getAvenue() == 1 && robot.getStreet() == 2 && robot.getDirection() == "N";
         if (X == 3 && Y == 1) return robot.getAvenue() == 2 && robot.getStreet() == 1 && robot.getDirection() == "W";
         if (X == 2 && Y == 2) return robot.getAvenue() == 2 && robot.getStreet() == 1 && robot.getDirection() == "S";
         return false;
      }
   }

.. reveal:: Karel_if__turn_to_free_square_reveal
    :showtitle: Zgjidhja
    :hidetitle: Fshih zgjidhjen

    Ne ofrojmë 2 zgjidhje të shkurtra:
   
    .. activecode:: Karel_if__turn_to_free_square_solution1
        :passivecode: true
      
        from karel import *
        while not front_is_clear():
            turn_left()
        move()

    .. activecode:: Karel_if__turn_to_free_square_solution2
        :passivecode: true
      
        from karel import *
        for i in range(3):
            if not front_is_clear():
                turn_left()
        move()
                
Vendosni topa aty ku nuk ka
''''''''''''''''''''''''''''''''''

.. questionnote::

   Ekziston një numër i panjohur i kutive përpara Karelit, dhe, secila prej tyre mund të përmbajë një top ose asnjë top. Karel ka mjaft topa, dhe ai duhet të vendosë një top në çdo kuti të zbrazët.
   
.. karel:: Karel_if__fill_the_empty_squares
    :blockly:
   
    {
        setup: function() {
            function random(n) {
                return Math.floor(n * Math.random());
            }
            var N = 2 + random(5);
            var world = new World(N, 1);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.balls = [];
            world.putBall(1, 1);
            for (var k = 2; k <= world.getAvenues(); k++) {
                var ball = Math.random() > 0.5;
                world.balls.push(ball);
                if (ball)
                    world.putBall(k, 1);
            }
            var robot = new Robot();
            robot.setInfiniteBalls(true);
            var code = ["from karel import *",
                        "# write the program"
                        ]
            return {world: world, robot: robot, code: code};
        },

        isSuccess: function(robot, world) {
            for (var k = 1; k <= world.getAvenues(); k++)
                if (world.getBalls(k, 1) != 1)
                    return false;
            return true;
        }
    }
