Lëvizja e vizatimeve
-----------------

Animacionet që kemi parë deri më tani bazohen në shfaqjen e një imazhi të ndryshëm që përgatitëm paraprakisht në secilën kornizë. Tani do të lëvizim edhe imazhet që janë treguar, në mënyrë që e njëjta imazh të shfaqet në vende të ndryshme në dritare, domethënë lëviz.

Le të shohim një shembull:

.. image:: ../../_images/car.png
   :width: 50px

.. activecode:: PyGame__anim_car_oneway
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src/PyGame/2_Animation/2b_Anim_Motion/car_rightwards_only.py

Si më parë, ne kemi një funksion *new_frame* që tregon një imazh në secilën kornizë. Ajo që është e re në këtë shembull është se pozicioni i asaj imazhi ndryshon nga korniza në kornizë.

Imazhi tregohet në mënyrë që këndi i sipërm i saj i majtë të shfaqet në pikën (*car_x*, *car_y*). Në mënyrë që makina të lëvizë në të djathtë, në secilën kornizë rrisim koordinatën *x* të figurës. Vetëm kemi parasysh se kur makina shkon shumë larg në të djathtë, ne e kthejmë makinën në mënyrë që skaji i saj i djathtë të rreshtohet me skajin e majtë të dritares. Në këtë mënyrë, makina fillon të rishfaqet gradualisht në të majtë.

~~~~

Në mënyrë të ngjashme, ne gjithashtu ne mund të lëvizim vizatimet të vizatojnë veten (jo vetëm imazhe të gatshme). Duke vepruar kështu, ne mund të lëvizim imazhin ose vizatimin në çdo drejtim. Këtu është një shembull:

.. activecode:: PyGame__anim_billiards
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src/PyGame/2_Animation/2b_Anim_Motion/billiards.py

Vini re se si kontrollojmë nëse topi prek buzë ekranit. E djathta e djathtë e topit ka një koordinatë *x* të barabartë me :math:`cx + r`. Nëse kjo vlerë do të ishte e barabartë me gjerësinë e dritares, do të nënkuptonte që topi prek skajin e djathtë të dritares, dhe nëse :math:`cx + r> width`, do të thotë që topi tashmë ka kaluar pjesërisht në të djathtë buzë dritares. Në këtë rast, me komandën :math:`dx = -dx`, duke filluar nga korniza tjetër një vlerë e kundërt me atë të deritanishme do t'i shtohet koordinatës *x* të topit, d.m.th., topi do të vijojë tutje duke lëvizur 3 pixel në të majtë. Kjo do të duket si topi i kërrusur në skajin e djathtë të dritares.

Vini re një detaj tjetër: në vend të :math:`cx + r> width` ne mund të kishim përdorur gjithashtu :math:`cx + r> = width` dhe programi do të funksiononte pothuajse i njëjtë. Sidoqoftë, meqenëse topi **nuk lëviz me një piksel**, nuk do të ishte e vlefshme nëse do të përdorim kushtin :math: `cx + r == width`, sepse atëherë topi mund të kalonte pozicionin që po kontrollojmë dhe do kalojmë nëpër buzë të dritares.

Ne e analizuam plotësisht rastin e skajit të djathtë të dritares dhe i njëjti arsyetim u aplikua në skajet e tjera kur programi ishte duke u shkruar. Efekti i përgjithshëm i dy komandave *if* është që topi të lëshohet në çdo cep të dritares.

Kontrolloni nëse e kuptoni këtë duke iu përgjigjur pyetjeve të mëposhtme.

Lëvizja e vizatimeve - pyetje
'''''''''''''''''''''''''''''

.. dragndrop:: pygame__anim_quiz_bounce1
    :feedback: Provo përsëri!
    :match_1: for left edge ||| if cx - r < 0
    :match_2: for right edge ||| if cx + r > width
    :match_3: for top edge ||| if cy - r < 0
    :match_4: for bottom edge ||| if cy + r > height

    Krahasoni kontrollin që topi nga shembulli i mëparshëm ka kaluar një skaj të caktuar në komandën *if*  të duhur.

.. mchoice:: pygame__anim_quiz_bounce2
    :answer_a: djathtas
    :answer_b: lart
    :answer_c: majtas
    :answer_d: poshtë
    :correct: c
    :feedback_a: Provo përsëri
    :feedback_b: Provo përsëri
    :feedback_c: Saktë!
    :feedback_d: Provo përsëri

    Në cilën anë lëviz një imazh duke shtuar një vlerë negative në koordinatën e tij *x*?

.. mchoice:: pygame__anim_quiz_bounce3
    :answer_a: if x + im_width < 0:
    :answer_b: if y + im_height < 0:
    :answer_c: if x < 0:
    :answer_d: if y < 0:
    :correct: b
    :feedback_a: Provo përsëri
    :feedback_b: Saktë!
    :feedback_c: Provo përsëri
    :feedback_d: Provo përsëri

    Le të jetë 'width' e gjerësisë së dritares, 'im_width' gjerësia e figurës dhe (x, y) këndi i sipërm i majtë i figurës. Përputhni kushtet logjike me kuptimin e tyre
    
.. dragndrop:: pygame__anim_quiz_bounce4
    :feedback: Provo përsëri!
    :match_1: imazhi doli përmes skajit të majtë të dritares ||| x + im_width <0
    :match_2: imazhi filloi të dalë përmes skajit të majtë të dritares ||| x <0
    :match_3: imazhi doli përmes skajit të djathtë të dritares ||| x> gjerësi

    Le të jetë 'width' e gjerësisë së dritares, 'im_width' gjerësia e figurës dhe (x, y) këndi i sipërm i majtë i figurës. Përputhni kushtet logjike me kuptimin e tyre

.. mchoice:: pygame__anim_quiz_bounce5
    :answer_a: x = width; dx = -10
    :answer_b: x = width + im_width; dx = -10
    :answer_c: x = width - im_width; dx = -10
    :answer_d: x = width + im_width; dx = 10
    :correct: a
    :feedback_a: Saktë!
    :feedback_b: Jo, kjo është shumë larg nga skaji i duhur.
    :feedback_c: Jo, në këtë mënyrë e gjithë imazhi është tashmë në dritare.
    :feedback_d: Jo, imazhi është shumë larg dhe do të vazhdojë të bëhet më larg.

    Le  të jetë *width* gjerësia e dritares, *im_width* gjerësia e figurës, (*x*, *y*) këndi i sipërm i majtë i figurës dhe *dx* vlera me të cilën koordinata *x* e imazhi do të ndryshohet më vonë. Cilat komanda do të bëjnë që imazhi të fillojë të shfaqet duke hyrë në dritare përmes skajit të djathtë?

Detyrë - një makinë që shkon majtas djathtas
'''''''''''''''''''''''''''''

Provoni të ripërpunoni programin e parë në mënyrë që makina të lëvizë në mënyrë alternative në njërën anë dhe në anën tjetër, si në shembullin (butoni "Luaj detyrën"). Programi tashmë përmban komanda për të formuar një bashkim të dy imazheve. Imazhi i makinës që përballet drejt, është i ngarkuar, ndërsa imazhi i makinës përballë palës tjetër merret duke përdorur funksionin *pg.transform.flip*, i cili shndërron imazhin e dhënë në një simetrik me të.

.. activecode:: PyGame__anim_car_right_left
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/2_Animation/2b_Anim_Motion/car_right_left.py
    
    import pygame as pg, pygamebg
    (width, height) = (400, 300)
    canvas = pygamebg.open_window(width, height, "Car")
    
    car_rightwards_image = pg.image.load("car.png") 
    # creating flipped image (symmetric with respect to the vertical axis)
    car_leftwards_image = pg.transform.flip(car_rightwards_image, True, False)
    car_images = (car_rightwards_image, car_leftwards_image)
    fps = 50
    
    def new_frame():
        pass
        
    pygamebg.frame_loop(fps, new_frame)

        
