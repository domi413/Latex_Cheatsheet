[//]: # (Thanks to NaoPross for his template on HSR-Stud who encouraged me to write this doc)

# General LaTeX Cheatsheet

## Table of Contents
1. [Document Structure and Sections](#1-document-structure-and-sections)
   1. [Basic Document Structure](#11-basic-document-structure)
   2. [Creating Sections and Subsections](#12-creating-sections-and-subsections)
   3. [Table of Contents](#13-table-of-contents)
2. [Text Formatting](#2-text-formatting)
   1. [Basic Text Editing](#21-basic-text-editing)
   2. [Handling Special Characters](#22-handling-special-characters)
   3. [Paragraphs and New Lines](#23-paragraphs-and-new-lines)
   4. [Coloring Text and Elements](#24-coloring-text-and-elements)
   5. [Changing Text Size and Spacing](#25-changing-text-size-and-spacing)
3. [Math Expression](#3-math-expression)
   1. [Inline and Centered Math](#31-inline-and-centered-math)
   2. [Defining Vectors and Matrices](#32-defining-vectors-and-matrices)
4. [Creating Tables](#4-creating-tables)
   1. [Basic Table Structure](#41-basic-table-structure)
5. [Including Images and Figures](#5-including-images-and-figures)
   1. [Referencing a Figure](#51-referencing-a-figure)
   2. [Inserting a Figure](#52-inserting-a-figure)
   3. [Setting Image Path](#53-setting-image-path)
6. [List Environments](#6-list-environments)
7. [Footnotes](#7-footnotes)
8. [Customizing Document Layout](#8-customizing-document-layout)
   1. [Change Font](#81-change-font)
9. [Code Snippet](#9-code-snippet)
10. [Setting PDF Metadata](#10-setting-pdf-metadata)
11. [Managing Sources and Citations with Zotero](#11-managing-sources-and-citations-with-zotero)
12. [Miscellaneous](#12-miscellaneous)
    1. [Suggestion for Indentation](#121-suggestion-for-indentation)
    2. [Preferred LaTeX Compiler](#122-preferred-latex-compiler)
13. [Managing Complex LaTeX Projects with Multiple Files](#13-managing-complex-latex-projects-with-multiple-files)

## 1. Document Structure and Sections

### 1.1 Basic Document Structure

A LaTeX document typically starts with a document class declaration, followed by the inclusion of packages, and then the document content within `\begin{document}` and `\end{document}`:

```Latex
\documentclass{article}

\usepackage{package_name} % Add required packages

\begin{document}

% Document content goes here

\end{document}
```

### 1.2 Creating Sections and Subsections

- **Section**: Use `\section{Section Title}` to create a new section. Sections are numbered automatically.

- **Subsection**: Use `\subsection{Subsection Title}` within a section to create a subsection.

- **Subsubsection**: Use `\subsubsection{Subsubsection Title}` within a subsection for more detailed division.

- **Unnumbered Sections**: Add an asterisk (*) to create an unnumbered section or subsection, like `\section*{Title}`. The section also won't be visible in the table of content

Example:

```Latex
\section{Introduction}
This is the introduction text.

\subsection{Background}
Details about the background.

\subsubsection{Detailed Topic}
More specific details.

\section*{Acknowledgments}
Unnumbered section for acknowledgments.
```

### 1.3 Table of Contents

- Automatically generate a table of contents based on sections and subsections using `\tableofcontents`.

Example:

```Latex
\tableofcontents
\section{Introduction}
...
```

### 1.3.1 Clickable Table of Contents

To create a clickable Table of Contents in LaTeX, use the `hyperref` package. Simply add `\usepackage{hyperref}` to your document's preamble, and then use `\tableofcontents` where you want the ToC to appear. The `hyperref` package automatically turns all entries in the ToC into clickable links.

## 2. Text Formatting

### 2.1 Basic Text Editing

- Italic: `\textit{text}`
- Bold: `\textbf{text}`
- Underline: `\underline{text}`
- Double Underline: Use `\underline{\underline{text}}` or define a new command in the preamble with `\def\doubleunderline#1{\underline{\underline{#1}}}` and then use `\doubleunderline{text}`

### 2.2 Handling Special Characters

LaTeX reserves several characters for formatting and commands, which cannot be used directly in the text. Here's how to include these special characters in your document:

- **Backslash `\`**: Use `\textbackslash` for backslash, as it is used to start commands.
- **Tilde `~`**: Use `\textasciitilde` or `\~{}` for a tilde, often used for non-breaking spaces.
- **Dollar `$`**: Use `\$` for dollar signs, as `$` is used for entering math mode.
- **Percent `%`**: Use `\%` for percent signs, as `%` is used for comments.
- **Ampersand `&`**: Use `\&` for ampersands, as `&` is used for tabular alignment.
- **Underscore `_`**: Use `\_` for underscores, as `_` is used for subscripts in math mode.
- **Hash `#`**: Use `\#` for hash symbols, as `#` is used for macro parameters.
- **Curly Braces `{}`**: Use `\{` and `\}` for curly braces, as `{}` are used for grouping.
- **Caret `^`**: Use `\textasciicircum` or `\^{} ` for caret symbols, as `^` is used for superscripts in math mode.
- **Pipe `|`**: Use `\textbar` for pipe symbols, as `|` can be used in tabular and math environments.

Example usage in a LaTeX document:

```latex
This is a special character example: \% \$ \& \# \{ \} \_ \textasciitilde \textasciicircum \textbar
```

### 2.3 Paragraphs and New Lines

- **Paragraphs**: Start a new paragraph by leaving an empty line in the LaTeX code. Avoid using `\\` for breaking paragraphs.

    - Incorrect method:
        ```latex
        This is my first paragraph. \\
        This is my second paragraph.
        ```
    
    - Correct method:
        ```latex
        This is my first paragraph.

        This is my second paragraph.
        ```
      In this correct method, the second paragraph will start with an indent. If you prefer to not have this indent, you can use the `parskip` package.

- **Removing Indentation**: To remove the indentation at the beginning of paragraphs and add a bit of vertical space between paragraphs, include `\usepackage{parskip}` in your document's preamble.

- **Line Breaks**: Use `\\` or `\newline` for a new line within the same paragraph when necessary, though it's generally best to let LaTeX handle line breaks automatically.

### 2.4 Coloring Text and Elements

Coloring in LaTeX can enhance the visual appeal and clarity of your document. This can be achieved using the `xcolor` package, which provides a wide range of color options and functionalities.

#### 2.4.1 Adding the xcolor Package

First, include the `xcolor` package in your document's preamble:

```latex
\usepackage{xcolor}
```

You can specify options when loading `xcolor` to access more color models or predefined colors, like so:

```latex
\usepackage[usenames,dvipsnames,svgnames,table]{xcolor}
```

#### 2.4.2 Basic Text Coloring

To change the color of text:

```latex
\textcolor{color_name}{text}
```

For example:

```latex
\textcolor{blue}{This text will be blue.}
\textcolor{red}{This text will be red.}
```

#### 2.4.3 Defining Custom Colors

You can define your own colors:

```latex
\definecolor{mycolor}{RGB}{0,123,255} % RGB model
\definecolor{anothercolor}{HTML}{00FF00} % HTML color codes
```

And use them like this:

```latex
\textcolor{mycolor}{Custom colored text.}
```

#### 2.4.4 Coloring Backgrounds

To set the background color of a text block:

```latex
\colorbox{color_name}{text}
```

For a frame around the text with a background color:

```latex
\fcolorbox{frame_color}{background_color}{text}
```

#### 2.4.5 Advanced Coloring

- **Paragraphs**: You can apply color to entire paragraphs or larger text blocks using the `\color` command at the beginning of the paragraph.

- **Custom Environments**: Combine color commands with custom environments to colorize specific sections or elements consistently.

- **Math Mode**: Colors can also be applied within math mode to highlight equations or parts of equations.

### 2.5 Changing Text Size and Spacing

In LaTeX, you have the flexibility to adjust the text size and spacing to meet your specific formatting needs. This section covers how to change the text size and control vertical spacing.

#### 2.5.1 Changing Text Size

LaTeX provides several commands for adjusting the text size. These commands affect the text size within their scope (enclosed within curly braces `{}` or within a LaTeX group/environment).

Here are the most common text size commands, listed from smallest to largest (The font size in pt is only approximately and based on the default `article` class):

```latex
\tiny          % 5pt
\scriptsize    % 7pt
\footnotesize  % 8pt
\small         % 9pt
\normalsize    % 10pt
\large         % 12pt
\Large         % 14.4pt
\LARGE         % 17.28pt
\huge          % 20.74pt
\Huge          % 24.88pt
```

Example of usage:

```latex
This is {\small small text} and this is {\Large large text}.
```

#### 2.5.2 Customizing Text Size

For more specific text size requirements, you can use the `\fontsize{size}{baselineskip}` command, followed by `\selectfont`. 

Example:

```latex
\fontsize{12pt}{14pt}\selectfont
```

#### 2.5.3 Adjusting Vertical Spacing

Vertical spacing can be controlled using commands like `\vspace` and `\vfill`.

- **`\vspace{length}`**: Adds vertical space of the specified length. Can be negative.
- **`\vfill`**: Adds a variable amount of vertical space that expands as much as possible.

Example:

```latex
Text before space.
\vspace{10mm}
Text after space.
```

#### 2.5.4 Customizing Line Spacing

To adjust the line spacing for a portion of the document, use the `setspace` package and its commands:

```latex
\usepackage{setspace}
\singlespacing % Single line spacing
\onehalfspacing % One and a half line spacing
\doublespacing % Double line spacing
```

For a specific section:

```latex
\begin{spacing}{2.5}
Your text here.
\end{spacing}
```

#### 2.5.5 Paragraph Spacing

- **Customizing Paragraph Indent**: Use `\setlength{\parindent}{length}` to set the paragraph indent.
- **Customizing Paragraph Skip**: Use `\setlength{\parskip}{length}` to set the space between paragraphs.

Example:

```latex
\setlength{\parindent}{0em}
\setlength{\parskip}{1em}
```

## 3. Math Expression

### 3.1 Inline and Centered Math

- Centered Math: Use `\[ ... \]` for equations that you want to appear centered on a new line.
- Inline Math: Use `\( ... \)` for equations that appear inline with the text.

Example:

```Latex
Here is an inline equation \( x^2 + y^2 = z^2 \) and here is a centered equation:
\[ E = mc^2 \]
```

In LaTeX, it's recommended to use `\(...\)` for inline math and `\[...\]` for display math instead of `$...$` and `$$...$$` because:

1. `\(...\)` and `\[...\]` ensure proper spacing and formatting.
2. They are compatible with the `amsmath` package, which is widely used for advanced math typesetting.
3. `$...$` and `$$...$$` can cause issues in formatting and are not recommended in LaTeX, though they are originally from plain TeX.

### 3.2 Defining Vectors and Matrices

- Use different environments for matrices, depending on the brackets you want:

```Latex
\begin{bmatrix} % for square brackets []
    1 & 2 \\
    3 & 4
\end{bmatrix}

\begin{pmatrix} % for parentheses ()
    1 & 2 \\
    3 & 4
\end{pmatrix}
```

Other types:
- `matrix`: without brackets.
- `Bmatrix`: `{}` curly brackets.
- `vmatrix`: `| |` single vertical lines.
- `Vmatrix`: `|| ||` double vertical lines.

Here's a section about creating tables in LaTeX that you can add to your Markdown instruction:

## 4. Creating Tables

### 4.1 Basic Table Structure

1. **Begin with the `table` Environment**:
   - Use for floating placement, captions, and labels.
   - Placement specifiers: `htbp` (here, top, bottom, page of floats).
   - Example: `\begin{table}[htbp] ... \end{table}`

2. **Use the `tabular` Environment Within `table`**:
   - Define table format and structure.
   - Specify columns and alignments (`l` = left, `c` = center, `r` = right).
   - Separate rows with `\\` and columns with `&`.
   - Add horizontal lines with `\hline`.

#### 4.1.1 Commonly Used Specifiers

- **`table` Environment Specifiers**:
  - `h`: Place the table approximately at the same point it occurs in the text.
  - `t`: Position the table at the top of a page.
  - `b`: Place the table at the bottom of a page.
  - `p`: Place the table on a separate page of floats.
  - `!`: Override internal parameters for float placement.

- **`tabular` Environment Specifiers**:
  - `l`, `c`, `r`: Align columns left, center, or right.
  - `p{width}`, `m{width}`, `b{width}`: Paragraph columns with specified width and vertical alignment.
  - `|`: Add vertical lines between columns.

#### 4.1.2 Table Example

```latex
\begin{table}[htbp]
    \centering
    \begin{tabular}{lcr}
        \hline
        Left & Center & Right \\
        \hline
        Text1 & Text2 & Text3 \\
        Text4 & Text5 & Text6 \\
        \hline
    \end{tabular}
    \caption{Example of a simple table}
    \label{table:example}
\end{table}
```

#### 4.1.3 Advanced Formatting

- **Column Separators**: Use `|` for vertical lines between columns.
- **Row Spacing**: Adjusstomize using `@{...}`.
- **Enhanced Lines**: For professional tables, use `\toprule`, `\midrule`, `\bottomrule` from the `booktabs` package.

#### 4.1.4 Notes

- It's often best to keep tables as simple and uncluttered as possible.
- For complex tables, consider using pat with `\vspace{...}`.
- **Column Spacing**: Cuckages like `booktabs` for better visual quality.
- Remember that large tables may need to be scaled or adjusted to fit the page width.


## 5. Including Images and Figures

### 5.1 Referencing a Figure

Use the `\ref` command within the text:

```Latex
... as shown in Figure \ref{fig:that-figure}.
```

### 5.2 Inserting a Figure

- Use the `figure` environment with placement specifiers. Only use specifiers if necessary; otherwise, LaTeX's default placement is often sufficient.

```Latex
\begin{figure}[htbp] % h: here, t: top, b: bottom, p: separate page, !: force location.
  \centering
  \includegraphics[width=0.5\textwidth]{path/to/your/image.png}
  \caption{Meaningful description}
  \label{fig:that-figure}
\end{figure}
```

- Reference the figure in your text as shown above.

### 5.3 Setting Image Path

- Specify relative or absolute path if the figure is not in the same directory:

```Latex
\includegraphics{../Images/your_image.png}
```

- Use `\graphicspath` in the preamble (globally) for multiple directories:

```Latex
\graphicspath{{./images/}{./photos/}}
```

## 6. List Environments

LaTeX provides various list environments which can be customized to fit different needs. Here are the common list types and ways to customize them:

### 6.1 Unordered List (Itemize)
- **Basic Usage**:
    ```latex
    \begin{itemize}
        \item First item
        \item Second item
    \end{itemize}
    ```
- **Changing Bullet Styles**:
    Customize bullet points by redefining `\labelitemi` (first level), `\labelitemii` (second level), etc.
    ```latex
    \renewcommand{\labelitemi}{$\star$}
    \renewcommand{\labelitemii}{$\cdot$}
    ```

### 6.2 Ordered List (Enumerate)
- **Basic Usage**:
    ```latex
    \begin{enumerate}
        \item First item
        \item Second item
    \end{enumerate}
    ```
- **Changing Numbering Style**:
    Redefine `\labelenumi`, `\labelenumii`, etc., for different levels.
    ```latex
    \renewcommand{\labelenumi}{\Roman{enumi}.}
    \renewcommand{\labelenumii}{(\alph{enumii})}
    ```

### 6.3 Description List
- **Basic Usage**:
    ```latex
    \begin{description}
        \item[Term] Definition of the term.
        \item[Concept] Explanation of the concept.
    \end{description}
    ```

### 6.4 Customizing Spacing
- Adjust spacing between items and paragraphs in lists using `\itemsep` and `\parsep`.
    ```latex
    \begin{itemize}
        \setlength{\itemsep}{5pt}
        \setlength{\parsep}{3pt}
        \item Item 1
        \item Item 2
    \end{itemize}
    ```

### 6.5 Nested Lists
- Lists can be nested within each other for more complex structures.
    ```latex
    \begin{enumerate}
        \item First item
            \begin{itemize}
                \item Nested item
                \item Another nested item
            \end{itemize}
        \item Second item
    \end{enumerate}
    ```

## 7. Footnotes

- Adding a footnote:

```Latex
This is some text with a footnote.\footnote{This is the footnote text.}
```

## 8. Customizing Document Layout

- Changing margins and customizing header/footer:

```Latex
\usepackage[margin=2.1cm]{geometry} % Change margins

\usepackage{fancyhdr} % Customize header and footer
\pagestyle{fancy}
\fancyhead[L]{Left Header}
\fancyhead[C]{Center Header}
\fancyhead[R]{Right Header}
\fancyfoot[L]{Left Footer}
\fancyfoot[C]{Center Footer}
\fancyfoot[R]{Page \thepage}
```

### 8.1 Change font

If you're tired of Latex's default font, you can change it with the `fontspec` package.

Define a new font with `\setmainfont{Calibri}`

If you're on Linux and want to use a MS office font, you can download the fonts somewhere on github and copy them to `/usr/share/fonts`

you can create a new folder inside `/fonts` e.g. `sudo mkdir /usr/share/fonts/win`

## 9. Code Snippet

- Import the package: `\usepackage{listings}`
- Example for Java code:

```Latex
\begin{lstlisting}[language=Java, caption=Java Example]
// This is a comment
public class HelloWorld {
    public static void main(String[] args) {
        // Prints Hello, World!
        System.out.println("Hello, World!");
    }
}
\end{lstlisting}
```

- Create custom syntax highlighting with `\lstdefinestyle{name}` and use it with `\lstset{style=name}`.

## 10. Setting PDF Metadata

In LaTeX, you can use the `\hypersetup` command from the `hyperref` package to set metadata for the compiled PDF file. This metadata includes the title, author, subject, and other properties that can be viewed in PDF readers, which helps in organizing and finding documents, especially in digital libraries or personal archives.

First, ensure that the `hyperref` package is included in your preamble:

```latex
\usepackage{hyperref}
```

Then, use the `\hypersetup` command to set your PDF metadata:

```latex
\hypersetup{
    pdftitle={Your Document Title},
    pdfauthor={Your Name},
    pdfsubject={The Subject of Your Document},
    pdfkeywords={Keyword1, Keyword2, Keyword3},
    % other settings like colorlinks, linkcolor, etc.
}
```

## 11. Managing Sources and Citations with Zotero

#### 11.1.1 Setup
- **Install Zotero**: [Download](https://www.zotero.org/download/) and install.
- **Install Better BibTeX (BBT)**: Add-on for Zotero. Automates BibTeX export. [Installation guide](https://retorque.re/zotero-better-bibtex/installation/).

#### 11.1.2 Exporting BibTeX File
- **Auto-Export with BBT**: Set up BBT to auto-export your Zotero library to a `.bib` file. Configure this in Zotero's BBT settings.

#### 11.1.3 LaTeX Document Setup
- **Bib File**: Place `.bib` file in LaTeX project directory.
- **Bibliography Command**: Add `\bibliography{filename}` to your LaTeX file (replace `filename` with your `.bib` file name, without extension).
- **Bibliography Style**: Define style with `\bibliographystyle{stylename}` (e.g., `plain`, `IEEEtran`).

#### 11.1.4 Citation in LaTeX
- **Cite Command**: Use `\cite{key}` in the document, where `key` is the citation key from the `.bib` file.
  
#### 11.1.5 Example Code Snippet
```latex
\documentclass{article}
\usepackage{hyperref}
\begin{document}

\section{Introduction}
As discussed in \cite{Smith2020}, the results...

% (normally) at the end of the document insert:
\bibliographystyle{IEEEtran}
\bibliography{myreferences} % Assumes a file named 'myreferences.bib'

\end{document}
```

#### 11.1.6 Compilation
- **Compile Sequence**: Run LaTeX, BibTeX, LaTeX, and LaTeX again to process citations and update the bibliography.

## 12. Miscellaneous

### 12.1 Suggestion for indentation

LaTeX is very weird at first, because on one hand it feels like a programming language where indentation should be mandatory, but on the other hand it kinda isn't. Here I have some (opinionated) suggestions to make indentation in your LaTeX sources consistent.


1. Use an indentation of 2 spaces. This is because you can get many nested expressions. You could go with 4, but keep in mind that you will need a wider screen.

2. Indent only `\begin{...} \end{...}` blocks and open parenthesis `()` brackets `[]` or braces `{}`. Example:  
    ```latex
    \begin{table}
      \begin{tabular}{l l}
        \toprule
        % ...
      \end{tabular}
      \caption{
        A decently indented table.
        \label{tab:another-table}
      }
    \end{table}
    ```
    Another example for maths:
    ```latex
    \[ % yes these count as brackets
      y = \bar{y} \pm \sigma_y
        \approx f(\bar{\vec{x}}) \pm \sqrt{\sum_{i=1}^m \left( % and these as well
          \partial_{x_i} f(\bar{\vec{x}}) \sigma_{x_i}
        \right)^2}
    \]
    ```

3. The only exception is `\begin{document}` and `\end{document}`, which should not be indented. **This is the only exception**. The reasoning behind this is that (unless you use `\include`) everything will be be indented which is not very useful.

4. Section headings etc. do not cause indentation. You should think of these macros as just putting there the title, not as a block.
    ```latex
    \section[VHSIC Hardware Description Language (VHDL)]{
      VHDL: Very high-speed integrated circuits program
      Hardware Description Language
    }

    \subsection{Basic syntax and identifiers}

    In VHDL an identifier is a case insensitive string composed of \texttt{A-Z a-z 0-9 \_} that
    \begin{itemize}
      \item is not a keyword,
      \item does not start with a number or \texttt{\_},
      \item does not have two or more \texttt{\_} in a row.
    \end{itemize}
    ```

5. Align tables to the `&`, if the content is short. For example
    ```latex
    \begin{table}
      \centering
      \begin{tabularx}{\linewidth}{>{\ttfamily}c l X}
        \toprule
        \textrm{Value} & Meaning & Usage \\
        \midrule
        U & Uninitialized  & In the simulator \\
        X & Undefined      & Simulator sees a bus conflict \\
        0 & Force to 0     & Low state of outputs \\
        1 & Force to 1     & High state of outputs \\
        Z & High Impedance & Three state ports \\
        W & Weak Unknown   & Simulator sees weak a bus conflict \\
        L & Weak Low       & Open source outputs with pull-down resistor \\
        H & Weak High      & Open drain output with pull-up resistor \\
        - & Don't care     & Allow minimization \\
        \bottomrule
      \end{tabularx}
      \caption{
        Possible values for \vhdl{std_logic} signals.
        \label{tab:std-logic-1164-types}
      }
    \end{table}
    ```

### 12.2 Preferred LaTeX Compiler

If you're currently using pdfLaTeX, consider switching to XeLaTeX or LuaLaTeX. These modern compilers provide several advantages, including:

1. **Advanced Font Handling**: Easily use any font on your computer (with the `fontspec` package), including OpenType and TrueType, unlike the limited font options in pdfLaTeX.

2. **Robust Unicode Support**: Ideal for multilingual documents and special characters, offering seamless support for Unicode, a feature where pdfLaTeX often falls short.

3. **Modern Features and Flexibility**: LuaLaTeX integrates Lua scripting for advanced programmable capabilities within your documents.

4. **Enhanced Micro-typography**: LuaLaTeX enhances the appearance and readability of your document with advanced typesetting features.

5. **Reduced Package Conflicts**: Both compilers are aligned with current LaTeX development, ensuring better compatibility with new packages and fewer conflicts.

## 13. Managing Complex LaTeX Projects with Multiple Files

When working on large LaTeX projects, such as a thesis or a book, it's beneficial to split the content into multiple files for better organization and manageability. Here's a guide to setting up a structured folder system for such projects:

#### 13.1.1 Folder Structure

A well-organized folder structure is crucial for managing complex documents. Here's an example of an effective structure:

```
myproject/
│
├── main.tex            # Main document file
│
├── chapters/           # Folder for chapter files
│   ├── chapter1.tex
│   ├── chapter2.tex
│   └── ...
│
├── images/             # Folder for images
│   ├── img1.png
│   ├── img2.jpg
│   └── ...
│
├── styles/             # Folder for custom style files
│   ├── mystyle.sty
│   └── ...
│
├── bib/                # Folder for bibliography files
│   ├── references.bib
│   └── ...
│
└── appendices/         # Folder for appendices
    ├── appendixA.tex
    └── ...
```

#### 13.1.2 Main Document (main.tex)

The `main.tex` file serves as the root document that integrates all other parts. Use `\input` or `\include` commands to add chapters and appendices.

Example:

```latex
\documentclass{book}
\usepackage{...} % Import necessary packages

% Document settings go here

\begin{document}

\tableofcontents

\include{chapters/chapter1}
\include{chapters/chapter2}
% Include other chapters as needed

\appendix
\include{appendices/appendixA}
% Include other appendices as needed

\bibliographystyle{plain}
\bibliography{bib/references}

\end{document}
```

#### Using `\input` vs. `\include` in LaTeX Documents

In LaTeX, the commands `\input` and `\include` are used to incorporate external files into a main document, but they serve different purposes and have distinct behaviors that suit particular use cases. The `\input{file}` command is like a text copy-paste operation; it takes the content of `file.tex` and inserts it at the point where the command is used, with no added spacing or new pages. It is ideal for pulling in sections of text, preambles, or LaTeX configurations, allowing for modular document organization without affecting the document's flow.

On the other hand, `\include{file}` is more suitable for adding whole chapters or sections that should begin on new pages in larger documents such as books or theses. This command inserts the content of `file.tex` starting on a new page, and importantly, it can be used with the `\includeonly{}` command. This feature can be leveraged during the drafting phase to compile only specific sections of the document, thereby speeding up the compilation process—a particularly handy tool when working with lengthy texts. 

One must note that `\include` cannot be nested, and it automatically adds a page break, which would be undesirable for smaller inclusions like figures, tables, or code snippets. In summary, use `\input` for seamless, continuous inclusions, and reserve `\include` for structuring larger documents into separately compiled units, each beginning on a new page.

#### 13.1.3 Best Practices for Multi-File Documents

1. **Consistency**: Maintain consistent formatting across all files.
2. **Modularity**: Keep each chapter or section in its own file for easy editing and organization.
3. **Version Control**: Use a version control system like Git to manage changes, especially when collaborating.
4. **Regular Backups**: Regularly backup your project folder.
5. **Compilation**: Compile the `main.tex` file, not the individual chapter files.
6. **Relative Paths**: Use relative paths for including files and images.
7. **Comments and Documentation**: Comment your code for clarity, especially when working in teams.

#### 13.1.4 Compilation

With a multi-file structure, compilation remains straightforward. Compile `main.tex`, and LaTeX will automatically include the other files as specified.
