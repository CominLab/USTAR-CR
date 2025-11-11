# USTAR-CR (Unitig STitch Advanced constRuction with Colors Reordering)
## Overview
USTAR-CR is a k-mers set compressor, with colors.

It is based on the ideas of [UST](https://github.com/medvedevgroup/UST) 
and [prophAsm](https://github.com/prophyle/prophasm) 
for computing an SPSS representation (aka simplitigs) for the given k-mers set.

Additionally, it exploits the possibility of reusing already visited nodes to achieve better compression as shown by [Matchtigs](https://github.com/algbio/matchtigs).

## Dependencies
Good news, there are no dependencies. 
However, you'll need [GGCAT](https://github.com/algbio/ggcat) 
in order to compute a colored compacted de Bruijn graph (cdBG) of your multi-fasta file.

## How to download and compile
* `git clone https://github.com/CominLab/USTAR-CR`
* `cd USTAR-CR`
* `cmake . && make -j 4`

## How to run USTARC
Run GGCAT first: 
* `./GGCAT -k <kmer-size> -e -c <your-multi-fasta>`

Then USTAR-CR:
* `./ustar -k <kmer-size> -i <GGCAT-output> -D7`

To use the best heuristic, and the optimized RLE for colors, add `-s+u -x-c -e opt_rle`:
* `./ustar -k <kmer-size> -i <GGCAT-output> -D7 -s+c -x-c -e opt_rle`

See the help `./ustar -h` for details and advanced options.


USTAR-CR produces two separete files, one for the sequences and one for the colors.
These files can be merge into a single FASTA file, where the colors are inserted into the headers with a format similar to GGCAT, with the script "fasta-meger.py".


## References

If you are using USTAR-CR in your research, please cite (paper under sumbission) 

```
USTAR-CR: Efficient and Compact Compression of k-mer Sets Through Colored de Bruijn Graphs
```
.
