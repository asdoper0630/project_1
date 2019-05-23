# project_1. cibersort

1. 다운로드 받은 파일을 rotate시켜 파이썬으로 sample별 파싱이 쉽게 변경
- ncol : gene symbol, nrow : sample name 형식으로
- testmake.py(#1_1) 사용; output= test.txt
2. test.txt에서 tumor sample만을 추출
- TCGA ID의 4번 칼럼이 -01*- 인 것만 추출
- only.py(#1_2) 사용; output= data_tumor_only.txt
3. 다시 CIBERSORT에 사용 가능하게 rotate
- data_re_transpose.py 사용; output= data_tumor_only_retransposed.txt

CIBERSORT option
- NON-ABSOLUTE
- signature     : LM22
- permutations  : 100
- data          : https://gdac.broadinstitute.org/ - HNSC - data browse - mRNAseq - illuminahiseq_rnaseqv2-RSEM_genes_normalized
- DISABLE quantile normalization : TRUE

code 1-1. rotate table to analyze data in R ConsensusClusterPlus package
python code 1_1 : testmake.py
- input   = CIBERSORT_LM22_sep.txt
- output  = CIBERSORT_LM22.sep_T.txt

4. R에서 위 output을 넣어 clustering
5. 클러스터링 결과의 heatmap 확인
6. 최적의 k값에서 클러스터링 결과에 따라 itemconsensus의 최댓값인 클러스터# 확인 및 저장
