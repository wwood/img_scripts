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
 etc.
 etc.
```

Randomly sample each species in the genus Shigella:
```sh
$ img_metadata_scanner.rb --output-fields "taxon_oid,Genus,Species" Genus=Shigella --sample Species
649989998 Shigella	dysenteriae
637000261	Shigella	boydii
637000265	Shigella	flexneri
640427143	Shigella	sonnei
645058835	Shigella	sp.
```
In contrast, without sampling:
```sh
$ img_metadata_scanner.rb --output-fields "taxon_oid,Genus,Species" Genus=Shigella
649989998  Shigella	dysenteriae
641522650	Shigella	boydii
637000263	Shigella	flexneri
637000265	Shigella	flexneri
638341196	Shigella	dysenteriae
637000264	Shigella	flexneri
637000261	Shigella	boydii
640427143	Shigella	sonnei
646862341	Shigella	flexneri
640427142	Shigella	dysenteriae
645058835	Shigella	sp.
```


## The metadata file
The data comes from a metadata file, which is obtained through the instructions available from the [bio-img_metadata biogem documentation](https://github.com/wwood/bioruby-img_metadata). You can specify the location of
this file to the script using the ```--img-metadata-file``` flag, or you can set the ```IMG_METADATA_FILE``` environment
variable if you are too lazy to type it in each time.

## Copyright

Copyright (c) 2013 Ben J. Woodcroft. See LICENSE.txt for
further details.

