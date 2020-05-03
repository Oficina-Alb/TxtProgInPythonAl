Vizatimi i tekstit
------------

Programet e vizatimit shpesh shtypin mesazhe të ndryshme së bashku me fotografitë (ndoshta keni parë shumë shembuj vetë). Ja se si ta bëni atë në PyGame: e shembuj të frymëzuar nga shenja të tilla neoni.

.. activecode:: PyGame__anim_text
    :nocodelens:
    :modaloutput:
    :includesrc: src/PyGame/2_Animation/2d_Anim_Text/text_example.py

Siç mund ta shihni në shembull, në mënyrë që teksti të shfaqet, së pari **duhet të krijojmë një objekt që përfaqëson një font**. Për ta bërë këtë, ne përdorim funksionin ``pg.font.SysFont``, për të cilin specifikojmë llojin dhe madhësinë e shkronjave. Ne gjithashtu mund të krijojmë më shumë objekte të tilla në rast se synojmë të përdorim madhësi ose lloje të ndryshme të shkronjave, megjithëse shpesh na duhet vetëm një font.

Pas krijimit të fontit, sa herë që duam të shfaqim një tekst përsërisim dy hapat e mëposhtëm:

- Hapi i parë është **për të krijuar një imazh që përmban tekstin e dëshiruar.** Kjo është realizuar duke përdorur funksionin ``font.render``, ku *font* është objekti i shkronjave i krijuar në fillim. Parametrat e funksionit *font.render* janë teksti që do të shfaqet, vlera logjike që përcakton nëse duhet të vizatoni linja më të këndshme (d.m.th. të përdorni të ashtuquajturën teknikë anti-aliasing) dhe ngjyrën në të cilën do të jetë teksti shkruar, me atë rend.
- Hapi i dytë është njësoj siç shfaqim ndonjë imazh të gatshëm - **shfaqim imazhin e marrë në hapin e mëparshëm** në pozicionin që zgjedhim. Për të llogaritur pozicionin mund të përdorim madhësinë e figurës sipas nevojës (si në shembull).

Detyrat - shenja neoni
''''''''''''''''''

Ju duhet të keni parë shenja të ndezura të tubit neon. Ata tërheqin vëmendjen duke ndezur dhe fikur grupe të ndryshme shkronjash në një rend të caktuar përsëritës. Më poshtë janë disa shembuj të frymëzuar nga shenja të tilla ndezëse.


.. questionnote::

    **Teksti neon:** Shkruani një program që shfaq tekstin neon, i ngjashëm me shembullin më poshtë (butoni "Luaj detyrën").
    
     Ju mund të ndryshoni tekstin, ngjyrën dhe madhësinë e tij, fontin, frekuencën e ndërprerjes të aktivizuar / çaktivizuar, ose ndonjë gjë tjetër, nëse ju pëlqen. Nëse dëshironi të imitoni programin tonë sa më afër që të jetë e mundur, ai përdor shkronja të tipit "Arial", madhësia 80 dhe shfaq tekstin në çdo kornizë të dytë, në qendër, në 3 korniza për sekondën e kornizës.
    
**Këshillë:** Për variablat globale që përshkruajnë skenën, një variabël logjik është i mjaftueshëm për të treguar nëse teksti i dhënë duhet të shfaqet apo jo. Ne do ta ndryshojmë vlerën e këtij variabli në funksionin *new_frame ()* në mënyrë që të ketë një vlerë *të vërtetë* në çdo kornizë të dytë.

.. activecode:: PyGame__anim_neon1
    :nocodelens:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/2_Animation/2d_Anim_Text/neon_sign1.py

    import pygame as pg, pygamebg
    text = "PYTHON"
    (width, height) = (len(text) * 70, 100)
    canvas = pygamebg.open_window(width, height, "Neon sign")
    
.. reveal:: PyGame__anim_neon1_reveal
   :showtitle: Show solution
   :hidetitle: Hide solution

    .. activecode:: PyGame__anim_neon1_solution
        :nocodelens:
        :modaloutput:
        :includesrc: src/PyGame/2_Animation/2d_Anim_Text/neon_sign1.py

.. questionnote::

    **Shtimi i shkronjave:** Tani, provoni të imitoni këtë shembull. Vetëm shkronja e parë shfaqet në kornizën e parë dhe më pas një shkronjë më shumë në secilën kornizë vijuese derisa të shfaqen të gjitha shkronjat. Kjo pasohet nga një kornizë që tregon asgjë, pastaj tre korniza me të gjitha shkronjat që shfaqen, dhe pastaj gjithçka përsëritet. Shkalla e kornizës së programit tonë është 2 korniza për sekondë.

**Këshillë:** Këtu janë disa komente që mund të ndihmojnë në zgjidhjen e problemit

- Nga përshkrimi (dhe duke vëzhguar shembullin) mund të konkludojmë se cikli i plotë përmban katër korniza më shumë se numri i shkronjave në tekst.
- Ne mund të përcaktojmë madhësinë që na duhet dritarja jonë të bazohet në gjatësinë e tekstit, si në shembullin e mëparshëm.
- Teksti shfaqet gjithmonë në të njëjtin pozicion (këndi i sipërm i majtë i tekstit është i njëjtë). Prandaj, është e mjaftueshme për të llogaritur pozicionin një herë, në pjesën kryesore të programit.
- Ne mund të përdorim një variabël counter frame, dhe bazuar në vlerën e tij përcaktojmë nëse dhe cilën pjesë të tekstit duhet të shfaqet duke përdorur *if* komandat në funksionin *new_frame ()*.

.. activecode:: PyGame__anim_neon2
    :nocodelens:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/2_Animation/2d_Anim_Text/neon_sign2.py

.. questionnote::

    **Shkronjat e vetme:** Në këtë shembull së pari çdo shkronjë shfaqet individualisht dhe më pas të gjitha shkronjat ndizen dhe fiken 3 herë. A mund ta kopjoni këtë sjellje?

**Ndihmë:** Pozicionet e ekranit të shkronjave individuale janë (0, 0), (50, 0), (100, 0), (150, 0), etj. Numri i kornizave në një cikël është 6 plus numri i shkronjave në tekst. Pjesa tjetër e ideve janë shumë të ngjashme me ato të shembujve të mëparshëm.

.. activecode:: PyGame__anim_neon3
    :nocodelens:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/2_Animation/2d_Anim_Text/neon_sign3.py

.. questionnote::

    **Shkronjat lëvizëse:** Ky shembull është i ndryshëm në atë që shkronjat lëvizin. Mundohuni ta zgjidhni edhe këtë.
    
**Këshillë:** Pasi të formoni një imazh nga teksti i dhënë, detyra bëhet shumë e ngjashme me detyrën me një makinë në lëvizje.

.. activecode:: PyGame__anim_neon4
    :nocodelens:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/2_Animation/2d_Anim_Text/neon_sign4.py


Së fundmi, nëse dëshironi, mund të bëni një shenjë neoni të modelit tuaj këtu.

.. activecode:: PyGame__anim_neon5
    :nocodelens:
    :modaloutput:
