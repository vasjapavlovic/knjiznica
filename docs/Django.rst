.. _django:


DJANGO - Wasco
===================
===================

UPORABNO PRI FORMS
####################

Prenos podatkov preko "KWARGS"
*******************************

    v get_context_data(self, *args, **kwargs):
        context = super(StrosekCreateView, self).get_context_data(*args, **kwargs)

        # strosek
        context['strosek_osnova_create_form'] = StrosekOsnovaCreateForm

        racun = Racun.objects.get(id=self.get_object().id)
        davcna_klasifikacija = racun.davcna_klasifikacija
        context['vrsta_stroska_izbira_form'] = VrstaStroskaIzbiraForm(davcna_klasifikacija=davcna_klasifikacija)

        # zavihek
        modul_zavihek = Zavihek.objects.get(oznaka="STROSEK_CREATE")
        context['modul_zavihek'] = modul_zavihek



Factory Boy
###########

Generiranje podatkov za bazo pri testiranju.


Izdelava enega podatka
**********************

Izdelava več podatkov
*********************

.. code-block:: none
    aktivnost_list = AktivnostFactory.build_batch(2)
