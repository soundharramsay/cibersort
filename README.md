# cibersort

input single cell mat 

data.frame':	23684 obs. of  738 variables:
 $ Gene                : chr  "C9orf152" "RPS11" "ELMO2" "CREB3L1" ...
 $ Malignant           : num  0 135.79 0 0 1.78 ...
 $ Malignant.1         : num  0 153.4 13.1 0 0 ...
 $ Malignant.2         : num  0 296.924 0.358 0 0 ...
 $ Malignant.3         : num  0 283.82 5.16 0 0 ...
 $ Malignant.4         : num  0 313 0 0 0 ...
 $ Malignant.5         : num  0 323.528 0.927 0 0 

 sed '1 s/^/gene /' iN_ctrl_z8KO_gene_count_matrix.txt > temp_file.txt
mv temp_file.txt iN_ctrl_z8KO_gene_count_matrix.txt


