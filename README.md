# ImputeSCOPA
imputeSCOPA: a Python software for imputing high-dimensional numeric data using the random forest algorithm. Adapted from the original C++ imputeSCOPA implementation.

Requirements:
1. Python 3.10 or newer
2. NumPy ≥1.24, <3

Organisation:
impute_scopa.py: main imputation program
requirements.txt: required Python dependency
test_impute_scopa.py: automated tests
VALIDATION.md: validation results
data: example dataset

To install:
From the project folder:
python3 -m pip install -r requirements.txt
No compilation is required. Display available options with:
python3 impute_scopa.py -h

To run
a. Command line:
python3 impute_scopa.py -i data/3phigh_missing.txt -S {} -n {} -m {} -v {} -o python_imputed.txt
b. Python or Spyder:
Make the project folder available on your Python import path, then run:
from impute_scopa import impute_scopa, read_table, write_table
header, ids, data = read_table("data/3phigh_missing.txt")
imputed = impute_scopa(data, seed={}, num_trees={}, maxiter={})
write_table("python_imputed.txt", header, ids, imputed)
c.R version: 
source('csImputeSCOPA.R') 
imp <- csImputeSCOPA(output, maxiter={}, num.trees={}, verbose= TRUE, seed={}) 
write.table(data.frame("ID"=rownames(imp),imp), "../data/tstout.txt", quote=F, row.names=F, sep="\t")

If you are looking for duplication, you need to use the same seed in all a,b and c.
