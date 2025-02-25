# Annotate Genome
I made this create to annotate my vcf files in order to remove coding regions and flanking regions (10Kb) in order to do demographic modelling on neutral sites.
To start, you need to download the corresponding bed file from here (https://genome.ucsc.edu/cgi-bin/hgTables). In my case after selecting my desired reference genome, coding regions and bed format, a page with the bed file appear on the browser. I copied the link and downloaded like this:

```
wget -O coding_exons.bed "https://genome.ucsc.edu/cgi-bin/hgTables?hgsid=2468584971_w04caEyPqEtuFSwSq503otVCTDlU&boolshad.hgta_printCustomTrackHeaders=0&hgta_ctName=tb_knownGene&hgta_ctDesc=table+browser+query+on+knownGene&hgta_ctVis=pack&hgta_ctUrl=&fbUpBases=200&fbExonBases=0&fbIntronBases=0&fbQual=cds&fbDownBases=200&hgta_doGetBed=get+BED"
```
