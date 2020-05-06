Afishimi i imazheve të gatshme - detyra
------------------------------------------

Mësuam si të shfaqim një imazh të gatshëm në mënyrë që këndi i sipërm i saj i majtë të jetë në një pozicion të caktuar në ekran. Në disa situata, pozicioni i këndit të sipërm të majtë të figurës nuk do të jetë i njohur për ne, por do të duhet të llogaritet. Në raste të tilla, mund të jetë e nevojshme të njihni gjerësinë dhe lartësinë e figurës. Në librarinë e PyGame për figurën ``im``, gjerësia dhe lartësia e kësaj figure jepen përkatësisht ``im.get_width ()`` dhe ``im.get_height ()``.

Shporta
'''''''

Përfundoni programin e mëposhtëm për të marrë figurën si në shembull. Pozicionet e pemëve janë dhënë, dhe një shportë duhet të vizatohet pranë çdo peme në mënyrë që qoshet e poshtme të djathtë të shportës dhe imazhet e pemëve të mbivendosen.

Për të përfunduar këtë detyrë, duhet të llogaritni për secilën shportë të vizatuar pozicionin e këndit të tij të sipërm të majtë, i cili mund të bëhet duke filluar nga koordinatat e këndit të sipërm të majtë të pemës, duke përdorur gjerësitë dhe lartësitë e të dy imazheve.

.. image:: ../../_images/tree.png
   :width: 50px

.. image:: ../../_images/apple_small.png
   :width: 50px

.. image:: ../../_images/basket.png
   :width: 50px

.. activecode:: PyGame__pictures_baskets1
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\9_UsingImages\trees_baskets.py

    tree_image = pg.image.load("tree.png")  # image of a tree
    basket_image = pg.image.load("basket.png")  # image of a basket
    tree_positions = ((200, 70), (120, 150), (240, 290), (550, 170), (400, 200))


Kap mollët
''''''''''''''

Përfundoni programin e mëposhtëm për të marrë figurën si në shembull. Zgjidhja për këtë detyrë merret duke bashkangjitur programin e mëparshëm - kopjoni atë dhe shtoni mollë në pemë dhe shporta.

.. activecode:: PyGame__pictures_baskets_apples
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\9_UsingImages\trees_apples_baskets.py

    tree_image = pg.image.load("tree.png")  # image of a tree
    apple_image = pg.image.load("apple_small.png")  # image of an apple
    basket_image = pg.image.load("basket.png")  # image of a basket
    apples_on_tree_positions = ((43,191), (61, 158), (124, 145), (134, 175), (160, 180))
    apples_in_basket_positions = ((15, 38), (60, 41), (22, 43), (49, 45), (34, 48))
    tree_positions = ((200, 70), (120, 150), (240, 290), (550, 170), (400, 200))



Kuti
'''''

.. questionnote:: 

    Shkruaj programet që përdorin imazhin e një kutie të treguar më poshtë,

    .. image:: ../../_images/PyGame/box.png
        :width: 200px
        :align: center 

    dhe formoni imazhe si në shembuj (përdorni butonin "Luaj detyrën" në secilën detyrë).
      
 Koordinatat e figurës, domethënë, këndi i sipërm i saj i majtë për kutinë e majtë janë (60, 400) dhe për kutinë më të lartë janë (420, 115)

Nga të dhënat dhe imazhet e dhëna është e mundur të përcaktohen seritë *x* dhe *y* të koordinatave të figurës së secilës kuti në secilin shembull. Rendi i shfaqjes së fotove të kutisë gjithashtu duhet të merret parasysh këtu.

Për të kuptuar më mirë sesi mund të merren të njëjtën seri numrash (për shembull, 10, 15, 20, 25, 30) në dy rende të ndryshme, dhe çfarë tjetër për të kërkuar, përgjigjuni pyetjes mbështetëse.

.. dragndrop:: console__pictures_quiz_series_negative_step
    :feedback: Provo përsëri.
    :match_1: 10, 15, 20, 25, 30 ||| for x in range(10, 35, 5)
    :match_2: 30, 25, 20, 15, 10 ||| for x in range(30, 5, -5)
    :match_3: empty series ||| for x in range(30, 10, 5)
    :match_4: 5, 15, 25 ||| for x in range(5, 35, 10)

    Përputhen një seri numrash me deklaratat që i gjenerojnë ato.

.. activecode:: PyGame__pictures_boxes1
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\9_UsingImages\boxes1.py

.. activecode:: PyGame__pictures_boxes2
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\9_UsingImages\boxes2.py

.. activecode:: PyGame__pictures_boxes3
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\9_UsingImages\boxes3.py

