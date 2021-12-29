# 1. Call SNPs based on a ref and PE reads
## 1.1 filter PE reads using fastp 
`fastp -l 45 -q 20 -w 15 -i $ind_1.fq.gz -I $ind_2.fq.gz -o $ind_clean_1.fq.gz -O $n_clean_2.fq.gz`
