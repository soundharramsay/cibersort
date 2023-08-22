# cibersort

input single cell mat 
column ---cell name
rows genes 

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


## cibersort output statistical test 

#http://www.sthda.com/english/wiki/unpaired-two-samples-t-test-in-r
###
dataset<-read.csv("./Downloads/CIBERSORTx_Job6_Results_foreazyR.csv",header=T)
colnames(dataset) <- c("celltype","cnt","cnt","cnt","e13*z8ko","e13*z8ko","e13*z8ko")

library(tidyr)

# Assuming your dataframe is named 'wide_df'
tall_df <- pivot_longer(dataset, 
                        cols = starts_with("cnt") | starts_with("e13"),
                        names_to = "Sample",
                        values_to = "Value")
table(tall_df$celltype)

PIEZ02_GAL_SN_df <- tall_df[tall_df$celltype == "PIEZ02_GAL_SN", ]

PIEZ02_GAL_SN_df<-PIEZ02_GAL_SN_df[,-1]


library(dplyr)
group_by(PIEZ02_GAL_SN_df,Sample) %>%
  summarise(
    count = n(),
    mean = mean(Value, na.rm = TRUE),
    sd = sd(Value, na.rm = TRUE)
  )

# A tibble: 2 × 4
Sample   count  mean     sd
<chr>    <int> <dbl>  <dbl>
  1 cnt          3 0.327 0.0471
2 e13*z8ko     3 0.405 0.0327





