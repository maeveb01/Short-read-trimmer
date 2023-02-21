# Python script that acts as a short-read trimmer

#### Reads in file with multiple Fasta sequences
#### Removes  last 5 nucleotides from sequence string (but not header)
#### Prints headers and trimmed sequences back to the screen
#### Each sequence is fully contained in one line.

Input:

>SRR1528876.srr.1 HISEQ:68:C4CMYACXX:8:1101:1432:2120
TATTTTCTATACCTATAAACTTAAATGTATCATAATTCATAATACAATAAT
>SRR1528876.srr.2 HISEQ:68:C4CMYACXX:8:1101:1468:2172
GGCCTTCAATTGCAGAAGTTTTTGAAGGGAGAATATTTGATCCTCACATAA
>SRR1528876.srr.7 HISEQ:68:C4CMYACXX:8:1101:1894:2091
GGGTCTTCAAACCGTTCCACACACCAGTGTAATGTGTCTGTTCACCAATCT

Output:

>SRR1528876.srr.1 HISEQ:68:C4CMYACXX:8:1101:1432:2120
TATTTTCTATACCTATAAACTTAAATGTATCATAATTCATAATACA
>SRR1528876.srr.2 HISEQ:68:C4CMYACXX:8:1101:1468:2172
GGCCTTCAATTGCAGAAGTTTTTGAAGGGAGAATATTTGATCCTCA
>SRR1528876.srr.7 HISEQ:68:C4CMYACXX:8:1101:1894:2091
GGGTCTTCAAACCGTTCCACACACCAGTGTAATGTGTCTGTTCACC

#### use the file 'short_reads.fa'


```python
file = 'short_reads.fa'
f = open(file, 'r')

line = ""
header = f.readline()[:-1]

while True:
    text = f.readline()
    
    if text.startswith('>'):
        final = line[:-5]
        print (header)
        print (final)
        header = text[:-1]
        line = ""
    if not text.startswith('>'):
        line = line + text[:-1]
    if text == '':
        final = line[:-4]
        print (header)
        print (final)
        break
        
```

    >SRR1528876.srr.1 HISEQ:68:C4CMYACXX:8:1101:1432:2120
    TATTTTCTATACCTATAAACTTAAATGTATCATAATTCATAATACA
    >SRR1528876.srr.2 HISEQ:68:C4CMYACXX:8:1101:1468:2172
    GGCCTTCAATTGCAGAAGTTTTTGAAGGGAGAATATTTGATCCTCA
    >SRR1528876.srr.7 HISEQ:68:C4CMYACXX:8:1101:1894:2091
    GGGTCTTCAAACCGTTCCACACACCAGTGTAATGTGTCTGTTCACC



```python

```


```python

```
