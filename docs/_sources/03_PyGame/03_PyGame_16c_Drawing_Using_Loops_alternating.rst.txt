Bërja e vizatimeve më komplekse duke përdorur loops
----------------------------------------------------

Rregullsia që duam të përdorim në vizatime mund të jetë më komplekse, e krahasuar me problemet e mëparshme. Ketu jane disa shembuj:

.. image:: ../../_images/PyGame/repeat_alternating.png 
   :width: 800px
   :align: center 

Në të gjitha këto raste, rregullsia ende ekziston dhe mund të përdoret kur shkruani programe. Mund të vërejmë gjithashtu se shembujt në figurë të gjithë kanë diçka të përbashkët, që është se dy rregulla shfaqen në mënyrë alternative. Për shembull, në një vizatim me tulla, rreshti i parë i tullave fillon me tërë tullën, e dyta me gjysmë tullë, e treta përsëri me tërë tullën, etj. Në mënyrë të ngjashme, dritaret e ndriçuara dhe të lyera shfaqen në mënyrë alternative në vizatimin e ndërtesës.

Për shkak të alternimit të dy rregullave në të gjitha vizatimet, programet që vizatojnë ato do të kenë gjithashtu disa ngjashmëri. Le të shohim shembuj kodesh.

Shembull - zinxhir
''''''''''''''''''''

Për të vizatuar një zinxhir të tillë, sigurisht që do t'i vizatojmë linjat në një loop. Vizatimi tregon se çdo rresht pasues është i njëjti numër pikselësh më i ulët se ai i mëparshmi, kështu që nuk duhet të ketë asnjë problem me llogaritjen e koordinatës *y*. Situata me koordinatat *x* është disi më e vështirë sepse ato ndryshojnë sipas një rregulli pak më të ndërlikuar.

Ne mund ta zgjidhim këtë problem duke përdorur deklaratën *if* në loop. Pas vizatimit të një rreshti, ne kontrollojmë se cila nga dy vlerat e mundshme :math:`x` koordinata e fillimit të rreshtit ka. Nëse ka vlerën e parë - ia caktojmë asaj të dytën dhe anasjelltas. Ja si duket në program:

.. activecode:: PyGame_drawing_loops_zipper1
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :includesrc: src\PyGame\1_Drawing\7c_Loops_alternating\Examples\zipper1.py

Një mundësi tjetër për të zgjidhur problemin me koordinatat *x* është të vizatoni dy rreshta në një loop, për shembull:

.. activecode:: PyGame_drawing_loops_zipper2
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :includesrc: src\PyGame\1_Drawing\7c_Loops_alternating\Examples\zipper2.py


Shembull - Tulla
''''''''''''''''''

Ne kemi përmendur tashmë se rreshtat e tullave fillojnë në mënyrë alternative me tërë tullën dhe gjysmën e tullave. Kjo është arsyeja pse gjatë vizatimit të tullave mund të përdorim cilindo nga të njëjtat dy ide si në shembullin e mëparshëm.

Le të shënohet gjatësia e tullave nga :math:`a` dhe lartësia e saj nga :math:`h`. Ne e marrim tërë tullën në fillim të rreshtit duke vizatuar një drejtkëndësh në një lartësi të caktuar, me :math:`x` koordinatë e barabartë me zero. Gjysma e një tullë në fillim të një rreshti mund të merret duke vizatuar një tullë të tërë të zhvendosur nga :math:`a \ over 2` në të majtë, domethënë duke vizatuar një drejtkëndësh me :math:` x` koordinatë e barabartë me :code:`-a // 2`. Kështu, vetëm gjysma e djathtë e tullave është e dukshme. Mbetet për tu zgjidhur kur vizatojmë një tullë të zhvendosur dhe kur një të rregullt.

Një zgjidhje është që të ruani fillimin e rreshtit të tullave në një variabël, ta quajmë *x_start *. Pasi të tërhiqet secila rresht, kontrollojmë se ndryshorja *x_start* ka një vlerë zero ose :code: `-a // 2`. Ashtu si në shembullin e mëparshëm, cilindo prej dy vlerave që kemi, ne do t'i caktojmë vlerën tjetër në variabël, në mënyrë që në rreshtin tjetër vizatimi i tullave të fillojë ndryshe.

Kompletoni deklarimet e papërfunduara për vendosjen e variablës x_start

.. activecode:: PyGame_drawing_loops_bricks1
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7c_Loops_alternating\Examples\bricks1.py

    canvas.fill(pg.Color("red"))
    brick_a, brick_h = 80, 40
    x_start = 0
    for y0 in range(0, height, brick_h): # For each row of bricks
        for x0 in range(x_start, width, brick_a): # For each brick in the row
            pg.draw.rect(canvas, pg.Color("black"), (x0, y0, brick_a, brick_h), 1)
            
        if x_start == x_start: # fix the line
            x_start = -brick_a//2
        else:
            x_start = x_start # fix the line

Ideja e dytë është që të vizatojmë dy tulla në secilën kalim nëpër loop-in e dyfishtë: atë që kemi vizatuar në zgjidhjen e parë, dhe tullën poshtë dhe gjysmës së majtë të saj. Vini re se në këtë rast lak nga *y0* ka dy herë hapin, sepse loop i brendshëm vizaton dy rreshta tullash.

Deklarime të plota të papërfunduara për vizatimin e drejtkëndëshe

.. activecode:: PyGame_drawing_loops_bricks2
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includexsrc: src\PyGame\1_Drawing\7c_Loops_alternating\Examples\bricks2.py

    canvas.fill(pg.Color("red"))
    brick_width, brick_height = 80, 40
    for y0 in range(0, height, 2 * brick_height):
        for x0 in range(0, width, brick_width):
            # draw the first brick
            pg.draw.rect(???) # complete the statement as before
            
            # the second brick is in the following row, displaced by half its width
            x1, y1 = x0 - brick_width//2, y0 + brick_height 
            pg.draw.rect(???) # draw the brick below and half-left of the previous one


Ushtrime
''''''''''''''''''

.. questionnote:: 

    **Detyra - tabela e shahut**

     Vizatoni një tabelë shahu në të gjithë dritaren (sheshet e bordit duhet të jenë 50x50 pixel). Sheshi i poshtëm i majtë duhet të jetë i errët.

Pjesa më e madhe e programit është e shkruar, përpiquni ta mbaroni.

.. activecode:: PyGame_drawing_loops_chessboard
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7c_Loops_alternating\Tasks\chessboard1.py
    
    canvas.fill(pg.Color("gray")) # background - light squares
    
    # square size
    num_squares = 8
    square_width = width / num_squares
    square_height = height / num_squares

    # go through all the squares
    for i in range(num_squares):
        for j in range(num_squares):
            # paint black squares only
            if (i + j) % 2 != 0:
                pass # fix the statement


.. questionnote::

    **Detyra - Ndërtesa**

     Modifikoni programin më poshtë në mënyrë që dritaret të vizatohen në një lak të dyfishtë.

Pjesa që duhet të ndryshohet, pas ndryshimit, mund të fillojë si kjo:

.. code::

    for y in range(5):     # floor
        for x in range(2): # side of the building (0 - left, 1 - right)
            if (x+y) % 2 == 0:
                color = ...


.. activecode:: PyGame_drawing_loops_building_alternating
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7c_Loops_alternating\Tasks\building_alternating.py
    
    pg.draw.rect(canvas, pg.Color("darkgray"), (120, 50, 60, 140)) # building

    # change this part
    pg.draw.rect(canvas, pg.Color('yellow'), (130,  60, 15, 15))
    pg.draw.rect(canvas, pg.Color('black'), (155,  60, 15, 15))
    pg.draw.rect(canvas, pg.Color('black'), (130,  80, 15, 15))
    pg.draw.rect(canvas, pg.Color('yellow'), (155,  80, 15, 15))
    pg.draw.rect(canvas, pg.Color('yellow'), (130, 100, 15, 15))
    pg.draw.rect(canvas, pg.Color('black'), (155, 100, 15, 15))
    pg.draw.rect(canvas, pg.Color('black'), (130, 120, 15, 15))
    pg.draw.rect(canvas, pg.Color('yellow'), (155, 120, 15, 15))
    pg.draw.rect(canvas, pg.Color('yellow'), (130, 140, 15, 15))
    pg.draw.rect(canvas, pg.Color('black'), (155, 140, 15, 15))

    pg.draw.rect(canvas, pg.Color("black"),  (140, 160, 20, 30))   # door

~~~~

Nëse nuk keni pasur ndonjë problem të madh me të gjitha këto detyra, përpiquni të zgjidhni edhe një detyrë më të vështirë.

.. questionnote::

    **Detyra - sfidë: parket**

     Shkruani një program që tregon parketin (ju mund të shihni foton me parket kur klikoni në butonin "Luaj lojën", dhe fotografia është e njëjtë si në fillim të kësaj faqe, apo jo). Qëllimi, natyrisht, është të vizatoni dërrasat e dyshemesë në një loop të shumëfishtë. Dimensionet e bordit janë 10x60 dhe ngjyrat janë të arta dhe kafe.

Skeleti i programit përafërsisht duket si ky:

.. code::

    for row ...
        for column ...
            if ...
                for floorboard in range(6):
                    pg.draw.rect(...)
            else:
                for floorboard in range(6):
                    pg.draw.rect(...)


.. activecode:: PyGame_drawing_loops_parquet
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7c_Loops_alternating\Tasks\parquet.py
