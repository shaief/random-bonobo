To manipulate PDF files, i use the PDF Toolkit (pdftk) from [PDF Labs](https://www.pdflabs.com/).

### Merge pages from different PDFs:
```
pdftk A=file1.pdf B=file2.pdf C=file3.pdf D=file4.pdf cat A1-65 B1 A65 C1 A69 D1-end output desired_file.pdf
```

from [here](https://linuxcommando.blogspot.co.il/2013/02/splitting-up-is-easy-for-pdf-file.html).

### Add text/image on top of PDF files:

```
pdftk <original.pdf> multistamp <multistamp.pdf> output <output.pdf>
```
**Important notice**: if the multistamp.pdf is shorter than the original.pdf, the final page of the multistamp.pdf will be added to the rest of the document. Relevant usecases: if one would like to add a header only to the first page of a PDF file - they should create a multistamp.pdf with two pages - the first will have the additional text and the second should remain empty.
