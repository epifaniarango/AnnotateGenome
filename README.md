# Annotate Genome
I created this create to annotate my vcf files in order to remove coding regions and flanking regions (10Kb) in order to do demographic modeling on neutral sites.
To start, you need to download the corresponding bed file from here (https://genome.ucsc.edu/cgi-bin/hgTables). In my case after selecting my desired reference genome, coding regions and bed format, a page with the bed file appear on the browser. In my case I downloaded coding regions, 5UTR and 3UTR. You can download the bed files like this and the chromosome sizes:

```
wget -O coding_exons.bed "https://genome.ucsc.edu/cgi-bin/hgTables?hgsid=2468584971_w04caEyPqEtuFSwSq503otVCTDlU&boolshad.hgta_printCustomTrackHeaders=0&hgta_ctName=tb_knownGene&hgta_ctDesc=table+browser+query+on+knownGene&hgta_ctVis=pack&hgta_ctUrl=&fbUpBases=200&fbExonBases=0&fbIntronBases=0&fbQual=cds&fbDownBases=200&hgta_doGetBed=get+BED"
wget -O 3utr.bed "https://genome.ucsc.edu/cgi-bin/hgTables?hgsid=2468523179_EVZ2MavoVDBXYC8QRlkhHknaI6vA&boolshad.hgta_printCustomTrackHeaders=0&hgta_ctName=tb_knownGene&hgta_ctDesc=table+browser+query+on+knownGene&hgta_ctVis=pack&hgta_ctUrl=&fbUpBases=200&fbExonBases=0&fbIntronBases=0&fbQual=utr3&fbDownBases=200&hgta_doGetBed=get+BED"
wget -O 5utr.bed "https://genome.ucsc.edu/cgi-bin/hgTables?hgsid=2468523179_EVZ2MavoVDBXYC8QRlkhHknaI6vA&boolshad.hgta_printCustomTrackHeaders=0&hgta_ctName=tb_knownGene&hgta_ctDesc=table+browser+query+on+knownGene&hgta_ctVis=pack&hgta_ctUrl=&fbUpBases=200&fbExonBases=0&fbIntronBases=0&fbQual=utr5&fbDownBases=200&hgta_doGetBed=get+BED"
wget http://hgdownload.soe.ucsc.edu/goldenPath/hg19/bigZips/hg19.chrom.sizes -O genome.chrom.sizes

```

In my case, I am only interested in the autosomal chromosomes. So, I will use the following command to keep only those:
```
grep -E "^chr([1-9]|1[0-9]|2[0-2])\s" genome.chrom.sizes > autosomes.chrom.sizes
```

To run this script, you will need bcftools, bedtools and snakemake installed. Modify -j according to your needs: 
```
snakemake -s FilterOutCDS.snakemake  -j 5 --rerun-incomplete
```

