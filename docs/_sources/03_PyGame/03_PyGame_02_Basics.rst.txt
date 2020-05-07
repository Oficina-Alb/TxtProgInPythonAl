Shkrimi i një programi PyGame
================================

Struktura themelore e një programi PyGame
-------------------------------------------

Në mënyrë që programet që ne shkruajmë të përdorin librarinë (modulin) PyGame, gjëja e parë që duhet të bëjmë është të importojmë modulin PyGame në fillim të programit. Kjo na lejon të përdorim të gjitha funksionet dhe konstantet e përcaktuara në modulin PyGame.

Pas importimit të modulit por para thirrjes së funksioneve të tjera, çdo program që përdor librarinë PyGame duhet të bëjë disa hapa për inicializimin e bibliotekës, të specifikojë dimensionet e dritares në të cilën do të vizatojë programin, dhe të vendosë titullin e asaj dritare. Gjithashtu, ka disa hapa në fund të programit që do t'i tregojnë programit të presë derisa përdoruesi të klikojë në butonin mbyllës të dritares, dhe pas kësaj të mbyllë dritaren dhe të zhbllokojë bibliotekën PyGame.

Këto hapa në fillim dhe në fund të punës janë të njëjta ose shumë të ngjashme në secilin program. Për ta bërë më të lehtë për fillestarët të përdorin librarinë PyGame, do të përdorim gjithashtu një librari të vogël shtesë me emrin *PyGameBg*. Falë kësaj bibliotekë, në vend që të rendisni të gjitha hapat e nevojshëm, mjafton të futni modulin *pygamebg* në programin tonë (si dhe *pygame*), dhe më pas thirrni vetëm një funksion nga moduli *pygamebg* në fillim dhe një në fund të programit. Kjo i bën programet më të shkurtër dhe më të thjeshtë, duke na lejuar të përqëndrohemi në pjesën e programit që është specifik për detyrën në fjalë.

Ju gjithashtu mund të drejtoni programe duke përdorur bibliotekën *PyGameBg* në mjedisin tuaj të zhvillimit lokal (p.sh. *IDLE*). E tëra çfarë ju duhet të bëni është të instaloni bibliotekën *PyGameBg* në të njëjtën mënyrë si keni instaluar bibliotekën *PyGame*, d.m.th. duke shtypur ``pip3 install pygamebg`` në command line. Kur instaloni këtë librari, mund ta kopjoni programin e zgjedhur në redaktorin tuaj dhe ta ruani atë në kompjuterin tuaj. Pastaj mund të modifikoni programin sipas dëshirës, ​​të ruani versione të ndryshme të programit dhe t'i provoni duke ekzekutuar programin.

Ja se si duket një program PyGame që vizaton një segment të linjës së pjerrët dhe pret që përdoruesi të mbyllë dritaren.

.. activecode:: pygame__basics_first_example
    :nocodelens:
    :modaloutput: 

    import pygame as pg
    import pygamebg
    canvas = pygamebg.open_window(400, 400, "Pygame")

    canvas.fill(pg.Color("white"))
    pg.draw.line(canvas, pg.Color("black"), (100, 100), (300, 300), 5)

    pygamebg.wait_loop()


Le të kalojmë përmes deklaratave të këtij programi në mënyrë që të sqarojmë më hollësisht se çfarë bëjnë ata.

Së pari kemi një grup të deklaratave që do të duhet të paraqiten në fillim të secilit program:

- duke përdorur fjalinë ``import pygame as pg``, ne përfshijmë modulin *pygame* në programin tonë. Këtu ne përdorim një formë paksa të ndryshme të deklaratës *import* nga ajo që kemi përdorur më parë. Po ashtu, ne i japim modulit *pygame* një emër të shkurtuar, *pg*, dhe nga ajo pikë ne përdorim atë emër të shkurtuar në program si emrin e modulit. Mund të kishim vendosur thjesht ``import pygame`` pa asnjë ndryshim në funksionalitetin, por atëherë do të duhej të shkruanim *pygame.Color*, *pygame.draw.line*, etj në vend të *pg.color*, *pg.draw.line* dhe të ngjashme.
- duke përdorur fjalinë ``import pygamebg`` ne importojmë modulin *pygamebg* në programin tonë. Kjo deklarim mund të kombinohet me një të mëparshme për të marrë një thënie të vetme: `` import pygame as pg, pygamebg``, dhe ne shpesh do ta bëjmë këtë.
- Deklarimi ``canvas = pygamebg.open_window (400, 400, "Pygame")`` thërret funksionin ``open_window`` nga moduli ` pygamebg``, të cilin e kemi importuar në program. Ky funksion kryen të gjitha veprimet e nevojshme përgatitore që përmendëm më herët. Parametrat e funksionit janë gjerësia, lartësia dhe titulli i dritares që hapet duke e thirrur këtë funksion. Variabli *canvas* i kthyer nga ky funksion përdoret më vonë në program për të vizatuar në atë dritare.

Më poshtë është një grup i deklaratave që është i ndryshëm në secilin program dhe përcakton se çfarë bën në të vërtetë ai program i veçantë. Programi ynë i parë vizaton një vijë të zezë në një sfond të bardhë, dhe u arrit përmes kësaj pjese të programit:

- thënia ``canvas.fill (pg.color ("white"))`` pikturon dritaren e bardhë. Vizatimi shpesh fillon me këtë deklarim (mund të përdorim një ngjyrë tjetër)
- thënia ``pg. pull.line (canvas, pg.color ("black"), (100, 100), (300, 300), 5)`` vizaton segmentin e linjës.

deklarimet si kjo së shpejti do të shpjegohen në detaje, por nëse ndiheni të paduruar, mund të provoni të modifikoni vlerat e parametrave në program ose të shtoni deklarime të reja, të ngjashme dhe të zbuloni vetë se si funksionojnë këto funksione vizatimi.

Në fund të programit, ne thirrim një funksion tjetër nga moduli *pygamebg*: ``pygamebg.wait_loop ()``. Ky funksion përmban deklarim që lejojnë që vizatimi të shfaqet në dritare dhe ta mbaj dritaren të hapur derisa përdoruesi të klikojë në butonin e mbyllur. Pas mbylljes së dritares, funksioni çaktivizon të gjitha pjesët e përdorura të bibliotekës PyGame (i fik ato).

Të gjitha programet tona PyGame do të përfundojnë me një thirrje të funksionit ``pygamebg.wait_loop ()`` ose ndonjë funksion të ngjashëm me të. Pas ekzekutimit të këtij funksioni, programi mund të vazhdojë të funksionojë pa librarin[ *PyGame* në një dritare teksti nëse kërkohet.


Sistemi koordinativ
-----------------------

Koordinatat janë një term shumë i rëndësishëm për ne dhe ne do t'i hasim ato në pothuajse çdo program PyGame. Pozicioni i të gjitha objekteve (pikat, segmentet e linjës, rrathët, teksti, imazhet e importuara, etj.) Në dritare përcaktohet nga koordinatat e tyre në sistemin koordinativ të dritares.

Sistemi koordinativ i një dritareje është i ngjashëm, por ende pak i ndryshëm nga ai i përdorur në matematikë. Pozicioni i një pike përcaktohet nga një palë e porositur e koordinatave të saj në këtë rast gjithashtu (koordinata x, d.m.th abscissa dhe koordinata y, d.m.th. ordinojnë). Njësia e matjes është një pixel.

Në grafikat kompjuterike, origjina e një sistemi koordinativ është në këndin e sipërm të majtë të një dritareje. Koordinata :math:`x` rritet kur kalojmë në të djathtë (si në matematikë), por koordinoni :math:`y` zvogëlohet kur ngrihet lart, domethënë rritet kur ulemi poshtë, gjë që është e ndryshme nga e zakonshme sistemi koordinativ në matematikë. Le një pikë e dhënë të jetë :math:`A (5, 3)`. Nëse e lëviznim këtë pikë 1 piksel lart dhe mbajmë koordinatën e saj :math:`x`, atëherë koordinatat e reja të pikës :math:`A` do të ishin :math:`A (5, 2)`. Nëse lëvizim pikën :math:`A` 2 pixel nga pozicioni aktual, koordinatat e reja do të ishin :math:`A (5, 4)`. Pra, **koordinata e parë e pikës përcakton se sa larg është pika nga skaji i majtë i dritares**, dhe **koordinata e dytë, sa larg është pika nga skaji i sipërm i dritares**.


.. image:: ../../_images/PyGame/coordinate_system.png
   :width: 400px   
   :align: center 
      
Në gjuhën e programimit Python, një palë koordinata pikë mund të përfaqësohet ose nga një tufë dy elementësh ``(3, 5)``, ose nga një listë me dy elemente ``[[3, 5]``. Në shembullin e mëparshëm, dy pikat e fundit të segmentit të linjës u dhanë nga dy tupla dy elementësh (``(100, 100)`` dhe ``(300, 300)``).

.. activecode:: pygame__basics_coordinates
   :passivecode: true
   
   pg.draw.line(canvas, pg.Color("black"), (100, 100), (300, 300), 5)

Shpesh, duhet të specifikoni një drejtkëndësh, faqet e të cilit janë paralele me boshtet e koordinatave. Një drejtkëndësh i tillë përcaktohet duke përdorur një tuple ose një listë që përmban katër numra:: kodin: `(x, y, w, h)` ose: kodin: `[[x, y, w, h]`. Math: `x` dhe :math:` y` përfaqësojnë koordinatat e këndit të sipërm të majtë të drejtkëndëshit, dhe :math:`w` dhe :math:` h` përfaqësojnë gjerësinë dhe lartësinë e drejtkëndëshi në pixel. Për shembull, drejtkëndëshi në imazhin e mëposhtëm mund të specifikohet si :code: `pygame.Rect (2, 1, 4, 3)`, ose thjesht si :code:`(2, 1, 4, 3)` ose :code:`[[2, 1, 4, 3]`.

.. image:: ../../_images/PyGame/rect_coordinates.png
   :width: 400px   
   :align: center 

Programi i mëposhtëm mund t'ju ndihmojë të kuptoni koordinatat. Nisni programin duke klikuar në butonin "Luaj detyrën", pastaj lëvizni mouse dhe shikoni ndërsa koordinatat ndryshojnë. Dritarja që mouse po lëviz është me madhësi 300 herë 300 pixel. Vlerat e koordinatave *x* dhe *y* shfaqen si në shiritin e titullit të dritares ashtu edhe pranë treguesit të mouse. Shënimi që shfaqet pranë treguesit është në formën e një çifti të porositur, ashtu siç do të jetë në programet kur specifikojmë një pikë të vetme.

.. activecode:: pygame__basics_learn_coordinates
   :nocodelens:
   :modaloutput:
   :playtask:
   :includehsrc: src/PyGame/1_Drawing/1_BasicExamples/learn_coordinates.py

Testoni njohuritë tuaja për koordinatat përmes disa pyetjeve vijuese.
                 
.. image:: ../../_images/PyGame/pygame_quiz_coordinates.png
    :width: 300px
    :align: center
   
.. dragndrop:: pygame__basics_quiz_coordinates_circles
    :feedback: Provo përsëri!
    :match_1: red|||(30, 40)
    :match_2: green|||(50, 280)
    :match_3: blue|||(230, 20)
    :match_4: black|||(150, 170)

    Lidhni ngjyrën e rrethit me koordinatat e qendrës së tij (dimensionet e dritares janë 300 herë 300 pixel).

.. fillintheblank:: pygame__basics_quiz_coordinates_vindow_center

    Nëse dritarja është e gjerë 200 piksele dhe e lartë 300 piksele, cilat janë koordinatat e pikës së saj qendrore?

    - :\(100,[ ]*150\): Saktë!
      :\(100,[ ]*[0-9]+\): Llogaritni më me kujdes koordinatën y.
      :\([0-9]+,[ ]*150\): Llogaritni më shumë kujdes koordinatën x.
      :\([0-9]+,[ ]*[0-9]+\): Llogaritni me kujdes të dy koordinatat.
      :.*: Shkruajeni rezultatin si një palë e porositur.
   
.. mchoice:: pygame__basics_quiz_coordinates_dir
   :multiple_answers:  
   :answer_a: Koordinata x rritet nga e majta në të djathtë.
   :answer_b: Koordinata y zvogëlohet nga lart poshtë në ekran.
   :answer_c: Pikat në skajin e sipërm të ekranit kanë një koordinatë y të barabartë me 0.
   :answer_d: Pikat në skajin e djathtë të ekranit kanë një koordinatë x të barabartë me 0.
   :answer_e: Pika në këndin e poshtëm të djathtë të ekranit ka të dy koordinatat më të mëdha.
   :correct: a, c, e
   :feedback_a: Saktë.
   :feedback_b: Koordinata y rritet nga lart poshtë në ekran.
   :feedback_c: Saktë.
   :feedback_d: Pikat në skajin e djathtë të ekranit kanë koordinatën më të madhe x.
   :feedback_e: Saktë.
   
   Zgjidh përgjigjen e duhur.
   
.. dragndrop:: pygame__basics_quiz_coordinates_corners
   :feedback: Provo përsëri
   :match_1: top-left|||(0, 0)
   :match_2: top-right|||(w, 0)
   :match_3: bottom-left|||(0, h)
   :match_4: bottom-right|||(w, h)
   
   Nëse gjerësia e një dritare është `w` dhe lartësia është`h`, çiftoni qoshet e ekranit me koordinatat e tyre.


Specifikimi i ngjyrave
-----------------------

Sigurisht, kur vizatoni, mund të përdoren ngjyra të ndryshme. Ne mund të specifikojmë një ngjyrë me emrin e saj (në anglisht), të cilën e përcjellim si parametër në funksionin ``pg.Color``. Ju mund të përdorni ngjyrat duke përcjellë vargun e duhur: ``'black'``, për të zezën,``'white'``, për të bardhë, ``'gri'``, për gri,``'blue'``, për blu ``'green'`` për jeshilen,``'orange'`` për portokallin ``'yellow'`` për të verdhë, etj. Kujtojmë se vargjet specifikohen ose midis thonjëzave të vetme ose të dyfishtë (psh. "blu" dhe "blu" mund të përdoret në mënyrë të ndryshme). Për shembull, nëse e quani funksionin ``py.draw.line (canvas, pg.Color ('blue'), (0, 0), (200, 200), 3)`` një segment i linjës blu, 3 pixel i gjerë , koordinatat e pikave fundore të të cilave janë :math:`(0, 0)` dhe :math:`(200, 200)` do të shfaqet në dritare

Disa nga emrat e ngjyrave që përdoren zakonisht në programe janë:

========================   ============
``pg.Color("black")``      Black
``pg.Color("white")``      White
``pg.Color("red")``        Red
``pg.Color("green")``      Green
``pg.Color("blue")``       Blue
``pg.Color("cyan")``       Cyan
``pg.Color("magenta")``    Magenta
``pg.Color("yellow")``     Yellow
``pg.Color("orange")``     Orange
========================   ============

Luaj me ngjyrat në programin e mëposhtëm dhe përpiqu të ngjyrosësh dritaren në disa ose të gjitha këto ngjyra.

.. activecode:: pygame__basics_colors
   :nocodelens:
   :enablecopy:
   :modaloutput:

   # -*- acsection: general-init -*-
   import pygame as pg, pygamebg
   # start working with the PyGame library
   canvas = pygamebg.open_window(400, 400, "Color names")

   # -*- acsection: main -*-

   # painting the background
   canvas.fill(pg.Color("???"))
   
   # -*- acsection: after-main -*-
   # finishing work with the PyGame library
   pygamebg.wait_loop()
         
.. infonote::

    Një nga gabimet që bëhet shpesh kur shkruani programet e para të PyGame është të shkruani ``pg.color`` me shkronja të vogla kur specifikoni një ngjyrë, në vend që të kapitalizoni - ``pg.Color`. Kjo shkakton një gabim në mesazhin ``AttributeError: 'objekti nuk ka atribut color ngjyra’``
    
    Një gabim tjetër i zakonshëm nuk është të specifikoni emrin e ngjyrave nën thonjëza (për shembull, të specifikoni ``pg.Color(white)``). Atëherë gabimi tregon ``NameError: emri white nuk përcaktohet në mesazhin në rreshtin 8``.
  
Përveç këtyre ngjyrave, ka shumë të tjera që mund të përdorni. Numri i përgjithshëm i ngjyrave që ekzistojnë në kompjuter është shumë i madh, duke arritur në rreth 16 milion. Nga këto, ne mund të përmendim vetëm pak më shumë se 600 ngjyra të ndryshme (lista e plotë është në skedarin *colordict.py*, të cilin mund ta gjeni lehtësisht në Internet, dhe nëse e keni të instaluar PyGame, e keni atë në kompjuterin tuaj) gjithashtu).

Ne mund të specifikojmë të gjitha këto ngjyra të emërtuara, si dhe të gjitha të tjerat që nuk kanë emër, duke përdorur numra. I ashtuquajturi modeli me ngjyra *RGB* është më i përdoruri për këtë. Përkatësisht, në grafikat kompjuterike, çdo ngjyrë fitohet duke përzier një sasi të caktuar të kuqe, jeshile dhe blu, me emrat e të cilave emri *model RGB*. Për shembull, kombinimi i dritave të kuqe dhe jeshile prodhon një dritë të verdhë, duke kombinuar ngjyrën e kuqe dhe blu prodhon magjinë, dhe duke kombinuar blu dhe jeshil prodhon cian. Kombinimi i dritës së të tre ngjyrave kryesore rezulton në dritë të bardhë, ndërsa drita e zezë merret kur të tre dritat janë fikur. Drita gri fitohet duke përzier sasi të barabarta të dritës së kuqe, jeshile dhe blu.

.. image:: ../../_images/PyGame/RGB.png
   :align: center
   :width: 200px

Kjo do të thotë që ne mund të përshkruajmë një ngjyrë duke specifikuar tre numra (në këtë rast, numrat nga 0 në 255), të cilët përfaqësojnë sasinë e dritës me ngjyrë të kuqe, jeshile dhe blu, përkatësisht, në ngjyrën që ne përcaktojmë. Në gjuhën e programimit Python, ngjyra mund të përfaqësohet në formën e një tuple të rregulluar me tre elementë (p.sh. ``(123, 80, 56)``), ose një listë me tre elementë (p.sh. ``[123, 80 , 56]``). Ju mund të specifikoni tuple ose listë të drejtpërdrejtë si argument ngjyra, e një funksioni, ose mund ta ruani atë në një variabël dhe të përdorni emrin e ndryshueshëm më vonë. Për shembull, duke caktuar ``CYAN = (0, 255, 255)``, ne përcaktojmë ngjyrën cyan duke specifikuar sasitë e duhura të dritës së kuqe, jeshile dhe blu të përmbajtur në këtë ngjyrë (pasi është një përzierje e kaltër dhe jeshile nuk ka fare të kuqe, dhe përbërësit blu dhe jeshil janë në maksimum). Pas kësaj, ne mund ta përdorim këtë ngjyrë edhe në një thirrje funksioni (për shembull, `` canvas.fill (CYAN)``). Emrat e këtyre ndryshoreve nuk ka pse të kapitalizohen, por kjo është bërë praktikë e zakonshme për të shkruar programet e Python. Në programet që do të shihni më poshtë, do të hasni në përkufizime si kjo.

Një ngjyrë gjithashtu mund të specifikohet me katër numra, për shembull ``CYAN = (0, 255, 255, 10)``. Parametri i fundit, i katërt (gjithashtu në interval nga 0 deri në 255) përcakton transparencën e ngjyrës, d.m.th. ngjyra e cyanit e dhënë në këtë mënyrë është paksa transparente.

Le të përmbledhim vlerat RGB të disa ngjyrave të zakonshme.

===================        ========= 
``(255, 0, 0)``            red
``(0, 255, 0)``            green
``(0, 0, 255)``            blue
``(255, 255, 0)``          yellow
``(0, 255, 255)``          cyan
``(255, 0, 255)``          magenta
``(255, 255, 255)``        white
``(0, 0, 0)``              black
``(128, 128, 128)``        gray
``(255, 128, 0)``          orange
``(255, 128, 128)``        pink
===================        ========= 

Vini re se hijet e grisë janë të njohshme pasi sasitë e kuqe, jeshile dhe blu janë të barabarta në to. Sa më e vogël të jetë sasia, aq më e errët është hija dhe anasjelltas - sasi më të mëdha të barabarta të kuqe, jeshile dhe blu përfaqësojnë hije më të lehta të gri (bazuar në vlerën *RGB*, e zeza dhe e bardha mund të shihen si hija më e errët dhe më e lehtë e gri).

Në programin vijues, gjithashtu mund të provoni të specifikoni ngjyrat në formatin RGB. Përveç ngjyrosjes së dritares në disa ose të gjitha ngjyrat e listuara, mund të futni (ndonjë) treshe të tjera vlerash midis 0 dhe 255.

.. infonote:: 

    Kur zgjidhni ngjyrat që dëshironi të përdorni në programet tuaja, një mjet për zgjedhjen e ngjyrave mund t'ju ndihmojë. Ekziston një mjet si ai në shumë site (kërkoni për zgjedhësin e ngjyrave), ose mund të përdorni atë nga aplikacioni *Paint*. Mund ta provoni tani - zgjidhni një ngjyrë dhe kopjoni vlerat *R*, *G*, *B* në program.

.. activecode:: pygame__basics_colors_rgb
   :nocodelens:
   :enablecopy:
   :modaloutput:

   # -*- acsection: general-init -*-
   import pygame as pg, pygamebg

   # start working with the PyGame library
   canvas = pygamebg.open_window(400, 400, "RGB Colors")
   # -*- acsection: main -*-

   # painting the background
   canvas.fill([???, ???, ???])
   
   # -*- acsection: after-main -*-
   # finishing work with the PyGame library
   pygamebg.wait_loop()

Vendosni njohuritë tuaja për ngjyrat duke iu përgjigjur pyetjeve të mëposhtme.

.. commented out

    The following task is commented out because in English it doesn't make sense.
    
    After translation, you can remove lines starting ".. commented out" above up to this line, and un-indent the question below.

    .. dragndrop:: pygame__basics_quiz_color_names
        :feedback: Provo përsëri!
        :match_1: Black|||pg.Color("black")
        :match_2: Blue|||pg.Color("blue")
        :match_3: Red|||pg.Color("red")
        :match_4: Green|||pg.Color("green")

        Match the colors.

.. dragndrop:: pygame__basics_quiz_color_values
    :feedback: Provo përsëri!
    :match_1: Black|||(0, 0, 0)
    :match_2: Blue|||(0, 0, 255)
    :match_3: Red|||(255, 0, 0)
    :match_4: Green|||(0, 255, 0)

    Bashkoni ngjyrat.

.. mchoice:: pygame__basics_quiz_color_gray
   :answer_a: (1, 12, 123)
   :answer_b: (128, 0, 128)
   :answer_c: (0, 0, 128)
   :answer_d: (145, 145, 145)
   :correct: d
   :feedback_a: Provo përsëri
   :feedback_b: Provo përsëri
   :feedback_c: Provo përsëri
   :feedback_d: Saktë

   Which of the following colors is a shade of gray?

.. mchoice:: pygame__basics_quiz_color_purple
   :answer_a: red and green
   :answer_b: blue and red
   :answer_c: green and blue
   :answer_d: red, green and blue
   :correct: b
   :feedback_a: Provo përsëri
   :feedback_b: Saktë
   :feedback_c: Provo përsëri
   :feedback_d: Provo përsëri
   
   Cilat ngjyra janë të përziera për të prodhuar një ngjyrë vjollcë (magenta)?

.. mchoice:: pygame__basics_quiz_color_approx
   :answer_a: Bluish
   :answer_b: Reddish
   :answer_c: Yellowish
   :answer_d: Greenish
   :correct: c
   :feedback_a: Provo përsëri
   :feedback_b: Provo përsëri
   :feedback_c: Saktë
   :feedback_d: Provo përsëri

   Cila duhet të quhet më së miri ngjyra [240, 230, 18]?

Pra, ngjyrat përfaqësohen nga tre dhe koordinatat e pikave me dy numra.
Kontrolloni nëse e kuptoni këtë duke iu përgjigjur pyetjes vijuese.
   
.. dragndrop:: pygame__basics_quiz_colors_and_coordinates
    :feedback: Provo përsëri!
    :match_1: Black color|||[0, 0, 0]
    :match_2: Top left corner of the screen|||[0, 0]
    :match_3: Magenta color|||(255, 0, 255)
    :match_4: Bottom right corner of the screen|||(300, 200)

    
    çiftoni ngjyrat dhe koordinatat nëse ekrani është 300 pixel i gjerë dhe 200 pixel i lartë.
