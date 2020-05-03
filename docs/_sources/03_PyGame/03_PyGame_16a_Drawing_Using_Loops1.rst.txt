Vizatimi me ndihmën e loops
------------------------------

Shqyrtoni detyrën e mëposhtme: le të vizatojmë 6 rrathë, si në këtë foto:

.. image:: ../../_images/PyGame/target.png
   :width: 300px
   :align: center 

Duke parë figurën, mund të supozojmë (ose mund të ishte thënë në vendosjen e problemit) që rrathët janë të barabartë në hapësirë. Kjo do të thotë që diferenca në rreze të secilës dy rrathë ngjitur është e njëjtë.

Ne zgjedhim madhësinë e rrathëve të jenë sa më të mëdha të jetë e mundur, por të përshtaten në një hapësirë të caktuar vizatimi prej 300x300 piksele. Meqenëse gjerësia e dritares është 300 piksele, rrezja e rrethit më të madh është 150. Për ndryshimin e rrezeve të dy rrathëve ngjitur mund të marrim :math:`{150 \over 6} = 25`. Kjo jep rreze prej 25, 50, 75, 100, 125, 150.

Bazuar në vlerat e llogaritura, ne mund të shkruajmë një program si ky:

.. activecode:: PyGame_loop__target_fixed
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :includesrc: src\PyGame\1_Drawing\7a_UsingLoops\Examples\circles_target_fixed.py

Le të imagjinojmë që pas kësaj neve na u dha detyra e re për të bërë të njëjtën vizatim, por me 5 rrathë. Ky është një ndryshim shumë i vogël, apo jo? Ne duhet të jemi në gjendje të ripërdorim detyrën e zgjidhur më parë.

Kur fillojmë të punojmë në një vizatim me 5 rrathë, shohim që shumë pak nga programi i mëparshëm mund të përdoren. Në fakt, ne mund të përdorim vetëm idenë, dhe madhësia e rrathëve duhet të llogaritet nga e para.

Nëse do ta kishim shkruar programin ndryshe, rregullimi i tij do të ishte shumë më i lehtë. Për shembull, mund të shkruanim numrin e rrathëve në një variabël dhe më pas ta përdorim atë variabël në të gjitha llogaritjet e nevojshme. Ky program do të duket si ky:

.. activecode:: PyGame_loop__target_flexible
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :includesrc: src\PyGame\1_Drawing\7a_UsingLoops\Examples\circles_target_flexible.py

Në këtë program është e mjaftueshme të ndryshoni vetëm një numër në mënyrë që të vizaton çdo numër të caktuar të rrathëve.

Siç thamë edhe më parë, shumë vizatime kanë një rregullsi, siç janë simetria ose ndonjë pjesë përsëritëse (dhe shumë modele të tjera, më komplekse). Nëse e kuptojmë rregullsinë në vizatime të tilla dhe i shprehim në mënyrë matematikore, do të jemi në gjendje ta përdorim atë kur shkruajmë një program për të nxjerrë vizatime të tilla, siç kemi bërë në shembullin e mëparshëm. Në atë mënyrë ne marrim një program që është shumë më i lehtë për tu modifikuar për të marrë një vizatim tjetër, të ngjashëm. Për vizatimet me një numër të madh të përsëritjeve të një pjese (identike ose pak të modifikuar), programi që përdor rregullsinë do të jetë gjithashtu shumë më i shkurtër.

.. infonote::

    Shumë programe të përdorura nga miliona njerëz vazhdimisht përmirësohen dhe rafinohen dhe versionet e reja të programeve të tilla po publikohen. Prandaj, ndryshimet në program janë diçka krejt normale që ndodhin gjatë gjithë kohës. Situata është e ngjashme me programet që i shkruajmë vetë. Kur shkruajmë një program, mund të ndodhë që më vonë të mendojmë për diçka të re dhe të dëshirojmë të modifikojmë një pjesë të programit që është shkruar tashmë.
    
     Prandaj, kur shkruajmë programe, duhet të kemi parasysh që dikush (ndoshta edhe ne vetë) do të dëshirojë të krijojë një program të ngjashëm dhe mund të dëshirojë të përdorë programin tonë si një version fillestar.

Le të shohim një shembull tjetër se si mund të përdorim rregullsitë në një vizatim për të shkruar një program më fleksibël (një program që është më i lehtë për t’u përshtatur me një qëllim paksa të ndryshëm).

Shembull - antenë
'''''''''''''''''

Tashmë kemi parë një program që vizaton këtë antenë. Tani programi është shkruar në mënyrë që të mos jetë shumë e vështirë të ndryshosh numrin e segmenteve tërthor, ndarjen midis tyre, ndryshimin e gjatësive të segmenteve të njëpasnjëshme dhe të ngjashme.

.. activecode:: PyGame_loop__antenna
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :includesrc: src\PyGame\1_Drawing\7a_UsingLoops\Examples\antenna1.py

Një pjesë e programit që vizaton segmentet tërthorë të antenës mund të shkruhet si më poshtë:

.. code::

    for i in range(6):
        pg.draw.line(canvas, pg.Color('darkgray'), (120 - 10 * i,  75 + 25 * i), (180 +  10 * i,  75 + 25 * i), 1 + i//2)

Programi i shkruar në këtë mënyrë do të ishte pak më i shkurtër, por i pari është më i qartë, kështu që secili ka avantazhet e tij. Le të theksojmë vetëm se të dy këta programe janë më të mirë se sa vizatimi i 6 rreshtave një për një për segmentet tërthor (ne e kemi bërë). Nëse kjo pjesë e programit do të përbëhej nga gjashtë thirrje në funksionin e vizatimit të linjës, do të ishte më e vështirë të modifikohej dhe të rregullohej programi për të vizatuar një antenë ndryshe.

Numrat ekuivalentë
'''''''''''''''''''

Në të dy shembujt e mëparshëm, ishte e nevojshme të numëronit një ose më shumë seri numrash ekuivalentë. Në detyrën me rrathët, këta ishin numrat 25, 50, 75, 100, 125, 150 (rrezja e rrathëve), dhe në detyrën me antenën, na duheshin sa katër seri numrash - *x* dhe *y* koordinatat e skajeve të segmenteve të antenës tërthor. Në veçanti, këta numra janë:

- *x* koordinatat e skajeve të majta: 120, 110, 100, 90, 80, 70
- *y* koordinatat e skajeve të majta: 75, 100, 125, 150, 175, 200
- *x* koordinatat e skajeve të drejta: 180, 190, 200, 210, 220, 230
- *y* koordinatat e skajeve të drejta: 75, 100, 125, 150, 175, 200

Ne kemi parë që ka mënyra të ndryshme për të marrë vlerat që na duhen. Për shembull, në një detyrë me rrathë koncentrike, vlerat 25, 50, 75, 100, 125, 150 mund të marrim në ndonjë nga mënyrat e mëposhtme (po aq mirë):

..  code::

    for r in range(25, 151, 25):
        pg.draw.circle(canvas, pg.Color("red"), center, r, 2)

..  code::

    for i in range(br_krugova):
        pg.draw.circle(canvas, pg.Color("red"), center, round(25 + i * 25), 2)

..  code::

    r = 25
    for _ in range(br_krugova):
        pg.draw.circle(canvas, pg.Color("red"), center, r, 2)
        r += 25

Në rastin e përgjithshëm, nëse duhet të marrim një seri vlerash prej *a*, *a + d*, *a + 2d*, ... *a + (n-1) d*, tre metodat e mëparshme mund të jenë përdoret si më poshtë:

..  code::

    for x in range(a, a + n*d, d):
        print(x)

..  code::

    for i in range(n):
        print(a+i*d)

..  code::

    x = a
    for _ in range(n):
        print(x)
        x += d


Do të shohim që shumë detyra me vizatimin e formave ekuidente mund të zgjidhen duke aplikuar loops si kjo.

Vini re se funksioni ``range`` me një hap (me tre argumente) duhet të marrë argumente të plotë, kështu që në situatat kur hapi nuk është një numër i plotë përdorimi i tij nuk është i mundur.

Kur na duhet (si në një detyrë antene) të bëjmë disa seri në një loop, mënyra e parë është më pak e përshtatshme, prandaj duhet të zgjedhim njërën nga dy mënyrat e tjera.

Pyetjet e mëposhtme do t'ju ndihmojnë të konsolidoni njohuritë tuaja për formimin e një numri numrash ekuivalentë.

.. dragndrop:: pygame__loop_quiz_match_series
    :feedback: Provo përsëri!
    :match_1: 100, 200, 300, 400, 500|||for i in range(100, 600, 100)
    :match_2: 100, 300, 500|||for i in range(100, 601, 200)
    :match_3: 100, 200, 300, 400, 500, 600|||for i in range(100, 601, 100)
    :match_4: 200, 300, 400, 500, 600|||for i in range(200, 601, 100)

    Bashkoni një seri numrash me një lak që e gjeneron atë.
     
.. dragndrop:: pygame__loop_quiz_match_series2
    :feedback: Provo përsëri!
    :match_1: 100, 150, 200, 250, 300|||x = 100 + i*50
    :match_2: 50, 150, 250, 350, 450|||x = 50 + i*100
    :match_3: 0, 100, 200, 300, 400|||x = i*100
    :match_4: 100, 200, 300, 400, 500|||x = 100+i*100

    Përputhen numrat e marrë me shprehjen në loop "for i in range (5):" që i gjeneron ato.
    

.. mchoice:: pygame__loop_quiz_range01
    :answer_a: x = 25 * i + 50
    :answer_b: x = (25 + i) * 50
    :answer_c: x = 25 * 2*i+1
    :answer_d: x = 25 + 50 * i
    :correct: d
    :feedback_a: No.
    :feedback_b: No.
    :feedback_c: No.
    :feedback_d: Saktë!
    
    Cila shprehje duhet të përdoret në loop
    
    .. code::
    
        for i in range(19):
            x = ???
            ...
            
    që *x* të ketë të njëjtat vlera si në një loop

    .. code::
    
        for x in range(25, 500, 50):
            ...
            
Më poshtë janë detyrat për ushtrim.

Shkallë
''''''

Modifikoni programin në mënyrë që hapat e shkallëve të vizatohen në një loop.

.. activecode:: PyGame_loop__ladder
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7a_UsingLoops\Tasks\ladder.py

    canvas.fill(pg.Color("green")) # paint background

    pg.draw.line(canvas, pg.Color("brown"), (100, 10), (100, height - 10), 10)    # left side
    pg.draw.line(canvas, pg.Color("brown"), (200, 10), (200, height - 10), 10)    # right side

    # change (rewrite) this part
    pg.draw.line(canvas, pg.Color("brown"), (100,  50), (200, 50), 10) # step
    pg.draw.line(canvas, pg.Color("brown"), (100, 100), (200, 100), 10) # step
    pg.draw.line(canvas, pg.Color("brown"), (100, 150), (200, 150), 10) # step
    pg.draw.line(canvas, pg.Color("brown"), (100, 200), (200, 200), 10) # step
    pg.draw.line(canvas, pg.Color("brown"), (100, 250), (200, 250), 10) # step

   
.. reveal:: PyGame_loop__ladder_reveal
    :showtitle: Hint
    :hidetitle: Hide hint

   Në vend të 5 deklaratave të vizatimit të vijave, mund të përdorni një loop të formës vijuese:
    
    .. code::
    
        for y in ???:
            pg.draw.line(canvas, pg.Color("brown"), (100, y), (200, y), 10)
            
    Për ta kompletuar loop-in saktë, duhet t'i përgjigjeni pyetjes së mëposhtme:
    
    .. mchoice:: pygame__loop_quiz_range1
        :answer_a: range(0, 50, 250)
        :answer_b: range(250, 50)
        :answer_c: range(50, 251, 50)
        :answer_d: range(50, 250, 50)
        :correct: c
        :feedback_a: Jo, numri i parë është i papërshtashëm.
        :feedback_b: Jo, Provo përsëri.
        :feedback_c: Saktë!
        :feedback_d: Jo, numri i fundit është i papërshtashëm.
        
        Cila nga rangjet e ofruara jep vlera 50, 100, 150, 200, 250?

          
Pemë
'''''

Modifikoni programin në mënyrë që një pemë të vizatohet në secilën ose të tre kalon nëpër loop.

.. activecode:: PyGame_loop__trees
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7a_UsingLoops\Tasks\trees.py
   
    canvas.fill(pg.Color("green")) # paint background

    pg.draw.rect(canvas, pg.Color("brown"), (40, 180, 20, 100))        # first tree
    pg.draw.ellipse(canvas, pg.Color("darkgreen"), (10, 50, 80, 150))  # first treetop
    pg.draw.rect(canvas, pg.Color("brown"), (140, 180, 20, 100))       # second tree
    pg.draw.ellipse(canvas, pg.Color("darkgreen"), (110, 50, 80, 150)) # second treetop
    pg.draw.rect(canvas, pg.Color("brown"), (240, 180, 20, 100))       # third tree
    pg.draw.ellipse(canvas, pg.Color("darkgreen"), (210, 50, 80, 150)) # third treetop

.. reveal:: PyGame_loop__trees_reveal
    :showtitle: Hint
    :hidetitle: Hide hint

    The program can look like this:
    
    .. activecode:: PyGame_loop__trees_solution
        :nocodelens:
        :enablecopy:
        :modaloutput:
        :includexsrc: src\PyGame\1_Drawing\7a_UsingLoops\Tasks\trees.py

        canvas.fill(pg.Color("green")) # paint background

        for i in range(3):
            pg.draw.rect(canvas, pg.Color("brown"), (???, 180, 20, 100))        # tree
            pg.draw.ellipse(canvas, pg.Color("darkgreen"), (???, 50, 80, 150))  # treetop

    
    Në disa raste duhet të vendosen shprehje të përshtatshme për koordinatën *x* në vend të pikave të pyetjeve. Kur *i* merr vlerat 0, 1, 2 në rregull, shprehja në fjalinë e parë duhet të marrë vlerat 40, 140, 240 dhe shprehja në deklaratën e dytë duhet të marrë vlerat 10, 110, 210.


Rrjetë
''''

Modifikoni programin në mënyrë që linjat vertikale të vizatohen në një loop dhe linjat horizontale në loop-in e dytë.

.. activecode:: PyGame_loop__grid
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7a_UsingLoops\Tasks\grid.py
    
    pg.draw.line(canvas, pg.Color("black"), (10, 10), (10, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (30, 10), (30, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (50, 10), (50, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (70, 10), (70, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (90, 10), (90, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (110, 10), (110, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (130, 10), (130, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (150, 10), (150, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (170, 10), (170, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (190, 10), (190, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (210, 10), (210, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (230, 10), (230, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (250, 10), (250, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (270, 10), (270, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (290, 10), (290, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (310, 10), (310, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (330, 10), (330, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (350, 10), (350, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (370, 10), (370, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (390, 10), (390, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (410, 10), (410, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (430, 10), (430, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (450, 10), (450, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (470, 10), (470, height - 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (490, 10), (490, height - 10), 1)
    
    pg.draw.line(canvas, pg.Color("black"), (10, 10), (width - 10, 10), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 30), (width - 10, 30), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 50), (width - 10, 50), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 70), (width - 10, 70), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 90), (width - 10, 90), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 110), (width - 10, 110), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 130), (width - 10, 130), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 150), (width - 10, 150), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 170), (width - 10, 170), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 190), (width - 10, 190), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 210), (width - 10, 210), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 230), (width - 10, 230), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 250), (width - 10, 250), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 270), (width - 10, 270), 1)
    pg.draw.line(canvas, pg.Color("black"), (10, 290), (width - 10, 290), 1)

