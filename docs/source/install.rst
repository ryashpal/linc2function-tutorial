Installation
------------

Make sure you satisfy the requirements provided below to ensure smooth working of the utility;

System Requirements
~~~~~~~~~~~~~~~~~~~

Hardware Requirements
"""""""""""""""""""""

A standard computer with around 16 GB RAM

Software Requirements
"""""""""""""""""""""

Python 3.8 or above

Step-by-step procedure
----------------------

Follow the below steps to install linc2function in your computer.


Login
~~~~~

Upon login to a system and opening a terminal, the following prompt should appear, where the ``user`` is the user name and the ``hostname`` is the hostname of the system.

.. code-block:: console

   user@hostname:~$


Change directory
~~~~~~~~~~~~~~~~

From the home directory which will be open by default, change to a suitable directory on your computer where the utility needs to be installed. For example, in this tutorial we have changed to ``workspace`` directory.

.. code-block:: console

   user@hostname:~$ cd workspace

Clone
~~~~~

In the workspace directory, clone the current version of EHR-QC repository from the GitHub.

.. code-block:: console

    username@hostname:~$git clone https://gitlab.com/tyagilab/linc2functionpipeline.git

Open linc2function
~~~~~~~~~~~~~~~~~~

Open the linc2function directory that is downloaded from GitHub after cloning.

.. code-block:: console

    username@hostname:~$cd linc2functionpipeline

Python virtual environment
~~~~~~~~~~~~~~~~~~~~~~~~~~

The Python virtual environment encaptulates all the libraries required for the linc2function. All the necessary libraries listed in a requirements.txt file that can be found at the root of the repository. Below are the instructions to create and install dependancies in the Python virtual environment.

.. note::
   linc2function requires Python version 3.8 or higher. For installing Python, please refer the below link: https://www.python.org/downloads/

Create virtual environment
""""""""""""""""""""""""""

Inside the linc2functionpipeline directory, create a new Python virtual enviroment to conveniently manage all the dependencies required for the utility.

.. code-block:: console

    username@hostname:~/workspace/linc2functionpipeline$virtualenv -p python3 .venv

Activate virtual environment
""""""""""""""""""""""""""""

After creating the Python virtual enviroment, activate the virtual enviroment to start using it for subsequent commands. The prompt will change with ``(.venv)`` appearing in front of it as shown below;

.. code-block:: console

    username@hostname:~/workspace/linc2functionpipeline$source ./venv/bin/activate
    (.venv) user@hostname:~/workspace/linc2functionpipeline$

Install dependencies
""""""""""""""""""""

Install all the required dependencies listed in the requirements.txt file in the newly created Python virtual environment.

.. code-block:: console

    (.venv) user@hostname:~/workspace/linc2functionpipeline$pip install -r requirements.txt
