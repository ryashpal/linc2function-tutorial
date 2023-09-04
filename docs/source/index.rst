linc2function
=============

A Deep Learning Approach to assign functions to long noncoding RNA


System Requirements
-------------------

Hardware Requirements
~~~~~~~~~~~~~~~~~~~~~

A standard computer with around 16 GB RAM

Software Requirements
~~~~~~~~~~~~~~~~~~~~~

Python 3.6 virtualanv

Installation
------------

To run linc2functionPipeline in your system, please follow the below steps;

Clone linc2functionPipeline repository

.. code-block:: console

    (.venv) username@hostname:~$git clone https://gitlab.com/tyagilab/linc2functionpipeline.git

Change to linc2functionPipeline directory

.. code-block:: console

    (.venv) username@hostname:~$cd linc2functionpipeline

Create a virtual environment

.. code-block:: console

    (.venv) username@hostname:~$virtualenv -p python3.6 .venv

Activate the virtual environment

.. code-block:: console

    (.venv) username@hostname:~$source ./venv/bin/activate

Install Dependencies

.. code-block:: console

    (.venv) username@hostname:~$pip install -r requirements.txt



Usage
-----

For using Human Specific Model

.. code-block:: console

    (.venv) username@hostname:~$python3 main.py predict_hs_model <sequence> <model_path> <scalers_path>

For using Human Species Agnostic

.. code-block:: console

    (.venv) username@hostname:~$python3 main.py predict_sa_model  <sequence> <model_path> <scalers_path>

Contents
--------

.. toctree::

    introduction
    webpage
