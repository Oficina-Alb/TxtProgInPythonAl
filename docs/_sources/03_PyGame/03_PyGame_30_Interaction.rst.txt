Ndërveprimi
===========

Në programet PyGame që kemi parë deri më tani, përdoruesi nuk mund të ndikojë në ekzekutimin e tyre, përveç përfundimit të programit. Ne mund ta krahasojmë këtë lloj programi me shikimin e filmave - përdoruesi është në thelb një shikues.

Në pjesën tjetër, do të merremi me programe në të cilat përdoruesi ka një rol aktiv dhe mund të ndikojë në ekzekutimin e programit duke përdorur një mouse dhe një tastierë. Ekzistojnë dy mënyra themelore që programi ynë të "dijë" kur përdoruesi ka bërë një veprim.

- Një mënyrë është që **të lexoni statusin** e mouse dhe tastierës. Nga kodi mund të pyesim se cili është pozicioni aktual i mouse, nëse shtypet ndonjë çelës dhe si ato.
- Një mënyrë tjetër është të përdorni **ngjarjet e sistemit**. Cdo veprim i përdoruesit (shtypja e një butoni të mouse ose një tastierë tastierë, lëshimi i një çelësi, lëvizja e mouse, etj.) Është një ngjarje, dhe në programet mund të marrim informacione rreth ngjarje të tilla dhe u përgjigjen atyre.

Në këtë kapitull, ne do të njihemi me të dyja këto mënyra që mundësojnë programet tona t'u përgjigjen veprimeve të përdoruesit.

   .. toctree::
      :maxdepth: 1

      ./03_PyGame_31_Interaction_ReadMousePos.rst
      ./03_PyGame_32_Interaction_ReadMouseKey.rst
      ./03_PyGame_33_Interaction_ReadKeyboard.rst
      ./03_PyGame_34_Interaction_Events.rst
      ./03_PyGame_35_Interaction_EventMouse.rst
      ./03_PyGame_36_Interaction_EventKeyboard.rst
