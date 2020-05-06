Vizatimi i poligoneve me sythe
--------------------------------

Kujtoni një shembull të një programi që vizaton një gardh:

.. activecode:: PyGame_loops_fence_fixed
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :includesrc: src\PyGame\1_Drawing\7b_Loops_polygons\fence_fixed.py

Siç mësuam ndërkohë, vizatimi i secilës prej tyre me një deklarim të veçantë nuk është mënyra më e mirë për të vizatuar këtë vizatim. Një program më fleksibël do të merret duke vizatuar pickets në një loop. Le të shohim se si duhet të vizatojmë një poligon (një koleksion përfaqësohet nga një gjashtëkëndësh), në mënyrë që të ishte e lehtë të vizatoni të njëjtin poligon në vendet e tjera.

Është sigurisht e dobishme të prezantohet një pikë kryesore (anchor), në lidhje me të cilën do të shpreheshin të gjitha vertiktet poligonal. Në rastin e një gardh, vertikalet e pjesës së parë janë [(20, 80), (30, 70), (40, 80), (40, 270), (20, 270)]. Ne mund të zgjedhim pikën e parë të specifikuar (20, 80) për anchor, dhe të shprehim pikat e tjera duke përdorur koordinatat e pikës së parë. Pra, marrim që vertiktet të një pike janë [(x, y), (x + 10, y-10), (x + 20, y), (x + 20, y + 190), (x, y + 190)]. Duke vendosur *x* = 20, *y* = 80, marrim koordinatat e koleksionit të parë në gardh, dhe duke rritur *x* në mënyrë të njëpasnjëshme me 40 secila, mund të marrim edhe pika të tjera.

.. code:: 

    y = 80
    for x in range(20, 300, 40):
        pg.draw.polygon(canvas, pg.Color('brown'), [(x, y), (x + 10, y-10), (x + 20, y), (x + 20, y+190), (x, y+190)])

Meqenëse të gjitha kunjat janë në të njëjtën lartësi, koordinata *y* e spirancës nuk ndryshon, kështu që ne nuk kemi nevojë as ta prezantojmë (do të na duhet të prezantojmë koordinatat *y* nëse disa nga pjesët e rrumbullakëta ishin sipër të tjerët). Kjo do të thotë që në këtë rast, ne mund ta shkruajmë kodin e mëparshëm pak më thjeshtë.

.. code:: 

    for x in range(20, 300, 40):
        pg.draw.polygon(canvas, pg.Color('brown'), [(x, 80), (x + 10, 70), (x + 20, 80), (x + 20, 270), (x, 270)])

Variante të ndryshme të kësaj ideje themelore janë të mundshme. Për shembull, nëse fillimisht formojmë një listë të vertikteve poligonal (për koleksionin e parë), mund të formojmë një listë të vertikteve të zhvendosur në disa mënyra.

Ne mund të llogarisim koordinatat e vertices të zhvendosur në një loop shtesë:

.. code::

    picket = [(0, 0), (10, -10), (20, 0), (20, 190), (0, 190)]
    y0 = 80
    for x0 in range(20, 300, 40):
        displaced_picket = []
        for x, y in picket:
            displaced_picket.append((x+x0, y+y0))
        pg.draw.polygon(canvas, color, displaced_picket)

Ne mund të prezantojmë një funksion për të vizatuar një shumëkëndësh të caktuar në një pozicion të caktuar dhe të formojmë listën e vertikteve të zhvendosur në funksion:

.. code::

    def draw_polygon(points, color, x0, y0):
        displaced_points = []
        for x, y in points:
            displaced_points.append((x+x0, y+y0))
        pg.draw.polygon(canvas, color, displaced_points)

    picket = [(0, 0), (10, -10), (20, 0), (20, 190), (0, 190)]
    for x0 in range(20, 300, 40):
        draw_polygon(picket, pg.Color('brown'), x0, 80)


Secila nga këto dy qasje mund të zëvendësojë shtatë thirrjet në funksionin *pg.pull.polygon* në shembullin e dhënë fillestar, dhe secila është më e mirë se sa vizatimi i bashkëngjitur me komanda të ndara. Përdorimi i funksionit jep një kod pak më të gjatë, por ka përparësinë që i njëjti funksion të saktë mund të përdoret pa asnjë modifikim për të vizatuar ndonjë poligon në një pozicion të ri.

Provoni një, ose të dy ndryshimet e sugjeruara në programin e mësipërm, dhe më pas përdorni një nga këto metoda për të zgjidhur detyrat e mëposhtme.


Ushtrime
''''''''''''''''''

.. questionnote::

    **Detyra - tetëkëndëshat**
    
     Shkruaj një program që vizaton oktagona si në shembull (kliko butonin "Luaj detyrën").

Funksioni i vizatimit shumëkëndësh është i ngjashëm me atë të mëparshëm. Dallimi i vetëm është se në të, funksioni *pg.pull.polygon* thirret dy herë: një herë për pjesën e brendshme të poligonit, dhe kohën tjetër për skajet.

Jepen edhe koordinatat e tetëkëndëshit, mbetet të shtojmë një thirrje në funksionin e vizatimit brenda një lak të dyfishtë. Të dy *x* dhe *y* fillojnë nga vlera 0 dhe përparojnë në hapat prej 48 (48 është "gjerësia" dhe "lartësia" e tetëkëndëshit).
    
.. activecode:: PyGame_loops_octagons
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7b_Loops_polygons\octagons.py
    
    def draw_framed_polygon(vertices, color, frame_color, x0, y0):
        displaced_vertices = []
        for x, y in vertices:
            displaced_vertices.append((x+x0, y+y0))
        pg.draw.polygon(canvas, color, displaced_vertices)
        pg.draw.polygon(canvas, frame_color, displaced_vertices, 2)
    
    octagon = [(14, 0), (34, 0), (48, 14), (48, 34), (34, 48), (14, 48), (0, 34), (0, 14)]
    # finish the program
    
    
.. questionnote::

    **Detyra - shigjeta**

     Përfundoni programin e mëposhtëm për të vizatuar imazhin e dhënë (ju mund ta shihni imazhin duke klikuar butonin "Luaj detyrën").

Shigjetat e bardha po tregojnë drejtimin e majtë dhe shigjetat e zeza po drejtojnë djathtas. Ndërsa shigjetat e zeza dhe të bardha mbulojnë plotësisht imazhin së bashku, vini re se është e mjaftueshme për të vizatuar vetëm shigjeta të zeza (në një sfond të bardhë).

.. activecode:: PyGame_loops_arrows
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includexsrc: src\PyGame\1_Drawing\7b_Loops_polygons\arrows.py
   
    arrow = [(0, 10), (40, 10), (40, 0), (60, 20), (40, 40), (40, 30), (0, 30)]
    arrow_length, arrow_height = 60, 40
    canvas.fill(pg.Color("white"))
    ??? # finish the program



.. questionnote::

    **Detyrë - një tufë gjirafash**

     Jepen koordinatat e vertikteve të poligonit që përfaqësojnë gjirafën. Përfundoni programin duke vizatuar disa gjirafa (duke përdorur funksionin *Draw_polygon*). Bëni një listë të pozicioneve gjirafë sipas dëshirës.

.. activecode:: PyGame_loops_herd
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\7b_Loops_polygons\giraffe_herd.py
