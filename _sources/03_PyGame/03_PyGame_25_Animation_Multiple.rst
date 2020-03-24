Lëvizja e objekteve të shumta
-----------------------

Deri më tani, kemi bërë animacione në të cilat lëviznin objekte të ndryshme (makina, topi i bilardos, aeroplan, teksti), por në secilën prej këtyre programeve kishte vetëm një objekt lëvizës. Për variablat globale që përshkruajnë skenën kemi përdorur koordinatat e atij objekti në lëvizje, dhe nganjëherë kemi përdorur edhe vlera të tjera, siç janë zhvendosja, drejtimi i lëvizjes etj.

Lëvizja e objekteve të shumta nuk është thelbësisht e ndryshme nga lëvizja e një objekti të vetëm - thjesht do të na duhet të gjurmojmë vlerat që përshkruajnë lëvizjen për të gjithë objektet. Për shembull, ne mund të përfaqësojmë secilin objekt me një tufë vlerash që e përshkruajnë atë, dhe t'i mbajmë të gjitha tupujt e tillë në një listë.

Balls
'''''

Në shembullin e mëposhtëm do të shohim lëvizje të animuar të disa topave. Secila top përfaqësohet nga një :math: `(x, y, dx, dy, r, ngjyra)` tuple, ku :math:`x,y` janë koordinatat e qendrës së topit, :math:`dx,dy` janë zhvendosjet e topit për koordinatë, :math:`r` është rrezja, dhe :math:`color` është ngjyra e topit. Të gjitha tuples e tilla vendosen në listë *topat*.

Kur shpaketoni një tufë nga një element i listës (komanda ``x, y, dx, dy, r, ngjyra = balls [i]``), si dhe kur e ktheni atë në listë (komanda ``balls [i] = (x, y, dx, dy, r, color)``), duhet të kemi parasysh rendin e variablave.

Në shembull, ne përdorim modulin ``random`` për të krijuar topa në mënyrë që të marrim seleksionime të rastësishme (të importuara duke përdorur komandën *import*). Funksioni ``random.randint(a, b)`` kthen një numër të plotë të rastit ndërmjet *a* dhe *b* (përfshirë kufijtë), dhe funksioni ``rastësor.choice (a)`` kthen një element të rastit nga mbledhja *a*.

.. activecode:: PyGame__anim_balls_bouncing
    :nocodelens:
    :modaloutput:
    :includesrc: src/PyGame/2_Animation/2e_Anim_Multiple/balls_bouncing.py

Nëse e krahasojmë këtë program me animacionin e lëvizjes së një bilardo, do të vërejmë një ngjashmëri të madhe. Funksioni *new_frame* është në thelb i ndryshëm vetëm në atë që tani të gjitha veprimet (lëvizja, kërcimi, vizatimi) bëhen në një cikël, pasi ato duhet të bëhen për secilën top. Vendosja e gjendjes fillestare është gjithashtu disi më e ndërlikuar, pasi ka më shumë objekte dhe ne ruajmë të dhëna të shumta për secilën prej tyre, dhe përdorim edhe zgjedhje të rastësishme.

~~~~

Në shembullin e mëparshëm, të gjitha objektet (topat) janë të pranishëm që nga fillimi deri në fund të programit. Ka situata kur duam që disa objekte të pushojnë së ekzistuari gjatë ekzekutimit të programit, ose të shfaqen disa objekte të reja (ose të dyja). Në raste të tilla, ne mund të përdorim një listë ndihmëse në funksionin *new_frame* në të cilin do të vendosim vlera që përshkruajnë gjendjen e re. Një sekuencë tipike e aktiviteteve është si më poshtë:

- krijoni një listë të re bosh në fillimin e funksionit *new_frame*
- ne kalojmë nëpër listën e tuples ekzistuese, i ndryshojmë ato dhe shtojmë ato që ende duhen në listën e re
- nëse është e nevojshme, plotësoni listën me tuples të reja
- së fundi, ne azhornojmë listën globale duke vendosur vlera nga lista e re, ndihmëse

Le të shohim një shembull.

Yjet
''''''

Në këtë shembull, ne simulojmë lëvizjen nëpër hapësirë. Yjet që hasim përfaqësohen me rrathë të bardhë dhe përcaktohen nga pozicioni dhe rrezja e tyre.

Për secilën kornizë, ne llogaritim një listë të re ndihmëse që përshkruan gjendjen tjetër. Ne i lëvizim yjet duke ndjekur një rregull, dhe kopjojmë ato që nuk e kanë lënë plotësisht dritaren në listën tjetër. Pas përpunimit të yjeve ekzistues, ne shtojmë yje të rinj në listën tjetër shtetërore në mënyrë që numri i përgjithshëm i yjeve të mos ulet. Më në fund, ne i lëvizim të gjitha yjet në listën globale në mënyrë që të mund të llogarisim kornizën tjetër më vonë.


Detyra
'''''

.. questionnote::

    **Flokë dëbore:** Përfundoni programin në mënyrë që të funksionojë siç tregohet në shembullin (butoni "Luaj detyrën").
    
     Çdo fletë dëbore përshkruhet vetëm me dy numra, koordinatat e tij, kështu që tufat që do të përdorim do të jenë në të vërtetë bashkë :math:`(x, y)`.
    
     Flokët e dëborës bien 1 pixel në një kohë, dhe ato që dalin nga dritarja zëvendësohen me dëborë të reja. Formimi i një gjendje të re është i ngjashëm me atë të programit "yje", vetëm rregullat për lëvizjen e dëborës janë më të thjeshta.
    
     Fijet e dëborës në grupin fillestar zgjidhen kudo në dritare, dhe ato që shtohen më vonë, zgjidhen diku në skajin e sipërm të dritares.
    
.. image:: ../../_images/snowflake.png
   :width: 50px
    
.. activecode:: PyGame__anim_snowflakes
    :nocodelens:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/2_Animation/2e_Anim_Multiple/snowflakes.py

    import random, pygame as pg, pygamebg
    (width, height) = (800, 400)
    canvas = pygamebg.open_window(width, height, "Snowflakes")

    snowflake_image = pg.image.load("snowflake.png")  # a snowflake image
    snowflake_height = snowflake_image.get_height()
    num_flakes = 10 # total number of the snowflakes


.. questionnote::

    **Topat në dalje:** Kopjoni programin e parë (topat) këtu, dhe modifikoni atë në mënyrë që topat të mos kërcejnë, por vazhdoni të largoheni, dhe ato që shkëputen zëvendësohen me topa të rinj. Ky program është një kombinim i dy shembujve të dhënë (topa dhe yje), kështu që përpiquni të përdorni pjesë nga të dyja këto programe.

.. activecode:: PyGame__anim_balls_passing
    :nocodelens:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/2_Animation/2e_Anim_Multiple/balls_passing.py


.. questionnote::

    **Tekst rrëshqitës** Provoni programin dhe përpiquni të kuptoni se si funksionon. Provoni të ndryshoni diçka në program (teksti që shfaqet, ngjyra në të cilën po shfaqet teksti, shpejtësia me të cilën lëviz teksti ose ndonjë detaj tjetër).
    
     Sfida: Përpiquni të modifikoni programin në mënyrë që teksti të rrëshqasë në vend të lart.

.. activecode:: PyGame__anim_gliding_text
    :nocodelens:
    :modaloutput:
    :includesrc: src/PyGame/2_Animation/2e_Anim_Multiple/gliding_text.py
