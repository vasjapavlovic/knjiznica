.. _python:

PYTHON
===================================================


.. _python install python36:

Install python 3.6 on ubuntu
----------------------------

#.  potreben dodatek za add-apt-repository

    .. code-block:: none
    
        sudo apt-get install software-properties-common


#.  dodamo repository

    .. code-block:: none

        sudo add-apt-repository ppa:jonathonf/python-3.6


#.  updatamo repositorije

    .. code-block:: none

        sudo apt-get update


#.  inštaliramo python

    .. code-block:: none

        sudo apt-get install python3.6


#.  NAVODILA:

    *   http://ubuntuhandbook.org/index.php/2017/07/install-python-3-6-1-in-ubuntu-16-04-lts/

    *   po defaultu je pod ukazom python3 --> python3.5


#.  sprememba na python3.6

    .. code-block:: none

        sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.5 1

        sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 2

        sudo update-alternatives --config python3


#.  izberi pravo številko

#.  testiramo kaj se skriva pod ukazom python3

    .. code-block:: none

        python3 -V



.. _python install pip:

Install pip
-----------

#.  pred inštalacijo je potrebno urediti, da se pod ukazom python3 nahaja python za katerega želimo inštalirati pip glej podrobnosti v [3][1]


#.  inštaliramo pip

    .. code-block:: none

        sudo apt-get install python3-pip


#.  upgradamo pip

    .. code-block:: none

        pip3 install --upgrade pip