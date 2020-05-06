Eventet e tastierës
---------------------

Nga eventet e krijuara në tastierë, më e rëndësishmja është ngjarja kryesore e shtypjes, kështu që ne do të përqendrohemi më shumë në atë. Kur shtypni tastet në tastierë, në objektin *event* që përfaqëson një ngjarje në programet tona, vlera e *events.type* do të jetë ``pg.KEYDOWN``.

Kur shtypnja e një çelësi në tastierë është regjistruar, ne pothuajse gjithmonë dëshirojmë të dimë se cili çelës është. Këtë mund ta zbulojmë duke testuar vlerën e ``event.key``. Siç kemi përmendur tashmë në mësimin për të lexuar gjendjen e tastierës, ekziston një konstantë për secilën çelës që korrespondon me atë çelës. Le të rikujtojmë emrat e këtyre konstantave për disa çelësa të testuar shpesh (mund të shihni një listë të plotë të këtyre konstanteve
 (`këtu <https://www.pygame.org/docs/ref/key.html>`__ ):

============ ==============
Celësi       konstant
============ ==============
pg.K_LEFT    shigjeta majtas
pg.K_RIGHT   shigjeta djathtas
pg.K_UP      shigjeta lart
pg.K_DOWN    shigjeta poshtë
pg.K_SPACE   space bar
pg.K_a       çelësi *a*
pg.K_b       çelësi *b* 
pg.K_c       çelësi *c* 
============ ==============

Vlera e *event.key* na tregon se cili çelës fizik shtypet, dhe kjo vlerë është e përshtatshme për çelësat siç janë çelësat shigjetë, *Ctrl*, *Shift*, *Alt*, *Home*, *End* dhe të ngjashme Kur bëhet fjalë për tekstin, mund të jetë më i përshtatshëm të përdoret vlera e fushës ``event.unicode``, e cila përmban karakterin që sapo ishte shtypur (si një varg i vetëm karakteresh).

Shembulli i mëposhtëm ilustron testimin e një goditjeje kryesore ose një ngjarje *pg.KEYDOWN*.

.. questionnote::

    **Shembull - fjalëkryq** 
    
    Në këtë shembull, përdoruesi mund të përdorë tastet e shigjetave në tastierë për të lëvizur kornizën dhe për të futur shkronja në kuti.
    
Vini re funksionin *hand_event* në të cilin ndodh kontrolli i llojit të ngjarjes, dhe pastaj, nëse është një shtypje kryesore, kontrollohen informacione shtesë për ngjarjen, të ruajtura në fushat *event.key* dhe *event.unicode*.

Për më tepër, mund të provoni të bashkoni disa fjalëkryq interesantë.

.. activecode:: PyGame__interact_crossword
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src/PyGame/3_Interaction/3e_Keyboard_events/crossword.py
    
Le ta krahasojmë këtë program me programin "Navigimi" nga mësimi i leximit të statusit të tastierës:

=========================================================== =============================================================
Në programin "Navigimi"                                     Në programin "Fjalëkryq"
=========================================================== =============================================================
rrethi i verdhë po lëvizte me një pixel                     po rrëshqiste lëvizjet e kornizës nga një fushë - kërcen
nuk kemi pasur kontroll të saktë se ku do të ndalet rrethi  ne mund të kontrollojmë saktësisht se ku do të ndalet korniza
nuk kishte rëndësi se ku do të ndalonte saktësisht rrethi   ka rëndësi se ku do të ndalet saktësisht korniza
ne po lexonim statusin e çelësave të tastierësne            jemi duke përdorur një ngjarje (duke shtypur një çelës)
 (poshtë ose lart) 
=========================================================== =============================================================


.. questionnote::

    **Detyrë - navigo rreth fushave** 
    
    Shkruaj një program që funksionon siç tregohet në shembullin (butoni "Luaj detyrën").
    
     Përdoruesi mund të përdorë tastet e shigjetave në tastierë për të udhëhequr personazhin e përfaqësuar me një rreth të verdhë. Karakteri lëviz nëpër fusha me pika të bardha.
    

.. activecode:: PyGame__interact_pacman1
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/3_Interaction/3e_Keyboard_events/pacman1.py
    
    import pygame as pg, pygamebg
    num_rows, num_cols = 10, 10
    a = 50 # square size
    (width, height) = (a* num_cols, a * num_rows)
    canvas = pygamebg.open_window(width, height, "Dot-eater")

    (character_row, character_col) = (num_rows // 2, num_cols // 2)

    def new_frame():
        canvas.fill(pg.Color("black"))   # paint canvas

        # white dots
        for x in range(a // 2, width, a):
            for y in range(a // 2, height, a):
                pg.draw.circle(canvas, pg.Color("white"), (x, y), 3)
       
        # HERE ADD THE STATEMENTS FOR DRAWING THE YELLOW CIRCLE
        # (use character_row, character_col)
        
    def handle_event(event):
        global character_row, character_col
        # ADD THE EVENT PROCESSING STATEMENTS HERE
        
    pygamebg.frame_loop(30, new_frame, handle_event)


.. questionnote::

    **Detyrë - bëj një labirint** 
    
    Shkruaj një program që bën një labirint. Korniza e kuqe duhet të kontrollohet duke përdorur shigjetat, dhe shtypja e spacebar duhet të ndryshojë ngjyrën e një kutie (nga e zeza në e bardhë dhe anasjelltas).
    
Kur të kryeni detyrën, provoni si më poshtë:

- klikoni në butonin "Luaj detyrën" (këtë herë programi i shembullit bën më shumë nga sa kërkuam prej jush)
- bëni labirint ashtu siç dëshironi
- shtypni *S* për fillimin dhe shikimin
- shtypni *P* për të aktivizuar dhe fikur modalitetin e pauzës, domethënë për të ndaluar ose rifilluar kërkimin

labirint
    
.. commented out

    Here it would be ideal if the students could not try the search before solving the task

.. activecode:: PyGame__interact_labyrinth
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includehsrc: src/PyGame/3_Interaction/3e_Keyboard_events/labyrinth_edit_and_search.py
    
    import pygame as pg, pygamebg, random
    a = 50 # square size
    num_rows = 12
    num_cols = 20
    (width, height) = (num_cols * a, num_rows * a)
    canvas = pygamebg.open_window(width, height, "Maze")

    def new_frame():
        canvas.fill(pg.Color('white')) # paint background
        for row in range(num_rows):
            for col in range(num_cols):
                if board[row][col] == 1: # wall
                    pg.draw.rect(canvas, pg.Color('black'), (col * a, row * a, a, a))

        # frame
        pg.draw.rect(canvas, pg.Color('red'), (frame_col * a, frame_row * a, a, a), 3)
        
    def handle_event(event):
        global board, frame_row, frame_col
        
        # ADD STATEMENTS FOR KEYSTROKE PROCESSING HERE
        # (arrow keys and space bar should be covered)

    board = []
    for j in range(num_rows):
        board.append([])
        for i in range(num_cols):
            board[-1].append(random.randint(0, 1))
            
    (frame_row, frame_col) = (0, 0)
    pygamebg.frame_loop(10, new_frame, handle_event)
            

Bonus - një praktikë programi shkrimi
'''''''''''''''''''''''''''''''''''''''

Programi më poshtë ka për qëllim praktikën e shkrimit. Programi është i gjatë, por duhet të jeni në gjendje të kuptoni një pjesë të madhe të tij.

Ju mund të dëshironi (pa detyrim) ta përshtatni programin me nevojat tuaja, veçanërisht në fillim. Për shembull:

- për të ngadalësuar (ose më vonë përshpejtimin) rënien e shkronjave
- të mos humbasësh pikë kur gabon
- kur zotëroni shkronjat që bien të parat, për t'i hequr ato nga lista e letrave për të praktikuar
- për të ndryshuar grupin e karaktereve në rënie në numra dhe vetëm shenjat e funksionimit (nëse doni të praktikoni të shtypni vetëm në tastierën numerike në anën e djathtë)
- të mbani shtypur spacebar dhe të fshini shkronjën më të ulët (me paksa zvogëlimin e rezultatit)

ose gjithçka tjetër që mund të mendoni.
    
Kur të keni kohë, ju inkurajmë të përpiqeni të merrni sa më shumë rezultate (pa bërë hile)..

.. activecode:: PyGame__interact_typing_tutor
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src/PyGame/3_Interaction/3e_Keyboard_events/typing_tutor.py
