Conservation Pipeline
---------------------

Installation
~~~~~~~~~~~~

Follow the below steps to install linc2function_validation_data in your computer.


Login
"""""

Upon login to a system and opening a terminal, the following prompt should appear, where the ``user`` is the user name and the ``hostname`` is the hostname of the system.

.. code-block:: console

   user@hostname:~$


Change directory
""""""""""""""""

From the home directory which will be open by default, change to a suitable directory on your computer where the utility needs to be installed. For example, in this tutorial we have changed to ``workspace`` directory.

.. code-block:: console

   user@hostname:~$ cd workspace

Clone
"""""

In the workspace directory, clone the current version of linc2function_validation_data repository from the GitHub.

.. code-block:: console

    username@hostname:~/workspace$git clone https://gitlab.com/yram0006/linc2function_validation_data.git

Open linc2function_validation_data
""""""""""""""""""""""""""""""""""

Open the linc2function_validation_data directory that is downloaded from GitHub after cloning.

.. code-block:: console

    username@hostname:~/workspace/linc2function_validation_data$cd linc2function_validation_data

Open ucr_overlaps
"""""""""""""""""

Open the ucr_overlaps directory that is downloaded from GitHub after cloning.

.. code-block:: console

    username@hostname:~/workspace/linc2function_validation_data$cd ucr_overlaps

Download data
~~~~~~~~~~~~~

Download the multiple sequence alignment file `hg38.7way.maf.gz` from https://hgdownload.soe.ucsc.edu/goldenPath/hg38/multiz7way/ by running the following command;

.. code-block:: console

    username@hostname:~/workspace/linc2function_validation_data/ucr_overlaps$wget https://hgdownload.soe.ucsc.edu/goldenPath/hg38/multiz7way/hg38.7way.maf.gz

From this file, we can obtain the well conserved regions amonst 7 different species;

1. Human
2. Chimp
3. Rhesus
4. Dog
5. Mouse
6. Rat
7. Opossum


Create .bed files
~~~~~~~~~~~~~~~~~

Conserved Regions
"""""""""""""""""

The multiple sequnce alignment files containing conserved regions are to be converted into .bed format containing start and end co-oridate positions of the reference genome (Human) to make it comparable with the predicted binding sites. The following utility function can be used in this case;

.. code-block:: console

    username@hostname:~/workspace/linc2function_validation_data/ucr_overlaps$python maf_to_bed.py hg38.7way.maf hg38.7way.bed

Binding Sites
"""""""""""""

Next, the predicted binding sites are to be converted into .bed format containing start and end co-oridate positions of the reference genome (Human) to make it comparable with the conserved regions. The following utility function can be used in this case;

Make sure the predicted binding sites for each testing sequence is saved under `Sequence_lncRNA` and directory `Sequence_lncRNA_bed` is created before running the command.

.. code-block:: console

    username@hostname:~/workspace/linc2function_validation_data/ucr_overlaps$python binding_sites_to_bed.py

Install bedtools
~~~~~~~~~~~~~~~~

To compare the intersection of the above two .bed files, which essentially gives the binding sites which are well conserved we user bedtools library. Instructions regarding installation of this library can be found here: https://bedtools.readthedocs.io/en/latest/content/installation.html

Run bedtools
~~~~~~~~~~~~

To find the overlap between the bed files for the binding sites corresponding to every transcript, we have created another utility function. This function iterates though all the files in the Sequence_lncRNA_bed directory and invokes the intersection command. Please make sure Sequence_lncRNA_intersect directory is created before running this script as all the results will be saved under this directory.

.. code-block:: console

    username@hostname:~/workspace/linc2function_validation_data/ucr_overlaps$sh run_bed_tools.sh


Analyse output
~~~~~~~~~~~~~~

The output from the above command gives the overlaps for each binding site indivdually. To aggregate the results at transcript level and obtain the number of overlapping binding sites that are predicted for each species, the following script might be executed;

.. code-block:: console

  for f in ./*;do echo $f; cat $f | awk -F'\t' '{print $4}' | sort | uniq -c; done
