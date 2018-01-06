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

Osnovna dokumentacija:
https://media.readthedocs.org/pdf/factoryboy/latest/factoryboy.pdf
http://factoryboy.readthedocs.io/en/latest/recipes.html



Osnova za generiranje podatkov
******************************

.. code-block:: Python

    import factory

    class AktivnostFactory(factory.Factory):
        class Meta:
            model = AktivnostFactory

        naziv = 'Moj prvi factory za aktivnost'



Izdelava enega podatka
**********************

.. code-block:: python

    # izdelamo aktivnost iz factory boya
    aktivnost = AktivnostFactory.create()

    # aktivnost shranimo v bazo
    aktivnost.save()


Izdelava več podatkov
*********************

.. code-block:: none

    aktivnost_list = AktivnostFactory.build_batch(2)


.. image:: images/test_picture.png



Selenium
########

Install geckodriver
*******************

* https://askubuntu.com/questions/870530/how-to-install-geckodriver-in-ubuntu
