Lëvizja e vizatimit
----------------------

Në shembujt e mëparshëm, kemi bërë disa vizatime të përbëra nga forma themelore. Duke vepruar kështu, ishte e nevojshme të përcaktohej pozicioni i saktë për secilën nga këto forma që të bashkohen të gjitha pjesët së bashku. Për disa vizatime, ishte e mundur (dhe në disa detyra të kërkuara) që koordinatat e pikave individuale të llogariten bazuar në koordinatat e njohura të pikave të tjera. Ky llogaritje mund të ishte bërë jashtë programit dhe pastaj koordinatat e llogaritura thjesht mund të ishin futur në program. Sidoqoftë, është më mirë të kryhen llogaritjet e tilla në vetë programin, për disa arsye:

- Ne mund të mos i llogaritim saktë koordinatat në përpjekjen e parë. Në një situatë të tillë, është më e lehtë të modifikohen udhëzimet e llogaritjes (d.m.th. programi) sesa të llogaritni gjithçka manualisht që nga fillimi.
- Kur krijojmë vizatimin vetë, mund të jetë që pas versionit të parë të programit mund të dëshirojmë të shtojmë diçka, për shembull në anën e majtë të vizatimit, por që nuk kemi hapësirë ​​të mjaftueshme. Në këtë rast, e gjithë vizatimi duhet të zhvendoset në të djathtë, në mënyrë që koordinatat *x* të të gjitha pikave të rriten me të njëjtën vlerë. Nëse llogaritim me dorë koordinatat e pikave, duhet t'i llogaritim përsëri të gjitha. Në një program vizatimi të organizuar mirë, është e mjaftueshme të ndryshoni një numër për të lëvizur tërë vizatimin në të djathtë. Ky proces mund të ketë nevojë të përsëritet disa herë derisa të jemi të kënaqur me pozicionin e pjesës së vizatuar, kështu që provimi i tij është shumë më i lehtë kur programi bën llogaritjen në vend të nesh.
- Nëse duam të vizatojmë të njëjtën vizatim në shumë vende në dritare, përfitimet e llogaritjes brenda programit vijnë përsëri në dritë.

Tani do ta sistemojmë pak më shumë llogaritjen e koordinatave dhe do ta përdorim për të lëvizur më lehtë objektet e vizatuara. Para se të fillojmë, do të ishte një ide e mirë për të kontrolluar sfondin dhe t'u përgjigjemi këtyre pyetjeve:

.. mchoice:: PyGame__drawing_quiz_point_left
   :answer_a: (50, 60)
   :answer_b: (50, 80)
   :answer_c: (40, 70)
   :answer_d: (60, 70)
   :answer_e: (40, 60)
   :correct: c
   :feedback_a: Provo përsëri.
   :feedback_b: Provo përsëri.
   :feedback_c: Saktë!
   :feedback_d: Provo përsëri.
   :feedback_e: Provo përsëri.

   Cilat janë koordinatat e pikës 10 piksele në të majtë të pikës (50, 70)?

.. mchoice:: PyGame__drawing_quiz_point_down
   :answer_a: (50, 60)
   :answer_b: (50, 80)
   :answer_c: (40, 70)
   :answer_d: (60, 70)
   :answer_e: (40, 60)
   :correct: b
   :feedback_a: Provo përsëri.
   :feedback_b: Saktë!
   :feedback_c: Provo përsëri.
   :feedback_d: Provo përsëri.
   :feedback_e: Provo përsëri.

   Cilat janë koordinatat e pikës 10 piksel nën pikën (50, 70)?

.. mchoice:: PyGame__drawing_quiz_rect_up_left
   :answer_a: pg.draw.rect(canvas, color, (70, 120, 50, 60))
   :answer_b: pg.draw.rect(canvas, color, (100, 150, 110, 120))
   :answer_c: pg.draw.rect(canvas, color, (100, 150, 50, 60))
   :answer_d: pg.draw.rect(canvas, color, (70, 120, 80, 90))
   :answer_e: pg.draw.rect(canvas, color, (70, 180, 80, 90))
   :correct: d
   :feedback_a: Provo përsëri.
   :feedback_b: Provo përsëri.
   :feedback_c: Provo përsëri.
   :feedback_d: Saktë!
   :feedback_e: Provo përsëri.

   Drejtkënëshi është vizatuar duke përdorur``pg.draw.rect(canvas, color, (100, 150, 80, 90))``. Si mund të vizatoni një drejtkëndësh me të njëjtën madhësi, të vendosur 30 pixel në të majtë dhe 30 piksele mbi këtë drejtkëndësh?

.. mchoice:: PyGame__drawing_quiz_circle_above
   :answer_a: pg.draw.circle(canvas, color, (100, 120), 40)
   :answer_b: pg.draw.circle(canvas, color, (100, 160), 40)
   :answer_c: pg.draw.circle(canvas, color, (120, 100), 40)
   :answer_d: pg.draw.circle(canvas, color, (160, 100), 40)
   :answer_e: pg.draw.circle(canvas, color, (20, 120), 40)
   :correct: a
   :feedback_a: Saktë!
   :feedback_b: Provo përsëri.
   :feedback_c: Provo përsëri.
   :feedback_d: Provo përsëri.
   :feedback_e: Provo përsëri.

   Rrethi ëeshtë vizatuar duke përdorur ``pg.draw.circle(canvas, color, (100, 200), 40)``. Si mund të vizatohet një rreth me të njëjtën madhësi mbi këtë rreth dhe ta prekë atë?


Ndryshime për të bërë një vizatim lehtësht të lëvizshëm
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

Le të shohim se si një re është vizatuar në shembullin e mëposhtëm:

.. activecode:: PyGame__drawing_cloud_fixed
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\5_Movable\cloud_fixed.py

Ne prezantuam renë me tre rrathë, një më të madh në mes dhe dy më të vegjël rreth tij:

.. code::

    pg.draw.circle(canvas, pg.Color("white"), (200, 200), 50)
    pg.draw.circle(canvas, pg.Color("white"), (150, 200), 30)
    pg.draw.circle(canvas, pg.Color("white"), (250, 200), 30)

Nëse do të donim ta vizatonim atë re në lartësi të ndryshme, mund të përsërisnim këto tre komanda, çdo herë me disa vlera të reja për :math:`y` koordinata e qendrave të këtyre tre rrathëve në vend të 200, siç është në vizatimin e parë . Për shembull:

.. code::

    pg.draw.circle(canvas, pg.Color("white"), (200, 200), 50)
    pg.draw.circle(canvas, pg.Color("white"), (150, 200), 30)
    pg.draw.circle(canvas, pg.Color("white"), (250, 200), 30)

    pg.draw.circle(canvas, pg.Color("white"), (200, 80), 50)
    pg.draw.circle(canvas, pg.Color("white"), (150, 80), 30)
    pg.draw.circle(canvas, pg.Color("white"), (250, 80), 30)
    
    pg.draw.circle(canvas, pg.Color("white"), (200, 320), 50)
    pg.draw.circle(canvas, pg.Color("white"), (150, 320), 30)
    pg.draw.circle(canvas, pg.Color("white"), (250, 320), 30)

.. image:: ../../_images/PyGame/clouds.png
    :width: 400px
    :align: center

Në këtë mënyrë, jo vetëm që programi rritet më shpejt se sa duhet, ne gjithashtu duhet të bëjmë çdo ndryshim në tre vende (për shembull, nëse duam të provojmë 330 në vend të 320, ai ndryshim duhet të bëhet në tre vende). Tre ndryshime nuk janë të shumta, por nëse e pranojmë këtë mënyrë të të bërit të gjërave, do të kishim gjithnjë e më shumë probleme në vizatime më komplekse, ose në programe komplekse në përgjithësi.

Në vend të kësaj, është më mirë të krijoni një funksion dhe të kaloni :math:`y` koordinata e qendrave si parametër:

.. code::

    def cloud(yc):
        pg.draw.circle(canvas, pg.Color("white"), (200, yc), 50)
        pg.draw.circle(canvas, pg.Color("white"), (150, yc), 30)
        pg.draw.circle(canvas, pg.Color("white"), (250, yc), 30)

    cloud(200)
    cloud(80)
    cloud(320)

Programi i ri është më i lehtë për tu lexuar dhe modifikuar më tej. Për më shumë re, ose re më komplekse, avantazhi i kësaj qasje do të ishte edhe më i madh.

~~~~

Tani le të shqyrtojmë se si duhet ta lëvizim renë në të majtë ose në të djathtë. Ne duhet të rrisim ose ulim koordinatat :math:`x` të të gjitha rrathëve (200, 150, 250) me të njëjtën vlerë. Për shembull, nëse do të shtypnim koordinatat 260, 210, 310 si :math:`x`, e gjithë reja do të lëvizet 60 pixel në të djathtë.

Do të ishte mirë nëse do të mund të përdorim vetëm një numër të vetëm për të specifikuar pozicionin horizontal të reve. Për ta arritur këtë, vërejmë se qendrat e rrathëve më të vegjël janë 50 pixel larg nga qendra e rrethit të mesëm në të majtë dhe të djathtë. Këto distanca nuk ndryshojnë kur lëviz reja. Kjo do të thotë që nëse tregojmë :math:`x` koordinata e qendrës së rrethit të mesëm me:math:` X_c`, atëherë qendrat e rrathëve më të vogla kanë :math:`x` koordinatat :math:` X_c - 50 `dhe:math:` X_c + 50`. Falë kësaj lidhjeje (e cila nuk varet nga pozicioni i resë), tani mund të prezantojmë edhe parametrin :math:`x` në funksionin që vizaton renë:

.. code::

    def cloud(xc, yc):
        pg.draw.circle(canvas, pg.Color("white"), (xc, yc), 50)
        pg.draw.circle(canvas, pg.Color("white"), (xc - 50, yc), 30)
        pg.draw.circle(canvas, pg.Color("white"), (xc + 50, yc), 30)
        
    cloud(200, 200)
    cloud(200, 80)
    cloud(200, 320)

Secila prej këtyre tre reve tani mund të zhvendoset lehtësisht, për shembull, 60 pixel në të djathtë, duke shtypur 260 si parametrin e parë në vend të 200 në thirrjet e funksionit. Është po aq e thjeshtë për të bërë një vizatim me disa re. Ngjyra, ose hija e gri, gjithashtu mund të jetë një parametër i funksionit. Në këtë mënyrë, disa reve mund të jenë më të errëta dhe disa më të ndritshme.

Kur përdorim të gjitha sa më sipër, mund të krijojmë një program që vizaton disa re me hije të ndryshme, për shembull:

.. activecode:: PyGame__drawing_cloud_movable
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\5_Movable\clouds_movable.py

Le të përmbledhim, me përgjithësime të vogla, çfarë duhet të bëhet për të qenë në gjendje të tregojmë një vizatim në vende të ndryshme:

- Duhet të zgjedhim një pikë, koordinatat e së cilës vendosen direkt. Ne e quajmë këtë pikë të zgjedhur **pikën kryesore**, (nganjëherë kjo pikë quhet edhe **anchor**). Në shembullin e reve, pika kryesore është qendra e rrethit të mesëm.
- Pas zgjedhjes së pikës kryesore, koordinatat e të gjitha pikave të tjera të rëndësishme përcaktohen në lidhje me të duke shtuar ose zbritur një zhvendosje të caktuar në koordinatat e pikës kryesore. Në shembullin me re, për të marrë :math:`x` koordinata e qendrës së rrethit të majtë, nga :math:` x` koordinata e pikës kryesore (qendra e rrethit të mesëm) ne zbritim 50 pixel, dhe për rrethi i duhur shtojmë 50 pixel.

Në rastin e përgjithshëm, në vizatim mund të ketë forma të ndryshme nga rrathët. Pikat e rëndësishme që përcaktojnë pozicionet e këtyre formave janë:

- për një vizë: skajet e saj
- për një shumëkëndësh: pikat e saj
- për një rreth: qendra e saj
- për një drejtkëndësh: këndi i sipërm i saj i majtë
- për një elips: këndi i sipërm i majtë i drejtkëndëshit në të cilin është gdhendur ajo elips

Të gjitha këto pika duhet të jepen në lidhje me pikën kryesore, domethënë, koordinatat e tyre duhet të shprehen si koordinata të pikës kryesore, të rritura ose të zvogëluara për ndonjë vlerë.

Kontrolloni të kuptuarit tuaj për shpjegimet e mëparshme dhe përgjigjuni pyetjeve.

.. mchoice:: PyGame__drawing_quiz_anchor_introduction1 
   :answer_a: pg.draw.circle(canvas, pg.Color("red"), (x, y), 50, 1)
   :answer_b: pg.draw.circle(canvas, pg.Color("red"), (x+120, y+90), 50, 1)
   :answer_c: pg.draw.circle(canvas, pg.Color("red"), (x+20, y-10), 50, 1)
   :answer_d: pg.draw.circle(canvas, pg.Color("red"), (x-20, y+10), 50, 1)
   :correct: c
   :feedback_a: Provo përsëri.
   :feedback_b: Provo përsëri.
   :feedback_c: Saktë!
   :feedback_d: Provo përsëri.

   Ne dëshirojmë të rregullojmë një vizatim të përbërë nga disa forma, në mënyrë që gjithçka të vizatohet në lidhje me anchor me koordinatat `x = 100`,` y = 100`. Një nga pohimet që formojnë një vizatim është
                
   .. activecode:: PyGame__drawing_quiz_anchor_introduction_code1
      :passivecode: true
                    
      pg.draw.circle(canvas, pg.Color("red"), (120, 90), 50, 1)

   Cila fjali e zëvendëson këtë?
      
.. mchoice:: PyGame__drawing_quiz_anchor_introduction2
   :answer_a: pg.draw.line(canvas, pg.Color("red"), (x-50, y-50), (150, 150))
   :answer_b: pg.draw.line(canvas, pg.Color("red"), (x-50, y-50), (x+50, y+50))
   :answer_c: pg.draw.line(canvas, pg.Color("red"), (x-50, x+50), (y-50, y+50))
   :answer_d: pg.draw.line(canvas, pg.Color("red"), (x+50, y+50), (x+150, y+150))
   :correct: b
   :feedback_a: Provo përsëri.
   :feedback_b: Saktë!
   :feedback_c: Provo përsëri.
   :feedback_d: Provo përsëri.
 
Ne dëshirojmë të rregullojmë një vizatim të përbërë nga disa forma, në mënyrë që gjithçka të vizatohet në lidhje me anchor me koordinatat `x = 100`,` y = 100`. Një nga pohimet që formojnë një vizatim është
               
   .. activecode:: PyGame__drawing_quiz_anchor_introduction_code2
      :passivecode: true
                    
pg.draw.line(canvas, pg.Color("red"), (50, 50), (150, 150))

Cila fjali e zëvendëson këtë?
      
.. mchoice:: PyGame__drawing_quiz_anchor_introduction3
   :answer_a: pg.draw.rect(canvas, pg.Color("red"), (x-50, y-50, x, y))
   :answer_b: pg.draw.rect(canvas, pg.Color("red"), (x, y, 100, 100))
   :answer_c: pg.draw.rect(canvas, pg.Color("red"), (x+50, y+50, 100, 100))
   :answer_d: pg.draw.rect(canvas, pg.Color("red"), (x-50, y-50, 100, 100))
   :correct: d
   :feedback_a: Provo përsëri.
   :feedback_b: Provo përsëri.
   :feedback_c: Provo përsëri.
   :feedback_d: Saktë!

Ne dëshirojmë të rregullojmë një vizatim të përbërë nga disa forma, në mënyrë që gjithçka të vizatohet në lidhje me anchor me koordinatat `x = 100`,` y = 100`. Një nga pohimet që formojnë një vizatim është
                
   .. activecode:: PyGame__drawing_quiz_anchor_introduction_code3
      :passivecode: true
   
pg.draw.rect(canvas, pg.Color("red"), (50, 50, 100, 100))

    Cila fjali e zëvendëson këtë?
      
.. mchoice:: PyGame__drawing_quiz_move_to_the_right
   :multiple_answers:
   :answer_a: Instead of pg.draw.circle(canvas, color, (x, y), r, d) we call pg.draw.circle(canvas, color, (x+100, y), r, d).
   :answer_b: Instead of pg.draw.circle(canvas, color, (x, y), r, d) we call pg.draw.circle(canvas, color, (x-100, y-100), r, d).
   :answer_c: Instead of pg.draw.rect(canvas, color, (x, y, w, h), d) we call pg.draw.circle(canvas, color, (x+100, y, w+100, h), d).
   :answer_d: Instead of pg.draw.rect(canvas, color, (x, y, w, h), d) we call pg.draw.rect(canvas, color, (x+100, y, w, h), d).
   :answer_e: Instead of pg.draw.rect(canvas, color, (x, y, w, h), d) we call pg.draw.rect(canvas, color, (x-100, y, w, h), d).
   :correct: a, d
   :feedback_a: Saktë!
   :feedback_b: Provo përsëri.
   :feedback_c: Provo përsëri.
   :feedback_d: Saktë!
   :feedback_e: Provo përsëri.

   Ne duam të lëvizim një vizatim të përbërë nga disa forma në të djathtë nga 100 piksele. Shënoni pretendimet e sakta.

Shembujt e mëposhtëm trgojnë konvertimin e në vizatimi statik në një të lëvizshëm.

Ariu -  pozicioni
'''''''''''''''''''''

Programi i mëposhtëm, i cili tregon kokën e ariut të lodrave, është dhënë:

.. activecode:: PyGame__drawing_bear_fixed
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\5_Movable\teddy-bear_fixed.py





Programi e quan funksionin *framed_circle* shtatë herë, i cili vizaton rrethin e dhënë me kufi të zi (megjithëse mund të ishte shmangur për tre rrathët e vegjël të zi). Për të qenë në gjendje të ndryshojmë pozicionin e vizatimit, le të zgjedhim pikën kryesore (anchor). Bëni atë qendër të një rrethi të madh, domethënë kokat e ariut. Koordinatat e kësaj pike janë (250, 150). Tani duhet të shprehim koordinatat e qendrave të të gjitha rrathëve të tjera në lidhje me pikën kryesore. Merrni si shembull veshin e djathtë të ariut.

:math:`x` koordinata e qendrës së veshit të djathtë është :math:` 310 = 250 + 60`, ndërsa :math:`y` koordinata është :math:` 80 = 150 - 70`. Nga këtu mund të shohim që koordinatat e qendrës së veshit të djathtë mund të shkruhen në program si `(cx + 60, cy - 70)`, ku `(cx, cy)` janë koordinatat e pikës kryesore.

Ndiqni të njëjtën procedurë për rrathët e tjera dhe plotësoni funksionin *Draw_teddy*.

.. activecode:: PyGame__drawing_bear_movable1
    :nocodelens
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\5_Movable\teddy-bear_movable1b.py

   
    canvas.fill(pg.Color("white")) # paint background
    
    def framed_circle(canvas, color, center, radius):
        pg.draw.circle(canvas, color, center, radius)
        pg.draw.circle(canvas, pg.Color("black"), center, radius, 1)

    def draw_teddy(cx, cy):
        framed_circle(canvas, pg.Color("yellow"), (cx - 60,  cy - 70),  45) # left ear
        # complete the program
        
    draw_teddy(width // 2, height // 2)

    
Ky program na lejon të shfaqim me lehtësi arinj në vende të ndryshme të ekranit. Për shembull, thirrja e funksionit

.. code::

    draw_teddy(width // 2, height // 2)
    
e cila vizaton një arush me pikën kryesore në qendër të dritares (ashtu siç ishte), mund të zëvendësohet me dy vija: e cila vizaton një ari me pikën kryesore në qendër të dritares (ashtu siç ishte), mund të jetë zëvendësuar me dy në vija:

.. code::

    draw_teddy(width // 2 - 120, height // 2)
    draw_teddy(width // 2 + 120, height // 2)

Provoni këtë! Do të ishte shumë më e vështirë të vizatonim një arush tjetër nëse nuk do të kishim përshtatur programin fillestar për këtë përdorim.

Shtëpia - pozicioni
''''''''''''''''''''''

Le të themi që e keni shkruar këtë program, dhe qëllimi juaj është të shkruani programin në mënyrë që shtëpia të zhvendoset lehtësisht:

.. activecode:: PyGame__drawing_house_detailed_fixed
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\5_Movable\house2D_detailed_fixed.py

Le të jetë pika kryesore :code: `(x, y) = (50, 150)`. Përfundoni rimodelimin e nisur të programit në kutinë më poshtë, ku vizatimi është bërë në funksionin :code:`Draw_house (x, y, wall_color)`. Pasi të siguroheni që vizatimet në të dy programet duken njësoj (përveç që ato vizatohen në dritare me madhësi të ndryshme), zëvendësoni kodin :code: `Draw_house (50, 150, pg.Color (" khaki "))` 4 tjetër, për të marrë figurën si kur klikoni në butonin "Luaj lojën":

.. code::

    draw_house(150,  90, pg.Color(220, 220, 220))
    draw_house(220, 130, pg.Color("white"))
    draw_house(350, 160, (255,255,150))
    draw_house( 50, 150, pg.Color("khaki"))

.. activecode:: PyGame__drawing_house_detailed_movable
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask: 
    :includexsrc: src\PyGame\1_Drawing\5_Movable\house2D_detailed_movable.py
   
    canvas.fill(pg.Color("darkgreen")) # paint background

    def draw_house(x, y, wall_color):
        pg.draw.polygon(canvas, pg.Color("red"), [(x, y), (x+???, y-???), (x+140, y)]) # roof
        pg.draw.rect(canvas, wall_color,       (x,       y,     140, 100)) # walls
        pg.draw.rect(canvas, pg.Color("brown"), (x + ???, y + ???,  30,  30)) # left window
        pg.draw.rect(canvas, pg.Color("brown"), (x + ???, y + ???, ???, ???)) # right window
        pg.draw.rect(canvas, pg.Color("brown"), (x + ???, y + ???, ???, ???)) # door
        
    draw_house( 50, 150, pg.Color("khaki"))




.. commented out

    The task is non-active (commented out) until a related technical issue is resolved.

    Task - a constantly moving drawing
    ''''''''''''''''''''''''''''''''''

    The following function draws some drawing.
       
    .. activecode:: PyGame__drawing_movable_scalable_given
        :passivecode: true

        def draw():
            prozor.fill(pg.Color("white"))
            pg.draw.circle(canvas, pg.Color("blue"), (100, 100), 60)
            pg.draw.circle(canvas, pg.Color("yellow"), (75, 75), 15)
            pg.draw.circle(canvas, pg.Color("black"), (80, 80), 5)
            pg.draw.circle(canvas, pg.Color("yellow"), (125, 75), 15)
            pg.draw.circle(canvas, pg.Color("black"), (120, 80), 5)
            pg.draw.ellipse(canvas, pg.Color("red"), (75, 110, 50, 10))

    In the program that follows, the drawing function is just started. Complete it by drawing the same drawing, but using the anchor :math:`(x, y)`, which is located in the center of the blue circle (initially this is the point :math:`(100, 100)`).

    When you finish the function, make sure it works the same as when you click the "Play task" button.

    .. activecode:: PyGame__drawing_movable
       :nocodelens:
       :enablecopy:
       :modaloutput:
       :playtask:
       :includexsrc: src\PyGame\1_Drawing\5_Movable\movable_scalable.py
       
                     
       def draw():
           canvas.fill(pg.Color("white"))

.. commented out

    .. reveal:: PyGame__drawing_movable_reveal
       :showtitle: Show solution
       :hidetitle: Hide solution

       .. activecode:: PyGame_movable_code
          :passivecode:

          def draw():
              canvas.fill(pg.Color("white"))
              pg.draw.circle(canvas, pg.Color("blue"), (x, y), 60)
              pg.draw.circle(canvas, pg.Color("yellow"), (x-25, y-25), 15)
              pg.draw.circle(canvas, pg.Color("black"), (x-20, y-20), 5)
              pg.draw.circle(canvas, pg.Color("yellow"), (x+25, y-25), 15)
              pg.draw.circle(canvas, pg.Color("black"), (x+20, y-20), 5)
              pg.draw.ellipse(canvas, pg.Color("red"), (x-25, y+10, 50, 10))
           

