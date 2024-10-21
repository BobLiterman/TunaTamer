# TunaTamer  
#### Robert Literman, Amanda Windsor, Elizabeth Hunter  
#### US Food and Drug Administration, Human Foods Program  
#### Last Push: 2024-10-21  

This is a walkthrough of the development of a bioinformatics pipeline tailored towards identifying tuna and related fishes. First, we're going to generate a mitochondrial and nuclear pangenome for the *Thunnus* species to aid in species identification.  

1. **Genomic Data**  
    -  To build the raw mitochondrial and nuclear pangenomes, we downloaded:
       -  WGS data from the [NCBI SRA database](https://www.ncbi.nlm.nih.gov/sra) for tuna and closely related species  
       -  Complete mitochondrial genomes from [MitoFish](https://mitofish.aori.u-tokyo.ac.jp/) for any Scombridae species  
  
<div style="margin-left: 120px;">

| MitoFish Species                                | MitoFish Accession ID |
|-------------------------------------------------|-----------------------|
| Acanthocybium solandri                          | NC_067731             |
| Auxis rochei                                    | NC_005313             |
| Auxis thazard                                   | NC_005318             |
| Euthynnus affinis                               | NC_025934             |
| Euthynnus alletteratus                          | NC_004530             |
| Gasterochisma melampus                          | NC_020671             |
| Grammatorcynus bilineatus                       | NC_051931             |
| Gymnosarda unicolor                             | NC_022496             |
| Katsuwonus pelamis                              | NC_005316             |
| Rastrelliger brachysoma                         | NC_013485             |
| Rastrelliger kanagurta                          | NC_019624             |
| Sarda orientalis                                | NC_060588             |
| Sarda sarda                                     | NC_052756             |
| Scomber australasicus                           | NC_013725             |
| Scomber colias                                  | NC_013724             |
| Scomber japonicus                               | NC_013723             |
| Scomber scombrus                                | NC_006398             |
| Scomberomorus brasiliensis                      | NC_088025             |
| Scomberomorus cavalla                           | NC_008109             |
| Scomberomorus concolor                          | NC_033531             |
| Scomberomorus munroi                            | NC_021390             |
| Scomberomorus munroi x Scomberomorus semsciatus | NC_021392             |
| Scomberomorus niphonius                         | NC_016420             |
| Scomberomorus semsciatus                        | NC_021391             |
| Scomberomorus sierra                            | NC_033887             |
| Thunnus alalunga                                | NC_005317             |
| Thunnus albacares                               | NC_014061             |
| Thunnus atlanticus                              | NC_025519             |
| Thunnus maccoyii                                | NC_014101             |
| Thunnus obesus                                  | NC_014059             |
| Thunnus orientalis                              | NC_008455             |
| Thunnus thynnus                                 | NC_014052             |
| Thunnus thynnus thynnus                         | NC_004901             |
| Thunnus tonggol                                 | NC_020673             | 

</div>

2. **Mitochondrial/Nuclear Read Separation**  
    - For each sample, we used [*bbmap*](https://jgi.doe.gov/data-and-tools/software-tools/bbtools/bb-tools-user-guide/bbmap-guide/) to map the WGS against all MitoFish mitochondrial genome assemblies. Any reads that mapped were partitioned as mitochondrial, and all other reads were partitioned as putatively nuclear.  
