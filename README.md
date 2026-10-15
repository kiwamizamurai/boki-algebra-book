# Learning University Mathematics through the Algebra of Bookkeeping

A textbook for undergraduates that teaches university mathematics (sets and maps, monoids and groups, linear algebra, graph theory, and an introduction to category theory) through double-entry bookkeeping. The book is written in English with Quarto, and its main theorems are formalized in Lean 4.

## Aims

- **Readers.** Undergraduates. The book assumes high-school mathematics and no knowledge of bookkeeping.
- **Method.** Bookkeeping procedures such as journal entries, accounts, and the trial balance are redefined as mathematical objects. For example, the book shows how the rule "total debits equal total credits" becomes a statement about a group.
- **Machine-checked proofs.** The main theorems are formalized in Lean 4 and checked with `lake build`.
- **Research methods.** Part 0 uses the book's own topic as a worked example of a literature search, so readers can run the same process on their own topics.

## Tools

| Purpose | Tool | Reason |
| --- | --- | --- |
| Writing and typesetting | [Quarto](https://quarto.org/) book projects | One source produces HTML and PDF. Mathematics is written in LaTeX. Cross-references and BibTeX citations work out of the box. |
| PDF typesetting | LuaLaTeX with LuaTeX-ja | The bibliography contains Japanese titles, so the PDF needs Japanese typesetting support. |
| Formal proofs | Lean 4 with Mathlib (a Lake project in `lean/`) | Mathlib provides the algebra, linear algebra, and category theory the book needs. |
| Bibliography | `references.bib` | Cited from the text through Quarto. |

### How Quarto and Lean fit together

Quarto does not run Lean code, so the two have separate jobs.

1. Lean code lives in the Lake project under `lean/`. `lake build` checks every proof.
2. The book includes the relevant parts of those files with `{{< include >}}` and shows them as `lean` code blocks.
3. CI runs both `lake build` and `quarto render`, so every Lean snippet in the book is code that compiles.

### Claude Code setup

The book is written and formalized with Claude Code. Every skill and MCP server is pinned to a version.

| Purpose | Name | Pinned version | Location |
| --- | --- | --- | --- |
| Proofreading Japanese text | yomiyasu | tag v1.1.2 | `.claude/settings.json` |
| Proofreading English text | humanizer | tag v3.1.0 | `.claude/settings.json` |
| Checking English text | stop-slop | commit 8da1f03 | `.claude/skills/stop-slop/` |
| Lean formalization and proof workflow | lean4-skills (plugin `lean4`) | tag v4.11.3 | `.claude/settings.json` |
| Lean library design and style | writing-lean-proofs (Trail of Bits) | commit e1f86a3 | `.claude/skills/writing-lean-proofs/` |
| Lean goal states for Claude | lean-lsp-mcp | 0.31.0 | `.mcp.json` |

Repositories without tags are vendored at a fixed commit under `.claude/skills/`. Each folder's `SOURCE.md` records where the files came from.

The working rules are in `.claude/rules/` (written in Japanese): `research.md` (no guesses; check every claim, and ask the user when a check needs their action), `proofreading.md` (proofread every text with the skills above: yomiyasu for Japanese, humanizer and stop-slop for English), and `comments.md` (no comments in code or configuration files).

## Bibliography

The references used in the book are in [`references.bib`](references.bib). Every entry was checked against Crossref, arXiv, CiNii Research, an Internet Archive catalog record, a publisher's page, or the paper itself. The searches that found them are recorded in [`research/log.md`](research/log.md), and Part 0 of the book walks through them.

## Contents (plan)

The book has 15 parts and 106 chapters. One small company's transactions (opening the business, purchases, sales, a loan, depreciation, and the year-end closing) are used from start to finish. Each part rewrites the same transactions in a new mathematical language: sets, groups, vectors, graphs, and categories.

Each chapter ends with:

- **Exercises**, both by hand and on the running bookkeeping example;
- **Formalization**, the chapter's definitions and main theorems in Lean 4 (matching files in `lean/`);
- **Further reading**, the sources the chapter draws on.

Chapters are marked ★ (core), ★★ (standard), or ★★★ (advanced).

### Reading paths

| Path | Parts | Reader |
| --- | --- | --- |
| Shortest (one semester) | 0, II, III, IV, and the ★ chapters of V | First- and second-year students meeting university mathematics for the first time |
| Algebra | II–VI, IX | Students who want a solid base in group theory and linear algebra |
| Discrete mathematics | II–IV, VII, VIII, X | Students heading toward graph theory and category theory |
| Formalization | II–IV, XI | Students who want to write proofs in Lean |
| Applied accounting | II, IV, V, XII, XIII | Accounting and economics majors who want mathematics as a tool |
| Research | 0, I, XIV, and any other part | Students planning a thesis in this area |

### Preface

### Part 0: Research Methods (drafted)

1. Asking a researchable question
2. Collecting keywords
3. Finding the first paper
4. Following citations
5. Searching literature in Japanese
6. Finding older literature
7. Reading papers
8. Organizing what you find
9. Limits and pitfalls
10. Writing up the survey

### Part I: The Language of Mathematics and Proof

1. Propositions and logic ★
2. Writing proofs, and a first proof in Lean ★
3. Sets: the set of accounts and the set of transactions ★
4. Maps: a journal entry as a map from accounts to amounts ★
5. Relations and equivalence relations: records that give the same balance ★
6. Orders: the chart of accounts as an order ★★
7. Induction and recursion: the trial balance stays balanced after any number of entries ★
8. Number systems: building the integers from pairs, and the T-account ★★

### Part II: Bookkeeping Basics (no mathematics)

1. What bookkeeping is ★
2. The accounting equation ★
3. Transactions and journal entries ★
4. Accounts and posting ★
5. The trial balance ★
6. Closing the books ★
7. Financial statements ★
8. The running example: one company's year ★

### Part III: Monoids and Groups

1. Binary operations ★
2. Monoids: the journal as a sequence of entries ★
3. Groups ★
4. Subgroups and cosets ★★
5. Homomorphisms: computing balances from the journal ★
6. Quotient groups and the first isomorphism theorem: merging accounts ★★
7. Direct products and direct sums: several currencies and goods ★★
8. Free abelian groups: accounts as a basis ★★

### Part IV: The Group of Differences (the Pacioli Group)

1. T-accounts as pairs ★
2. The Pacioli group [@ellerman2014] ★
3. Journal entries and the trial balance, formalized ★
4. The algebraic meaning of the accounting equation ★
5. The Grothendieck group ★★
6. The monoid of records and the group of balances [@ozawa2026] ★★
7. Multi-dimensional bookkeeping [@ellerman1986] ★★
8. An algebra of errors ★★

### Part V: Linear Algebra

1. Vector spaces: balance vectors ★
2. Matrices and linear maps: journal entries as matrices ★
3. Matrix bookkeeping [@leech1986; @ozawa2023matrix] ★
4. Kernel, image, and rank ★
5. Systems of linear equations: recovering transactions from statements ★
6. Least squares and generalized inverses [@arya2000] ★★
7. Inner products and duality: prices as linear functionals ★★
8. Aggregation and projection [@arya2004] ★★
9. Eigenvalues and diagonalization ★★
10. Input-output analysis ★★★

### Part VI: Rings, Modules, and Order

1. Rings and fields ★★
2. Modules [@rambaud2010] ★★
3. Tensor products ★★★
4. Ordered groups ★★
5. Lattices and the chart of accounts ★★

### Part VII: Graphs and Networks

1. Graphs: accounts as vertices, transactions as edges ★
2. The incidence matrix ★
3. Flows and conservation ★★
4. Trees and spanning trees ★★
5. Cycle space and cut space ★★
6. An introduction to graph homology ★★★
7. Bookkeeping graphs [@liang2023] ★★★

### Part VIII: Category Theory

1. Categories ★★
2. Functors and natural transformations ★★
3. Universal properties ★★
4. Adjunctions ★★★
5. Monoidal categories and string diagrams ★★★
6. Spans and cospans: partita doppia [@katis2008] ★★★

### Part IX: Time and Change

1. Sequences and difference equations ★
2. Series and present value ★
3. Derivatives and integrals: stocks and flows ★★
4. Differential equations ★★
5. Triple-entry bookkeeping [@ijiri1986] ★★
6. Probability and estimates ★★

### Part X: Computation and Information

1. Automata [@rambaud2005] ★★
2. The ledger as a data structure ★
3. Relational databases ★★
4. Plain-text accounting ★
5. Error detection ★★
6. Types that rule out unbalanced entries ★★★

### Part XI: Formalizing Bookkeeping in Lean

1. Lean 4 basics ★
2. Using Mathlib ★
3. Defining accounts and journal entries ★
4. Building the Pacioli group ★★
5. Proving that the trial balance balances ★★
6. Comparing with the Grothendieck group in Mathlib ★★★
7. Matrix bookkeeping in Lean ★★★
8. Graphs and incidence matrices in Lean ★★★
9. Checking the running example in Lean ★★
10. Running a formalization project ★★

### Part XII: Applications in Accounting

1. Consolidation ★★
2. Foreign currency translation ★★
3. Cost accounting ★★
4. Management accounting and optimization ★★
5. The cash flow statement, algebraically [@ozawa2023cashflow] ★★
6. Auditing and anomaly detection ★★

### Part XIII: Applications in Economics

1. National accounts ★★
2. Input-output tables ★★
3. Social accounting matrices ★★★

### Part XIV: History and Research Directions

1. The origins of double entry [@stone2021] ★
2. Negative numbers and bookkeeping [@peters1978] ★★
3. The algebra of accounts, from Sprague onward [@sprague1880; @sprague1908; @ijiri1965; @ellerman1985] ★★
4. Research in Japanese [@ozawa2023matrix] ★★
5. Open problems and thesis topics ★★★

### Appendices

- A. Notation
- B. Glossary of bookkeeping and mathematical terms (English and Japanese)
- C. The running example: all transactions and books
- D. Lean tactic reference
- E. Solutions to exercises
- F. Bibliography
- G. Index

The keys in brackets refer to entries in `references.bib`. They mark which sources a chapter will draw on; the content of each chapter will be written after reading those sources in full.

## Directory layout

```
boki-algebra-book/
├── README.md
├── _quarto.yml
├── index.qmd
├── references.bib
├── research/
│   └── log.md
├── chapters/
│   └── p00-research/
├── mise.toml
└── lean/
    ├── lakefile.toml
    ├── lean-toolchain
    └── BokiAlgebra.lean
```

## Building

| Task | Command |
| --- | --- |
| Render the book to HTML | `quarto render --to html` |
| Preview while writing | `quarto preview` |
| Check the Lean proofs | `cd lean && lake build` |

### Setting up the environment

Tool versions are pinned in `mise.toml` (Quarto 1.10.19, elan 4.2.4) and `lean/lean-toolchain` (Lean 4.35.0). Mathlib is pinned to the tag `v4.35.0` in `lean/lakefile.toml`.

1. Install Quarto and the elan installer with mise.
   ```sh
   mise trust && mise install
   ```
2. mise installs only the elan installer (`elan-init`), so install elan into `~/.elan` once. `--no-modify-path` leaves your shell configuration unchanged; `mise.toml` adds `~/.elan/bin` to `PATH`.
   ```sh
   "$(mise where github:leanprover/elan)/elan-init" -y --no-modify-path --default-toolchain none
   ```
3. Install the Lean version named in `lean/lean-toolchain`.
   ```sh
   cd lean && elan toolchain install "$(cat lean-toolchain)"
   ```
4. Fetch Mathlib and its prebuilt cache, then build.
   ```sh
   lake update && lake exe cache get && lake build
   ```

PDF output also needs TeX Live with LuaLaTeX and LuaTeX-ja.

## Status

- [x] README
- [x] Plan of contents
- [x] Quarto book scaffold (`_quarto.yml`, `index.qmd`)
- [x] Part 0 drafted
- [x] Lean project scaffold
- [ ] PDF typesetting settings
- [ ] CI for `lake build` and `quarto render`
- [ ] Parts I–XIV

## License

Not decided yet. One option is CC BY-SA 4.0 for the text and Apache 2.0 for the Lean code.
