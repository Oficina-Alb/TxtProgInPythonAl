Vizatimi i drejtkëndëshave, eklipse dhe rrathëve
-----------------------------------------

Të gjitha funksionet e vizatimit në bibliotekën e PyGame fillojnë me ``pg.pull`. Në varësi të asaj forme që duam të vizatojmë, ne i quajmë funksione të ndryshme. Në shpjegimet që vijojnë, kuptimi i parametrave është:

- Parametri *canvas* është zona në të cilën vizatojmë. Në këtë udhëzues, programet do të kenë tashmë një variabël të formuar (më saktësisht objekt) *canvas*, e marrë si rezultat i një thirrje të funksionit ``pygamebg.open_window``.
- Parametri *color* është ngjyra që ne përdorim për të vizatuar. Siç u tha më herët, një ngjyrë mund të specifikohet me emrin e saj (për shembull: kodi: `pg.Color ("black")`), ose si një tuple ose një listë e 3 elementeve (për shembull: kodi: `[ 255, 0, 0] `për të kuqe).
- Parametri *drejtkëndësh* është një tupë ose një listë me katër elementë: matematikë: `(x, y, w, h)` ose: matematikë: `[x, y, w, h]`, që përshkruan një drejtkëndësh, siç u shpjegua më herët (koordinatat e kulmës së sipërme të majtë, gjerësia dhe lartësia e drejtkëndëshit).
- Parametri *center* paraqet një pikë. Siç u përmend më herët, një pikë mund të specifikohet si një tuple (ose listë) e 2 elementeve, të cilat përfaqësojnë koordinatat e pikës në dritaren në të cilën ne vizatojmë.
- Parametri *thickness* është trashësia e linjave që përdorim për të vizatuar. Në funksionet që shpjegojmë këtu, ky parametër është opsional dhe mund të harrohet.

Tani do të shohim përshkrime më të hollësishme të funksioneve për të vizatuar drejtkëndësha, eklipse dhe rrathët. Një shembull i shkurtër i një ose dy rreshtave të kodit jepet pas secilit përshkrim të funksionit. Ju mund të ekzekutoni secilën nga këto shembuj duke e kopjuar atë në programin më poshtë (i cili tani nuk vizaton asgjë). Fotografitë që pasojnë shembujt janë marrë në të njëjtën mënyrë.

.. activecode:: pygame__drawing_primirives_def
    :nocodelens:
    :modaloutput: 

    import pygame as pg, pygamebg
    canvas = pygamebg.open_window(200, 200, "Pygame")

    canvas.fill(pg.Color("gray"))

    pygamebg.wait_loop()

Vizato një drejtkëndësh
'''''''''''''''''''

Për të vizatuar një drejtkëndësh ne përdorim funksionin ``pg.draw.rect``, i cili ka dy forma:

.. code::

    pg.draw.rect(canvas, color, rectangle, thickness)
    pg.draw.rect(canvas, color, rectangle)

Ne përdorim formularin pa parametrin *thickness* kur duam që brendësia e drejtkëndëshit të mbushet edhe me ngjyrën e treguar.

Për shembull, e para nga dy deklarimet e mëposhtme do të thotë:

- vizatoni një drejtkëndësh (funksioni *rect*)
- pikturojeni të zezë (parametri (0, 0, 0) specifikon ngjyrën e zezë)
- Kulmi i majës së sipërme të drejtkëndëshit ka koordinata (40, 80)
- gjerësia e drejtkëndëshit është 50 dhe lartësia 30 piksele
- vetëm korniza e drejtkëndëshit duhet të vizatohet dhe linjat duhet të jenë të trasha 3 pixel

Deklarimi e dytë do të thotë:

- vizatoni një drejtkëndësh (funksioni *rect*)
- pikturojeni atë të zezë (parametri pg.Color ("black" gjithashtu specifikon ngjyrën e zezë)
- Kulmi i majës së sipërme të drejtkëndëshit ka koordinata (140, 80)
- drejtkëndëshi do të jetë 20 piksel i gjerë dhe i lartë, kështu që në të vërtetë do të jetë një katror
- Sheshi do të mbushet me ngjyra pasi që nuk ka asnjë parametër të trashësisë

.. activecode:: pygame__drawing_rectangles_def
    :passivecode: true
    
    pg.draw.rect(canvas, (0, 0, 0), (40, 80, 50, 30), 3)
    pg.draw.rect(canvas, pg.Color("black"), (140, 80, 20, 20))

.. image:: ../../_images/PyGame/drawing_rectangles.png
   :width: 200px   
   :align: center 

Vizatimi i një elipsi
''''''''''''''''''

Për të vizatuar një elips, p[rdorni funksionin``pg.draw.ellipse``, me apo pa parametrin e trashesisë:

.. code::

    pg.draw.ellipse(canvas, color, rectangle, thickness)
    pg.draw.ellipse(canvas, color, rectangle)

Parametri *retrangle* përfaqëson drejtkëndëshin në të cilin është shkruar elipsi, dhe parametrat e tjerë kanë të njëjtin kuptim si më parë. Nëse kemi nevojë për të, ne mund të llogarisim qendrën dhe gjysëm boshtet kryesore dhe të vogla të elipsës duke përdorur tuple: matematikë: `(x, y, w, h)` ose listën :math:`[x, y, w, h] `që përcakton drejtkëndëshin. Koordinatat e qendrës së drejtkëndëshit, i cili është gjithashtu qendra e elipsit, janë :math:`(x + w / 2, y + h / 2)`, dhe gjysmë-boshtet kryesore dhe të vogla të elipsit janë :math:`w / 2` dhe: matematikë:` h / 2`. Kështu, për shembull, deklarimi:

.. activecode:: pygame__drawing_ellipse_def
    :passivecode: true

    pg.draw.ellipse(canvas, pg.Color("yellow"), (100, 160, 60, 40))

vizaton një elips të verdhë të mbushur. Qendra e elipsit është qendra e drejtkëndëshit të specifikuar, e cila është në pikën (130, 180). Gjendja gjysmë-boshtore horizontale e elipsit është e gjatë 30 piksele, dhe 20 vertikale.

.. image:: ../../_images/PyGame/drawing_ellipse.png
   :width: 200px   
   :align: center 

Viato një rreth
''''''''''''''''

Përdor funksionin ``pg.draw.circle`` për të vizatuar një rreth, me ose pa parameter trashësie:

.. code::

    pg.draw.circle(canvas, color, center, radius, thickness)
    pg.draw.circle(canvas, color, center, radius)

Parametri *center* është një pikë që përfaqëson qendrën e rrethit, dhe parametri *raduis* është një numër që përfaqëson rrezen e rrethit në pixel. Për shembull, thënia e mëposhtme vizaton një rreth të kuq, 3 pixel të trashë, me rreze 50 pixel, qendra e të cilit është në pikën (100, 100):

.. activecode:: pygame__drawing_circle_def
    :passivecode: true

    pg.draw.circle(canvas, pg.Color("red"), (100, 100), 50, 3)

.. image:: ../../_images/PyGame/drawing_circle.png
   :width: 200px   
   :align: center 

Nëse parametri i fundit (gjerësia e goditjes 3) do të ishte zhdukur, brendësia e rrethit do të ishte gjithashtu e kuqe.

Vizatimi i drejtkëndëshave, elipsave dhe rrathëve - pyetje
''''''''''''''''''''''''''''''''''''''''''''''''''''

Kontrolloni sa kuptoni dhe mbani mend për këto funksione vizatimi:

.. mchoice:: pygame__drawing_quiz_circle_arglist
   :multiple_answers:
   :answer_a: Koordinatat e kulm-majës së sipërme
   :answer_b: Rrezja
   :answer_c: Koordinatat e qendrës
   :answer_d: GJerësia dhe gjtësia
   :answer_e: Ngjyra
   :correct: b, c, e
   :feedback_a: Koordinatat e kulmit të sipërm të majtë specifikohen kur vizatoni një elips ose një drejtkëndësh
   :feedback_b: Saktë
   :feedback_c: Saktë 
   :feedback_d: Koordinatat e kulmit të sipërm të majtë specifikohen kur vizatoni një elips ose një drejtkëndësh...
   :feedback_e: Saktë

   Çfarë duhet të specifikohet kur vizatoni një rreth?

.. mchoice:: pygame__drawing_quiz_circle_right_args
   :answer_a: pg.draw.circle(canvas, color, 100, 100, 30, 5)
   :answer_b: pg.draw.circle(canvas, color, (100, 100), 30, 5)
   :answer_c: pg.draw.circle(canvas, color, (100, 100, 30, 5))
   :answer_d: pg.draw.circle(canvas, color, (100, 100), (30, 5))
   :correct: b
   :feedback_a: Provo përsëri
   :feedback_b: Saktë
   :feedback_c: Provo përsëri
   :feedback_d: Provo përsëri

   Për të vizatuar një rreth me qendër në pikën :math:`(100, 100)`, rrezja e së cilës është :math:`30` piksele, duke përdorur linjën :math:` 5` pixel të gjerë, cili funksion i thirrjes duhet të bëhet?

.. mchoice:: pygame__drawing_quiz_circle_opt_arg
   :answer_a: kjo e fundit vizaton një elips, boshtet gjysmë të mëdha dhe gjysmë të vogla të së cilës janë të barabarta r dhe 1.
   :answer_b: kjo e fundit mbush brendësinë e rrethit me ngjyra.
   :answer_c: i pari vizaton një disk (rrethi të mbushur), dhe i dyti një vijë rrethore.
   :answer_d: i pari vizaton një vijë rrethore, ndërsa i dyti një disk (rrethi i mbushur).
   :correct: c
   :feedback_a: Provo përsëri
   :feedback_b: Provo përsëri
   :feedback_c: Saktë
   :feedback_d: Provo përsëri

   Dallimi midis `pg. pull.circle (canvas, color, (cx, cy), r)` dhe `pg. pull.circle (canvas, color, (cx, cy), r, 1)" është se:

.. mchoice:: pygame__drawing_quiz_rect_args_1
   :answer_a: Koordinatat vertikale majtas
   :answer_b: Gjerësia e goditjes
   :answer_c: Gjerësi
   :answer_d: Gjatësi
   :answer_e: Koordinatat e qendrës
   :correct: e
   :feedback_a: Provo përsëri
   :feedback_b: Provo përsëri
   :feedback_c: Provo përsëri
   :feedback_d: Provo përsëri
   :feedback_e: Saktë

   Cfarë nuk specifikohet kur vizatoni një drejtkëndësh?

.. mchoice:: pygame__drawing_quiz_rect_args_2
   :answer_a: pg.draw.rect(canvas, color, 100, 100, 30, 50)
   :answer_b: pg.draw.rect(canvas, color, (100, 100), (30, 50))
   :answer_c: pg.draw.rect(canvas, color, (100, 100), 30, 50)
   :answer_d: pg.draw.rect(canvas, color, (100, 100, 30, 50))
   :correct: d
   :feedback_a: Provo përsëri
   :feedback_b: Provo përsëri
   :feedback_c: Provo përsëri
   :feedback_d: Saktë

   Për të vizatuar një drejtkëndësh, kulmi i majtë i të cilit është në pikë
    :math:`(100, 100)`, math: `30` pixel i gjerë dhe :math:` 50`
    pixel të lartë, cili thirrje funksion duhet të bëhet?

.. mchoice::  pygame__drawing_quiz_rect_args_3
   :answer_a: pg.draw.rect(canvas, color, (80, 80, 50, 80))
   :answer_b: pg.draw.rect(canvas, color, (80, 80), (130, 160))
   :answer_c: pg.draw.rect(canvas, color, (80, 80, 130, 160))
   :answer_d: pg.draw.rect(canvas, color, (80, 80), (50, 80))
   :correct: a
   :feedback_a: Saktë
   :feedback_b: Provo përsëri
   :feedback_c: Provo përsëri
   :feedback_d: Provo përsëri

   Për të vizatuar një drejtkëndësh, kulmi i majtë i të cilit është në pikë
   :math:`(80, 80)`, dhe kulmi i djathte poshtë
   :math:`(130, 160)`, cilin thirrje funksioni duhet të bëhet:

Vizatimi sipas udhëzimeve
'''''''''''''''''''''''

Në detyrat e mëposhtme, mund të shihni se çfarë programi juaj duhet të vizatojë duke klikuar butonin "Luaj detyrën". Për t'ju siguruar informacionin e nevojshëm për të shkruar deklarimet që ju nevojiten, jepen gjithashtu udhëzime të hollësishme me përshkrime të parametrave.

Mbani në mend se para se të vizatoni duhet të pikturoni sfondin me ngjyrën e duhur, për të cilën përdorni thënien ``canvas.fill (pg.Color (...))`` (në vend të pikave specifikoni një ngjyrë).

.. questionnote::

    **Detyrë - objektiv:** 
    
    Vizatoni një objektiv në një sfond të bardhë duke përdorur tre rrathë të mbushura. Qendrat e të tre rrathëve duhet të jenë në qendër të dritares dhe të gjitha rrathët duhet të jenë të mbushura me ngjyra. Së pari, vizatoni një rreth të kuq me rreze 100, pastaj një blu me rreze 75, dhe më pas një rreth jeshil me rreze 50 pixel.
    
Cfarë mendoni, a mund të tërhiqen këto rrathë në një renditje tjetër? Nëse nuk jeni të sigurt se çfarë do të ndodhte nëse detyra do ndryshonte, provojeni.

.. activecode:: PyGame__drawing_target
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :playtask:
   :includexsrc: src/PyGame/1_Drawing/1_BasicExamples/target.py

.. questionnote::

    **Detyrë - rosa:** 
    
    Në një sfond të gjelbër, vizatoni një rosë si një karakter vizatimor. Vizatimi përbëhet nga pjesët e mëposhtme:
    
    - Koka: një elitë e verdhë e mbushur, e gdhendur në një drejtkëndësh 320 x 300 pixel, me kulm të sipërm të majtë në pikën (40, 50)
    - Kufiri i kokës: një elitë e zezë që kornizon elipsën e mëparshme me një vijë gjerësi 1
    - Syri i majtë: një elips i mbushur me të zezë, i gdhendur në një drejtkëndësh me pixel 40 x 40 me kulm të sipërm të majtë në pikën (130, 130)
    - Syri i djathtë: një elips i mbushur me të zezë, i gdhendur në një drejtkëndësh me pixel 40 x 40, me kulm të sipërm të majtë në pikën (280, 120)
    - Goja (sqepi): një elips i mbushur me të kuqe, të gdhendur në një drejtkëndësh me pixel 120 x 140, me kulm të sipërm të majtë në pikën (200, 170)
    - Kufiri i gojës: një elitë e zezë që kornizon elipsën e mëparshme me një vijë gjerësi 1

Këtu kemi më shumë liri me rendin e vizatimit, por prapë na duhet të ndjekim njëfarë rendi. Mundohuni të shpjegoni se cilat pjesë të figurës duhet të vizatohen saktësisht në këtë renditje, dhe cilat nuk duhet.

Vini re se sytë janë të gdhendur në drejtkëndësha që janë në të vërtetë katrorë. Si (falë kësaj) mund t'i vizatojmë të njëjtat sy në një mënyrë tjetër?

.. activecode:: PyGame__drawing_duckling
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :playtask:
   :includexsrc: src/PyGame/1_Drawing/1_BasicExamples/duckling.py

