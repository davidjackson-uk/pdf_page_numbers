# PDF Page Numbers
With huge thanks to [Chloé-Agathe Azencott](https://www.cazencott.info/index.php/post/2015/04/30/Numbering-PDF-Pages)

A tex and pdftk process for adding page numbers to a pdf file. Useful for bates numbering.

1. Begin by installing ```pdftk``` and ```pdflatex``` if you don't already have them.

```
sudo apt-get install pdftk
sudo apt-get install pdflatex
```

2. Note how many pages your pdf file has. For this example we will assume there are 456 pages.
   
3. Create a plain text file with the following contents and save it as numbers.tex
   
```
 \documentclass[36pt,a4paper]{article}
 \usepackage{multido}
 \usepackage{xcolor}
 \usepackage[hmargin=.8cm,vmargin=1.5cm,nohead,nofoot]{geometry}
 \color{red}
 \LARGE
 \begin{document}
 \multido{}{456}{\vphantom{x}\newpage}
 \end{document}
```

 
 4. Use ```pdflatex``` to create a pdf file from the .tex file:
    ```
    pdflatex numbers.tex
    ```
   
5. Let's assume that the file you want to add the page numbers to is called ```myfile.pdf```, and you want to create a version of it with numbered pages called ```myfile_numbered.pdf```

    ```
    pdftk myfile.pdf multistamp numbers.pdf output myfile_numbered.pdf
    ```
6. You will now have a new file called myfile_numbered.pdf.
   
8. Do a happy dance.    

