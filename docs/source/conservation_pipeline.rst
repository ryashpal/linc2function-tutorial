Conservation Pipeline
---------------------

* Download hg38.7way.maf.gz file from https://hgdownload.soe.ucsc.edu/goldenPath/hg38/multiz7way/
* Create bed file containing well conserved regions across 6 species
Run script maf_to_bed.py
python maf_to_bed.py hg38.7way.maf hg38.7way.bed
* Create bed file for predicted binding sites
Make sure the predicted binding sites for each testing sequence is saved under `Sequence_lncRNA` and directory `Sequence_lncRNA_bed` is created
python binding_sites_to_bed.py
* Install bedtools
For instructions: https://bedtools.readthedocs.io/en/latest/content/installation.html)
* Run bedtools
Make sure `Sequence_lncRNA_intersect` is created
https://gitlab.com/yram0006/linc2function_validation_data/-/blob/master/ucr_overlaps/run_bed_tools.sh
* Analyse the results
for f in ./*;do echo $f; cat $f | awk -F'\t' '{print $4}' | sort | uniq -c; done
Count and obtain the overlaps and non-overlaps
