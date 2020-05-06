Vizatimi nga referenca - shembuj shtesë
--------------------------------------------

Supozojmë se tashmë keni fituar një aftësi në leximin e koordinatave dhe thirrjen e funksioneve për vizatimin e formave themelore. Prandaj, në detyrat e mëposhtme do të ketë disa sfida të reja.

Shumë vizatime kanë një rregullsi, si simetri boshtore ose një pjesë të vizatimit që përsëritet vetë. Nëse dëshironi të bëni një vizatim të tillë vetë, në mënyrë që të duket mirë, nuk mund të zgjidhni të gjitha pikat plotësisht lirshëm. Në vend të kësaj, duhet të zgjidhen disa pika dhe të llogariten disa pika.

Në mënyrë që të afrohemi në krijimin e imazheve që ne hartojmë vetë, mënyra e specifikimit të vizatimeve është modifikuar pak. Vizatimet ende specifikohen me një program shembulli që vizaton një imazh (ekziston një thënie se një imazh vlen 1000 fjalë). Ajo që është e re është se nuk do të jetë e mundur të lexoni njërën ose të dy koordinatat në disa pjesë të figurës, por përkundrazi do t'ju duhet të llogaritni ato koordinata bazuar në koordinatat e njohura.

Përveç që kanë nevojë për pak llogaritje, vizatimet në detyrat e mëposhtme kanë edhe më shumë detaje, kështu që duhet pak më shumë për t’i bërë ato.

Gardh
'''''''

Në këtë detyrë, leximi i koordinatës :math:`x` është i kufizuar në seleksionin e parë të gardhit dhe hapësirën e parë. Të gjitha koordinatat e tjera të nevojshme mund të llogariten.

.. activecode:: PyGame__drawing_fence
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :playtask:
   :includexsrc: src\PyGame\1_Drawing\4_ByGrid_Additional\fence_assist.py
   
.. reveal:: PyGame__drawing_fence_reveal
   :showtitle: Show solution
   :hidetitle: Hide solution

   The complete program is provided, you can try it here as well.
	       
   .. activecode:: PyGame__drawing_fence_solution
      :nocodelens:
      :enablecopy:
      :modaloutput:
      :includesrc: src\PyGame\1_Drawing\4_ByGrid_Additional\fence.py

Ndërtesa
''''''''

Të gjitha dritaret e ndërtesës janë të njëjtën madhësi, hapësirat midis dyshemeteve janë të barabarta, dhe faqet e majta dhe të djathta të ndërtesës janë simetrike (përveç që dritaret simetrik nuk janë domosdoshmërisht të njëjtën ngjyrë). Përdorni këtë informacion për të llogaritur koordinatat që nuk mund t'i lexoni.

.. activecode:: PyGame__drawing_building
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :playtask:
   :includexsrc: src\PyGame\1_Drawing\4_ByGrid_Additional\building_assist.py
   
.. commented out 

    .. reveal:: PyGame__drawing_building_reveal
       :showtitle: Show solution
       :hidetitle: Hide solution

       The complete program is provided, you can try it here as well.
               
       .. activecode:: PyGame__drawing_building_solution
          :nocodelens:
          :enablecopy:
          :modaloutput:
          :includesrc: src\PyGame\1_Drawing\4_ByGrid_Additional\building.py

Stickman
''''''''

Në këtë shembull, koordinatat e pikave në këmbën e djathtë nuk mund të lexohen, por është simetrike me këmbën e majtë. Meqenëse gjerësia e figurës është e njohur (shiko fillimin e programit), koordinatat e dy pikave të panjohura në të djathtë mund të llogariten duke përdorur pikat simetrike të njohura në të majtë.

**Ndihmë** Le të jetë :math:`A` një pikë në anën e majtë të figurës, dhe :math:` B` një pikë në anën e djathtë të figurës, simetrike me pikën :math:`A `. Dy pikat më pas kanë të njëjtat :math:`y` koordinatë, dhe shuma e koordinatave të :math:` x` të pikave :math:`A` dhe :math:` B` është e barabartë me gjerësinë e figurës.

.. activecode:: PyGame__drawing_stickman
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :playtask:
   :includexsrc: src\PyGame\1_Drawing\4_ByGrid_Additional\stickman_assist.py
   
.. commented out 

    .. reveal:: PyGame__drawing_stickman_reveal
       :showtitle: Show solution
       :hidetitle: Hide solution

       The complete program is provided, you can try it here as well.
               
       .. activecode:: PyGame__drawing_stickman_solution
          :nocodelens:
          :enablecopy:
          :modaloutput:
          :includesrc: src\PyGame\1_Drawing\4_ByGrid_Additional\stickman.py

Mace
'''''''

Veshët e kësaj mace mund të përshkruhen si trekëndësha të mbushur. Ndërsa veshët janë ngjitur në kokë, dy vertikale të secilit trekëndësh mund të zgjidhen me më shumë liri (mjafton t'i vendosni ato diku brenda rrethit të kokës). Përveç dy trekëndëshave që përfaqësojnë veshët, kemi gjithashtu:

- dy rrathë (koka dhe maja e gocës)
- gjashtë elips (sy, nxënës dhe pjesë të gërhitës)
- gjashtë rreshta (mustaqe)

:math:`x` koordinatat në anën e djathtë të figurës nuk mund të lexohen, por ato mund të llogariten duke përdorur simetri (dhe gjerësia e njohur e figurës - shiko fillimin e programit).

**Shënim:** Procedura për përcaktimin e parametrave të elipsit në anën e djathtë është paksa e ndryshme nga ajo e përdorur për rrathët ose segmentet e linjës. Vini re se kulmi i sipërm **majtas** i drejtkëndëshit të rrethuar në lidhje me elipsën e kërkuar është në të vërtetë një imazh pasqyrë i kulmës së sipërme **të djathtë** të drejtkëndëshit të rrethuar në lidhje me elipsën e njohur. Kjo do të thotë që kur gjejmë parametrat *(x, y, w, h)* të elipsit në anën e majtë, parametrat e elipsit të tij simetrik në të djathtë janë *(gjerësia - x - w, y, w, h )*, ku *gjerësia* është gjerësia e dritares, *x*, *y* janë koordinatat e kulmës së sipërme të majtë të drejtkëndëshit rreth elipsit në të majtë, dhe * w * dhe * h * janë gjerësia dhe lartësia e elipsave.

.. activecode:: PyGame__drawing_cat
   :nocodelens:
   :enablecopy:
   :modaloutput:
   :playtask:
   :includexsrc: src\PyGame\1_Drawing\4_ByGrid_Additional\cat_assist.py

.. reveal:: PyGame__drawing_cat_reveal
   :showtitle: Show solution
   :hidetitle: Hide solution

   The complete program is provided, you can try it here as well.
	       
   .. activecode:: PyGame__drawing_cat_solution
      :nocodelens:
      :enablecopy:
      :modaloutput:
      :includesrc: src\PyGame\1_Drawing\4_ByGrid_Additional\cat.py

