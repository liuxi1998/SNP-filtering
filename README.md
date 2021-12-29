# Call SNPs based on a ref and PE reads
## filter PE reads using fastp 
`fastp -l 45 -q 20 -w 15 -i $q1 -I $q2 -o $n_clean_1.fq.gz -O $n_clean_2.fq.gz`
