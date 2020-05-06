Leximi i butonave të mouse
----------------------------

Informacioni në lidhje me butonat e mouse të shtypur aktualisht sigurohet nga funksioni ``pg.mouse.get_pressed ()``. Ky funksion kthen një tufë prej tre elementësh (një treshe e porositur), të cilat përdoren si vlera logjike. Elementet tuple korrespondojnë me butonat e mouse, të mesëm dhe të djathtë përkatësisht. Një vlerë *True* tregon që një buton është shtypur aktualisht, dhe *False* se nuk është.

Shembulli më poshtë tregon se si të lexoni cilat butona të mouse shtypen. Kjo është pjesa e programit ku ndodh:

.. activecode:: PyGame__interact_put_ball_into_box_part
    :passivecode: true

    pressed_mouse_button = pg.mouse.get_pressed()

    if pressed_mouse_button[2]: # right button - new game
        (x, y) = (width//2, height//2) # return the ball to the center
        won, lost = False, False # the player has neither won nor lost
        
    if pressed_mouse_button[0]: # left button - move the ball
        (xm, ym) = pg.mouse.get_pos() # mouse position coordinates
        # the ball moves away from the mouse for another half of that distance
        x = x - 0.5 * (xm - x)
        y = y - 0.5 * (ym - y)

Tuple *pressed_mouse_button* merr 3 vlera nga funksioni *pg.mouse.get_pressed()*.Ne i përdorim këto në deklarimet *if*. Për shembull *if pressed_mouse_button[2]* do të thotë "nëse butoni i djathtë është shtypur" (0 për majtas, 1 në mes, and 2 për djathtas).

Shembuj dhe detyra
'''''''''''''''''''

.. questionnote::
    
    **Shembull - vendosni topin në kuti:**
    
     Ndërsa butoni i majtë i mouse mbahet i shtypur, topi largohet nga kursori. Qëllimi është të vendosni topin në kutinë e kuqe duke lëvizur mouse dhe duke shtypur butonin e majtë. Shtypja e butonit të djathtë e kthen lojën në fillim.
    
Së pari, studioni me kujdes funksionin *new_frame ()* dhe më pas hidhini një sy pjesëve të tjera të kodit. Provoni programin dhe shihni nëse funksionon ashtu siç e prisnit pasi të keni lexuar përshkrimin.
    
.. activecode:: PyGame__interact_put_ball_into_box
    :nocodelens:
    :enablecopy:
    :modaloutput:
    :includesrc: src/PyGame/3_Interaction/3b_Mouse_readkey/put_ball_into_box.py    



.. questionnote::

    **Detyrë - tek dhe nga mouse:**
    
     Përfundoni programin në mënyrë që të funksionojë siç tregohet në shembullin (butoni "Luaj detyrën").
    
     - Kur shtypet butoni i majtë i mouse, topi duhet të lëvizë larg mouse, si në shembullin "vendos topin në kutinë" më lart, por jo nga gjysma e distancës, por vetëm nga një e dhjeta e distancës me miun.
     - Kur butoni i majtë i mouse nuk shtypet, topi duhet të lëvizë më afër me një të dhjetën e distancës me mouse (si në detyrën "drejt mouse" në mësimin e kaluar).
    
.. activecode:: PyGame__interact_to_and_from_mouse
    :nocodelens:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/3_Interaction/3b_Mouse_readkey/to_and_from_mouse.py
    
    import pygame as pg, pygamebg
    (width, height) = (400, 400)
    canvas = pygamebg.open_window(width, height, "Ball following the mouse")

    (x, y) = (width // 2, height // 2) # ball starts from center of the window

    def new_frame():
        global x, y
        
        # ADD THE MISSING PART
        
        # draw a green ball on a white background
        canvas.fill(pg.Color("white")) 
        pg.draw.circle(canvas, pg.Color("green"), (int(x), int(y)), 10)

    pygamebg.frame_loop(50, new_frame)


.. questionnote::

    **Detyrë - laser:** 
    
    Përfundoni programin në mënyrë që të funksionojë siç tregohet në shembullin (butoni "Luaj detyrën").
    
     Ndërsa butoni i majtë i mouse është i shtypur, "lazeri" është i ndezur, përndryshe është i fikur. Ndërsa lazeri është i ndezur, energjia e tij zvogëlohet për 1 (por jo nën 0), dhe kur është jashtë energjisë rritet me 2 (por jo më shumë se 100).
    

.. activecode:: PyGame__interact_laser
    :nocodelens:
    :modaloutput:
    :playtask:
    :includehsrc: src/PyGame/3_Interaction/3b_Mouse_readkey/laser.py

    import pygame as pg, pygamebg
    width, height = 400, 400
    canvas = pygamebg.open_window(width, height, "Laser")

    laser_on = False
    energy = 25 # how full is the laser from 0 to 100

    def draw():
        canvas.fill(pg.Color("black")) # background
        
        # the indicator shows how full the laser is
        pg.draw.rect(canvas, pg.Color("green"), (10, 10, 100, 10), 1)
        pg.draw.rect(canvas, pg.Color("green"), (10, 10, energy, 10))
        
        if laser_on:
            reach = (4 * energy, height - 4 * energy)
            pg.draw.line(canvas, pg.Color("red"), (0, height), reach, 5)
        
    def new_frame():
        global energy, laser_on
        
        # READ THE STATE OF THE LEFT MOUSE BUTTON AND SET THE VALUES
        # OF THE GLOBAL VARIABLES energy, laser_on

        draw()

    pygamebg.frame_loop(15, new_frame)


.. commented out

    .. questionnote::

        **Task - background color:** This simple example only illustrates the reading of the mouse buttons status. While the left button is pressed, the background becomes lighter, and while the right button is pressed, the background becomes darker.
        

    .. activecode:: PyGame__interact_bg_color
        :nocodelens:
        :modaloutput:
        :includesrc: src/PyGame/3_Interaction/3b_Mouse_readkey/bg_color.py

