# 1. Call SNPs based on a ref and PE reads
## 1.1. filter PE reads using fastp 
```
fastp -l 45 -q 20 -w 15 -i $ind_1.fq.gz -I $ind_2.fq.gz -o $ind_clean_1.fq.gz -O $n_clean_2.fq.gz
```
## 1.2. build index for the ref
```
bwa index $ref
samtools faidx $ref
gatk CreateSequenceDictionary -R $ref -O $ref.dict
```
## 1.3. mapping
```
bwa mem -t 10 -R "@RG\tID:$ind\tPL:illumina\tLB:$ind\tSM:$ind" $ref $ind_clean_1.fq.gz $ind_clean_2.fq.gz| samtools view -Sb - > $ind.bam
```
## 1.4. sorting
```
samtools sort -@ 30 -m 2G -O bam -o $ind.sort.bam $ind.bam 
```
