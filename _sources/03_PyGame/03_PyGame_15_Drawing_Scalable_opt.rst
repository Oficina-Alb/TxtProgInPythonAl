Ndryshimi i madhësisë së vizatimit
-------------------------

Kur folëm për lëvizjen e një vizatimi, përmendëm se është më mirë të bëjmë të gjitha llogaritjet në program, sepse është më e lehtë në atë mënyrë që të lëvizësh vizatimin, ose ta vizatosh në disa vende kur të jetë e nevojshme. Situata është e ngjashme kur ne duam të vizatojmë të njëjtën vizatim në madhësi të ndryshme, ndoshta në disa vende (secila mund të jetë në madhësi të ndryshme). Në vend që të llogaritni të gjitha koordinatat nga e para, mund të jetë e mjaftueshme për të ndryshuar një numër të vetëm në programin tonë për të marrë një vizatim të një madhësie tjetër.

Për të mësuar se si të bëj vizatime që mund të ndryshohen në madhësi të lehtë, le të shohim së pari se çfarë duhet të ndryshohet në një program vizatimi, në mënyrë që vizatimi të marrë një madhësi të ndryshme. Për shembull, nëse kemi vizatuar një re duke përdorur këto deklarime:

.. code::

    def cloud(x, y, shade):
        # draw a cloud of three circles
        gray = (shade, shade, shade)
        pg.draw.circle(canvas, gray, (x,      y), 50)
        pg.draw.circle(canvas, gray, (x - 50, y), 30)
        pg.draw.circle(canvas, gray, (x + 50, y), 30)

    cloud(200, 200, 180)

dhe tani duam që reja të jetë dy herë më e vogël dhe në mes të saj të jetë akoma në pikën (200, 200), atëherë do ta ndryshonim funksionin e dhënë më lart në:

.. code::

    def cloud(x, y, shade):
        # draw a cloud of three circles
        gray = (shade, shade, shade)
        pg.draw.circle(canvas, gray, (x,      y), 25)
        pg.draw.circle(canvas, gray, (x - 25, y), 15)
        pg.draw.circle(canvas, gray, (x + 25, y), 15)
    
Rrezet e të tre rrathëve duhet të shkurtohen në gjysmën e madhësisë së mëparshme (25 piksele në vend të 50 dhe 15 në vend të 30), por kjo nuk është e mjaftueshme. Nëse qendrat e rrathëve të vogla do të mbeten aty ku ishin, do të merrnim tre rrathë të ndara (provoni). Në mënyrë që vizatimi të duket ende si një re, duhet gjithashtu t'i afrojmë rrathët më pranë. Më saktësisht, distancat e qendrave të rrathëve më të vogla nga qendra e rrethit të madh duhet gjithashtu të jenë dy herë më pak se më parë, domethënë 25 në vend të 50 pikselave.

Në përgjithësi, ne jo gjithmonë duam një re që është dy herë më e vogël, por që retë mund të jenë të madhësive të ndryshme. Përveç kësaj, ne nuk duam të krijojmë një funksion të veçantë për secilën madhësi të reve, por të kemi një funksion që mund të tërheqë një re të një madhësie të caktuar. Do të ishte më e rehatshme nëse mund të vendosnim madhësinë e cloud me vetëm një numër dhe të ndryshonim madhësinë e cloud duke ndryshuar atë një numër. Për ta bërë këtë, duhet të shprehim të gjitha madhësitë që ndryshojnë me ndryshimin e madhësisë së cloud (që është distanca midis qendrave të rrathëve dhe rrezet e atyre rrathëve) duke përdorur një madhësi të zgjedhur. Për shembull, për atë madhësi të zgjedhur mund të marrim rrezen e rrethit të mesëm, të cilin do ta tregojmë me anë të :math:`r`. Distancat e qendrave të rrathëve më të vogla deri në qendrën e rrethit më të madh janë saktësisht :math:`r`, dhe rrezja e rrathëve më të vogla është e barabartë :math:` {3 \ over 5} r` pavarësisht nga madhësia e re. Kur përdorim të gjitha këto marrëdhënie që kemi vërejtur, funksioni duket si ky:

.. code::

    def cloud(x, y, r, shade):
        # draw a cloud of three circles
        gray = (shade, shade, shade)
        r_small = round(3 * r / 5)
        pg.draw.circle(canvas, gray, (x,     y), r)
        pg.draw.circle(canvas, gray, (x - r, y), r_small)
        pg.draw.circle(canvas, gray, (x + r, y), r_small)

The function has one parameter more - besides the position and the shade of gray, we also set the size of the cloud to this function. Now we can make drawings like this:

.. activecode:: PyGame__drawing_clouds_scalable
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\6_Scalable\clouds_scalable.py

Tani, le të rendisim hapat për një procedurë të përgjithshme për të rimarrë çdo vizatim të lëvizshëm, në mënyrë që të mund të ndryshohet në madhësi:

- Duhet të përcaktojmë një gjatësi në vizatim, i cili do të vendoset direkt. Mund ta quajmë këtë gjatësi të zgjedhur **gjatësi themelore** ose njësi matëse. Në shembullin e reve, gjatësia themelore është rrezja e rrethit të mesëm.
- Të gjitha rrezet e rrathëve të të cilave përbëhet vizatimi shprehen në përpjesëtim me gjatësinë themelore. Kjo do të thotë që nëse gjatësia jonë bazë shënohet nga :math:`a`, të gjitha gjatësitë e tjera në program do të jenë shumëfish :math:`a`, për shembull :math:`2a` ose :math:` 5a`. Ne përcaktojmë numrin :math:`a` nga raporti i gjatësisë së kërkuar dhe gjatësisë themelore të zgjedhur në vizatimin fillestar (ky raport mbetet i njëjtë kur ndryshon madhësia e vizatimit). Në shembullin me re, rrezja e rrethit të vogël është gjithmonë :math:`{3 \ over 5}` e gjatësisë themelore të zgjedhur :math:`r`. Nëse drejtkëndëshat ose elipsat paraqiten në vizatim, lartësitë dhe gjerësia e atyre drejtkëndëshave dhe elipsave gjithashtu duhet të shprehen në përpjesëtim me gjatësinë themelore, në të njëjtën mënyrë si rrezet e rrathëve.
- Ne përcaktojmë koordinatat e të gjitha pikave në lidhje me pikën kryesore, duke shtuar ose zbritur një numër të caktuar gjatesish themelore në koordinatat e pikës kryesore. Numri i kërkuar i gjatësive themelore përcaktohet përsëri nga relacioni në vizatimin fillestare. Në shembullin me re, për të përftuar :math:`x` koordinata e qendrës së rrethit të majtë, ne zbritim **një ** gjatësi themelore nga :math:`x` koordinata e pikës kryesore (qendra e mesit rrethi). Ne e bëjmë këtë sepse raporti i ndryshimit të :math:`x` koordinatat dhe gjatësia themelore është e barabartë me një. E njëjta procedurë zbatohet në parim përkoordinatat :math:`y`, megjithëse në këtë rast është veçanërisht e thjeshtë. Meqenëse  koordinatat e qendrave të rrathëve :math:`y`janë të njëjta, raporti i ndryshimit të koordinatave :math:` y` dhe gjatësia themelore është zero, kështu që duhet të shtohen gjatësi zero themelore në: matematikë: koordinata `y` e spirancës për të marrë :math:` y` koordinatë e qendrës së një rrethi më të vogël.

Për të kuptuar më mirë procesin e ndryshimit të madhësisë së një vizatimi, ne do ta përdorim atë edhe në shembullin e një ariu pelushi.

Ariu - madhësia
''''''''''''

Programi i mëposhtëm tregon kokën e ariut në mënyrë që të mund të zhvendoset lehtësisht:

.. activecode:: PyGame__drawing_bear_movable
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\5_Movable\teddy-bear_movable1a.py

Për të përmasuar madhësinë e vizatimit, ne prezantojmë një gjatësi themelore, për shembull :math `a = 5`. Tani mund t'i shprehim të gjitha rrezet duke përdorur :math:`a` si kjo:

.. code::

    framed_circle(canvas, pg.Color("yellow"), (cx - 60,  cy - 70),  9*a) # left ear
    framed_circle(canvas, pg.Color("yellow"), (cx + 60,  cy - 70),  9*a) # right ear
    framed_circle(canvas, pg.Color("yellow"), (cx,       cy)     , 20*a) # head
    framed_circle(canvas, pg.Color("yellow"), (cx,       cy + 50), 10*a) # snout
    framed_circle(canvas, pg.Color("black"),  (cx - 50,  cy - 30),  3*a) # left eye
    framed_circle(canvas, pg.Color("black"),  (cx + 50,  cy - 30),  3*a) # right eye
    framed_circle(canvas, pg.Color("black"),  (cx,       cy + 20),  3*a) # snout top
    
Çdo numër mund të zgjidhet si gjatësi bazë, dhe duke zgjedhur një gjatësi bazë prej 5 pikselë, ne nuk kemi nevojë të përdorim numra të vërtetë - të gjitha rrezet janë shumëfishë të plotë të :math:`a` dhe ne mund t'i llogaritim lehtësisht. Për shembull, ne shprehim rrezen prej 45 pikselësh si :math:`45 = 9 \ cdot 5 = 9 \ cdot a`, etj.

Tani duhet të shprehim koordinatat e qendrave të të gjitha rrathëve të tjera duke filluar nga pika kryesore :math:`(cx, cy)` dhe duke lëvizur me numrin e kërkuar të gjatësive :math:`a` në :math:` x `dhe :math:` y` drejtimi i boshtit. Merrni si shembull veshin e djathtë të ariut.

:math:`x` koordinata e qendrës së veshit të djathtë është :math:` cx + 60 = cx + 12 a`, ndërsa :math:`y` koordinata është :math:`cy - 70 = cy - 14 a`. Kur e bëjmë këtë për të gjitha qendrat e rrathëve, ne vijmë në formën e mëposhtme të programit:

.. activecode:: PyGame__drawing_bear_tmp2
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\6_Scalable\teddy-bear_scalable1a.py
    
Tani ne jo vetëm që mund të lëvizim ose kopjojmë një ari në ekran, por edhe ta shfaqim atë në madhësi të ndryshme. Për të konfirmuar se me të vërtetë funksionon ndryshimi, thërrasim funksionin

.. code::

    draw_teddy(width // 2, height // 2, 6)
    
e cila vizaton një ari me pikën qendrore në qendër të dritares, mund të zëvendësohet me pesë rreshtat në vijim:

.. code::

    draw_teddy(85, 100, 4)
    draw_teddy(235, 100, 3)
    draw_teddy(50, 250, 2)
    draw_teddy(150, 250, 2)
    draw_teddy(250, 250, 2)

Kopjoni ose rivendosni këto pesë rreshta kodi në program dhe provojeni! Konsideroni sa punë do të ishte që këto pesë arinj të shfaqen pa u llogaritur në program.

Tani përpiquni të plotësoni një shembull të nisur.

Ushtrim - madhësia e shtëpisë
'''''''''''''''''

Do të fillojmë me një program që vizaton katër shtëpi në pozicionet e dhëna në ekran:

.. activecode:: PyGame__drawing_house_detailed1
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src\PyGame\1_Drawing\5_Movable\house2D_detailed_movable.py

Plotësoni rimodelimin e programit në kutinë më poshtë në mënyrë që shtëpitë të mund të ridimensionohen lehtësisht. Për shembull, ju mund të merrni 10 piksele për madhësinë themelore, sepse në atë rast, shprehja e të gjitha gjatësive duke përdorur gjatësinë themelore është shumë e lehtë. Kur konfirmoni që programi pas te luhet shfaq të njëjtën imazh si programi fillestar më lart, zëvendësoni thirrjet e funksionit të dhënë *house* me 4 në vijim dhe konfirmoni që madhësia e shtëpisë po funksionon si duhet (ju duhet të merrni imazhin siç keni klikuar në butonin "Luaj detyrën"):

.. code::

    house(150,  90,  8, pg.Color(220, 220, 220))
    house(250, 130,  9, pg.Color("white"))
    house(350, 160, 10, (255,255,150))
    house( 50, 150, 10, pg.Color("khaki"))

.. activecode:: PyGame__drawing_house_scalable1
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask: 
    :includexsrc: src\PyGame\1_Drawing\6_Scalable\house2D_detailed_scalable1.py
   
    canvas.fill(pg.Color("darkgreen")) # paint background

    def house(x, y, a, wall_color):
        pg.draw.polygon(canvas, pg.Color("red"), [(x, y), (x + ???*a, y - ???*a), (x+14*a, y)]) # roof
        pg.draw.rect(canvas, wall_color,       (x,       y,      14*a, 10*a)) # walls
        pg.draw.rect(canvas, pg.Color("brown"), (x + ???, y + ???, 3*a,  3*a)) # left window
        pg.draw.rect(canvas, pg.Color("brown"), (x + ???, y + ???, ???,  ???)) # right window
        pg.draw.rect(canvas, pg.Color("brown"), (x + ???, y + ???, ???,  ???)) # door
        
    house(150,  90, 10, (220, 220, 220))
    house(220, 130, 10, pg.Color("white"))
    house(350, 160, 10, (255, 255, 150))
    house( 50, 150, 10, pg.Color("khaki"))

Pasi të keni ndryshuar me sukses funksionin *house*, provoni paraqitjet e ndryshme, ngjyrat dhe madhësitë e shtëpive, siç është ajo më poshtë, ose ndonjë tjetër që ju zgjidhni vetë:

.. code::

    house(278, 110, 1, (211, 207, 169))
    house(231, 119, 2, (217, 211, 164))
    house(174, 130, 3, (228, 221, 152))
    house(112, 142, 4, (231, 222, 150))
    house( 18, 160, 6, (240, 230, 140))
