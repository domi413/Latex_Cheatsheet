# General LaTeX Cheatsheet

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

## 2. Text Formatting

### 2.1 Basic Text Editing

- Italic: `\textit{text}`
- Bold: `\textbf{text}`
- Underline: `\underline{text}`
- Double Underline: Use `\underline{\underline{text}}` or define a new command in the preamble with `\def\doubleunderline#1{\underline{\underline{#1}}}` and then use `\doubleunderline{text}`

### 2.2 Paragraphs and New Lines

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

- Examples of list environments:

```Latex
% Unordered list
\begin{itemize}
    \item First item
    \item Second item
\end{itemize}

% Ordered list
\begin{enumerate}
    \item First item
    \item Second item
\end{enumerate}

% Description list
\begin{description}
    \item[Term] Definition of the term.
    \item[Concept] Explanation of the concept.
\end{description}
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





## 10. Setting PDF Metadata with `\hypersetup`

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