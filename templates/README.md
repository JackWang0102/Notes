# LaTeX note templates

These templates follow the 11 pt article layout of `causal_basics.tex` and
`NE-EFIpf.tex`, with a title, table of contents, mathematical environments,
TikZ support, and the existing `math_command.tex` notation.

| Template | Use |
| --- | --- |
| `general-note.tex` | A new subject, concept, or short mathematical note |
| `causal-basics-note.tex` | Causal question, assumptions, identification, estimation, and sensitivity |
| `NE-EFI-proof-note.tex` | Probability preliminaries, Wasserstein bounds, Jacobian control, and proof audit |
| `course-note.tex` | Lecture or topic notes, including learning theory, SA, and Markov chains |

## Start a note

Run these commands from the repository root:

```sh
cp templates/general-note.tex my_topic.tex
latexmk -pdf my_topic.tex
```

Choose a different template in the `cp` command as needed. Edit the title,
then replace each `\notetodo{...}` with your content. The blue TODO text is
deliberate and compiles as ordinary LaTeX. Copy a section or theorem block
when you need another one, giving each label a unique name.

Keep new notes in the repository root so `notes-preamble.tex`,
`math_command.tex`, and `ref.bib` resolve consistently. To compile a template
directly, also run from the repository root:

```sh
latexmk -pdf templates/general-note.tex
```

To add references, insert citations such as `\cite{LiangKS2024EFI}` using
keys from `ref.bib`, then uncomment the two bibliography commands at the
bottom of the note. `latexmk` runs BibTeX and the required LaTeX passes.

## Shared formatting

Edit `notes-preamble.tex` to change the formatting of all new notes that
load it. Put reusable mathematical notation in `math_command.tex` and
topic-specific commands in the individual note after the preamble input.
The new preamble retains the existing separate counters for each theorem
type; definitions, examples, assumptions, and remarks use upright text.

Existing notes are untouched. They retain their own preambles unless you
choose to migrate them. `causal_basics.tex` and `NE-EFIpf.tex` currently have
identical contents and titles; the causal template provides a fresh causal
outline without replacing either source file.
