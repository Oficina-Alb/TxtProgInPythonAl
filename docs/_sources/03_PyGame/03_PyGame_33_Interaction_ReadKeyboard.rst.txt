Leximi i tastierës
--------------------

Përvetësimi i informacionit rreth tasteve në tastierë është shumë i ngjashëm me leximin e butonave të mouse. Funksioni ``pg.key.get_pressed()`` kthen një tuple, elementët e të cilit përdoren si vlera logjike, duke treguar për secilin tast në tastierë nëse aktualisht është duke u shtypur apo jo.

Për shkak se tastiera ka shumë më shumë çelësa se mouse, përdorimi i indekseve 0, 1, 2, etj për disa çelësa do të ishte jopraktik. Për të mos ditur se cili indeks në tuple korrespondon me cilin çelës, libraria e PyGame përmban konstanta të emërtuara që ne përdorim si indeks. Për shembull, konstantet ``pg.K_LEFT``, ``pg.K_RIGHT``, ``pg.K_UP``, ``pg.K_DOWN`` lidhen me shigjetat e përdorura shpesh. Për butonin e hapësirës është ``pg.K_SPACE``, ndërsa shkronjat, për shembull *a*, *b*, *c* kanë konstantet korrespondente ``pg.K_a``, ``pg.K_b``, ``pg .K_c`` etj. Listën e plotë e gjeni këtu `here <https://www.pygame.org/docs/ref/key.html>`__ .
 
Examples and tasks
'''''''''''''''''''

.. questionnote::
 
    **Shembull - Anije kozmike** Në këtë shembull, ne kemi një imazh të një anije kozmike, të cilën e lëvizim majtas dhe djathtas në përputhje me tastet e shigjetës së shtypur. Përveç kësaj, ne mund të zjarrmë nga anija duke shtypur tastin e shiritit hapësinor.
    
Së pari, kushtojini vëmendje pjesës së theksuar të kodit me një sfond më të lehtë (linjat 23-37). Kjo pjesë është e re këtu, dhe gjithashtu është komentuar më hollësisht në vetë kodin.

Pjesa tjetër e programit është thjesht gjallërim i objekteve të shumta, një teknikë e njohur që nga më parë.

.. image:: ../../_images/spaceship.png
   :width: 50px

.. activecode:: PyGame__interact_spaceship_arrow_keys
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src/PyGame/3_Interaction/3c_Keyboard_read/spaceship_arrow_keys.py

Pra, pasi të lexojmë statusin e të gjithë çelësave dhe ta vendosim në tuple *të shtypur*, ne thjesht mund të kontrollojmë statusin e çelësave që ne jemi të interesuar të përdorim deklaratën *if*.


.. questionnote::

 **Detyra - lundrimi:**
    
Plotësoni programin e mëposhtëm në mënyrë që 4 çelësat e shigjetave të kontrollojnë rrethin e verdhë, si në shembull. Rrethi nuk duhet të lëvizë nëse nuk shtypen shigjeta dhe lëvizin një piksel në drejtim të shigjetave që shtypen (shigjetat e kundërta anulojnë njëra-tjetrën jashtë).   

.. activecode:: PyGame__interact_navigtate1
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src/PyGame/3_Interaction/3c_Keyboard_read/navigtate1.py

        pressed = pg.key.get_pressed()
        if pressed[pg.K_LEFT] and (x > 0):
            x -= 1
            
        # COMPLETE THE PROGRAM



.. questionnote::

    **Detyrë - gjarpri:** 
    
    Plotësoni programin e mëposhtëm në mënyrë që shigjetat të mund të kontrollojnë një 'gjarpër' të përbërë nga disa sheshe, si në shembull.
    
     Variablat *d_row* dhe *d_col* tregojnë drejtimin e lëvizjes së gjarprit. Ndërsa nuk shtypen shigjeta, vlera e këtyre ndryshoreve nuk ndryshon dhe gjarpri vazhdon të lëvizë në të njëjtin drejtim. Detyra juaj është të shtoni komanda për leximin e statusit të tastierës dhe llogaritjen e vlerave të reja për *(d_row, d_col)* bazuar në shigjetat e shtypura, në mënyrë që lëvizja të vazhdojë në drejtimin e zgjedhur.

**Ndihme:** nëse koka e gjarprit ishte në katror *(row, col)*, në kornizën e re do të jetë në katror *(rresht + d_row, col + d_col)*. Kontrolloni nëse keni kuptuar se si duhet të caktoni vlera ndaj variablave *d_row*, *d_col* për secilin drejtim:

.. mchoice:: pygame__interact_quiz_direction
   :answer_a: Up
   :answer_b: Down
   :answer_c: Left
   :answer_d: Right
   :correct: c
   :feedback_a: No, values for up are (d_row, d_col) = (-1, 0)
   :feedback_b: No, values for down are (d_row, d_col) = (1, 0)
   :feedback_c: Saktë
   :feedback_d: No, values for right are (d_row, d_col) = (0, 1)

   Nëse variablat (d_row, d_col) janë lidhur me clerat (0, -1), në cilin drejtim vazhdon lëvizja?

.. activecode:: PyGame__interact_snake
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src/PyGame/3_Interaction/3c_Keyboard_read/snake.py
    
        # HERE CALCULATE THE DISPLACEMENT (d_row, d_col)
        # BASED ON THE KEYS PRESSED


Pyetje
'''''''''

Ndërsa ju përgjigjeni pyetjeve, kthehuni tek programi "gjarpri" sipas nevojës dhe kërkoni pjesët që duhet t'i përgjigjeni.

.. fillintheblank:: pygame__interact_quiz_snake_tablesize

    How many rows does the board have?

    - :40: Saktë!
      :[0-9]+: Look at the beginning of the program more carefully.
      :.*: The answer should be written in digits.

.. mchoice:: pygame__interact_quiz_snake_rowcol_to_xy
   :answer_a: x = row*a + a, y = col*a + a
   :answer_b: x = col*a + a, y = row*a + a
   :answer_c: x = row*a, y = col*a
   :answer_d: x = col*a, y = row*a
   :correct: d
   :feedback_a: Provo përsëri
   :feedback_b: Provo përsëri
   :feedback_c: Provo përsëri
   :feedback_d: Saktë

   Cilat janë koordinatat e këndit të sipërm të majtë të katrorit *(row, col)*?

.. mchoice:: pygame__interact_quiz_snake_head
   :multiple_answers:
   :answer_a: Në secilën listë kornizë 'gjarpri' shtrihet nga një element i ri që përfaqëson pozicionin e ri të kokës së gjarprit.
   :answer_b: Lista 'gjarpri' ka të njjtin numër elementësh në program.
   :answer_c: Një element që përfaqëson fundin e bishtit të gjarprit është hequr nga lista 'gjarpër' në secilën kornizë.
   :correct: b
   :feedback_a: Nuk ezkiston kjo komandë në program
   :feedback_b: Saktë
   :feedback_c: Nuk ezkiston kjo komandë në program

   Cilat fjali janë të vërteta?
    

.. commented out

    chase_and_avoid.py
