# img_scripts

A collection of scripts dealing with local stores of IMG data.

## ```img_metadata_scanner.rb```
Scan through a taxon metadata file, filtering by particular fields. Only certain fields are extracted.

Print out the genus and species of each archaeon:
```sh
$ img_metadata_scanner.rb Domain=Archaea --output-fields "Genus,Species" |head
Thermococcus	gammatolerans
Methanolobus	
Pyrobaculum	
Methanobacterium	sp.
Sulfolobus	islandicus
Desulfurococcus	mucosus
Haladaptatus	paucihalophilus
Methanothermobacter	thermautotrophicus
Methanosarcina	barkeri
Methanobrevibacter	smithii
```

Print out the headers available for filtering or reporting
```sh
$ img_metadata_scanner.rb -l |less
taxon_oid
Domain
Status
Proposal Name
Genome Name / Sample Name
Sequencing Center
Phylum
Class
Order
Family
Genus
Species
Genome ID
NCBI Taxon ID
RefSeq Project ID
GenBank Project ID
Strain
...
```

The data is comes from a metadata file, which is obtained through the instructions below. You can specify the location of
this file to the script using the ```--img-metadata-file``` flag, or you can set the ```IMG_METADATA_FILE``` environment
variable if you are too lazy to type it in each time.

Go to IMG > Genome Browser: http://img.jgi.doe.gov/cgi-bin/w/main.cgi?section=TaxonList&page=taxonListAlpha

In the Table Configuration section:
* Genome Field     > Click All
* Project Metadata > Click All
* Data Statistics  > Click All

Click Display Genomes Again. In the Genome Browser section > Click Select All. Finally, click the Export button.

PS/ Don't trust the IMG metadata _too much_. There are some big mistakes, e.g. in the 16S copy number

PS2/ What have I done to create the FIXED metadata?
* I have deleted two occurences of "\r" (^M) by ""
* taxonoid 2515154013 has two extra fields: remove the two cells containing "Human wound, cranian"
* Replace cells containing "-1" by ""
* Replaced 'Marine archaeal group 1 BG20 (Nitrosoarchaeum limnia BG20)' by 'Nitrosoarchaeum limnia BG20'

(Download instructions kindly contributed by @fangly / Florent Angly)

## Copyright

Copyright (c) 2013 Ben J. Woodcroft. See LICENSE.txt for
further details.

