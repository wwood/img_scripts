# img_scripts

A collection of scripts dealing with local stores of IMG data.

## ```img_metadata_scanner.rb```
Scan through a taxon metadata file, filtering by particular fields. Only certain fields are extracted.

Print out the genus and species of each archaeon:
```sh
$ img_metadata_scanner.rb Domain=Archaea --output-fields "Genus,Species" |head
DEBUG img_metadata_scanner: Using environment variable IMG_METADATA_FILE to define path to IMG metadata file /srv/whitlam/bio/db/img/4.0/metadata/img_metadata_4_0_FIXED.csv
 INFO img_metadata_scanner: Using 1 filters.
 INFO img_metadata_scanner: Found 4700 taxons in the IMG metadata file
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

## Copyright

Copyright (c) 2013 Ben J. Woodcroft. See LICENSE.txt for
further details.

