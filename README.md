# miRBShunter
A pipeline to identify miRNA binding sites from Ago2-CLIP data by de novo motif finding

***  Requirements. ***

Required Python libraries are:

- Bio.Seq 

- wx (for the GUI)


Required programs installed and available in the path:

- Homer -> http://homer.salk.edu/homer/

- Meme Suite -> http://meme-suite.org/doc/download.html


Genome sequences in fasta files. You can download them from UCSC web site or you can find them in Homer folder. 


***  Installation. ***


Just simply untar the package in any destination folder:


         tar zxvf miRBShunter_v1.0.tgz ./


You'll find four folders:


./miRBShunter_scripts: contains all scripts included in the pipeline

./example_data: contains input files needed to run the pipeline

./example_temp and ./example_output: folders to be used to run the pipeline on the example files




*** Using the miRBShunte pipeline. ***


miRBShunter could be run either via command line (shell) or using the user-friendly GUI. To run the GUI easily type:


         python miRBShunter_GUI.py


Before running the GUI, the users may want to check if the library wx is already installed.


Or you can use the command line script miRBShunter_script.py.


Input files: 


peaks bed file: Coordinates of peaks found by peak calling tool. The file must contain 6 columns (chr, st, end, pval, reads, strand).


miRNA sequences file: a file with the most expressed miRNA in fasta format.



Examples files are provided in the example_data folder. 



         usage: python ./miRBShunter_make_script.py [options] [peaksbedfile] [mirnafastafile]



Options:


          -h, --help            show this help message and exit

          -o OUTDIR, --outdir=OUTDIR
                                directory for output files. Default is current directory.
          
          -t TEMPDIR, --tempdir=TEMPDIR
                                directory for temporary files. Default is current directory.
                                
          -d GENOMEFASTADIR, --genomefastadir=GENOMEFASTADIR
                                directory with genome fasta file. Default is current directory.
                                
          -b FASTABG, --fastaBG=FASTABG
                                file with background sequences in fasta format. If file is not provided, sequence scrumble will be done. Check Homer parameters for more details.
          
          -p PVALUE, --pvalue=PVALUE
                                pvalue threshold for peaks selection. Default is 0.001.
                                
          -r READS, --reads=READS
                                minimum number of reads for peaks selection. Default is 5.
                                
          -g GENOME, --genome=GENOME
                                Genome of the organism, either mm10 or hg19. Default mm10.
          
          -f PREFIX, --prefix=PREFIX
                                Prefix name for output files. Default is test.

                        
Example procedure:


          python ./miRBShunter_script.py -o example_output/ -t example_temp/ -p 0.1 -r 2 -d /home/silvia/programs/homer/data/genomes/mm10/ -g mm10 -f test -b ./example_data/scrambleBg.fasta ./example_data/example_file_peaks.bed ./example_data/mirna_fasta_seq.txt

Output files:


*.anno: peaks annotated with Homer

*.annstats: statistics on annotated peaks

meme_motif: folder containing the motif selected with the combined score in meme format

results_table.txt: A table containing the information about the heteroduplex and the duplex score. The table can be loaded on excel.


For questions/comments please drop us an email: silvia.bottini@unice.fr

