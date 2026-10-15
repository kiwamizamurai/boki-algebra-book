# Research log

All searches below were run on 2026-10-15.

## Web search (Google)

- Query: `"algebra" bookkeeping double-entry book filetype:pdf`
  - Results included a PDF of Ellerman, "The Mathematics of Double Entry Bookkeeping," on ellerman.org, and a PDF of Ellerman, "On Double-Entry Bookkeeping: The Mathematical Treatment," on arXiv.
  - Kept: ellerman1985, ellerman2014.
- Query: `"algebra of accounts" OR "algebra of accounting" OR "bookkeeping algebra" book pdf`
  - Several result snippets cited Sprague, "The Algebra of Accounts," 1880.
  - One result was a PDF of a book on accounting history on a document-sharing site. Not used.

## Connected Papers

- Graph with origin ellerman2014: built. Nodes kept: ellerman1985, ellerman1986, rambaud2010, leech1986, arya2000, arya2004, peters1978, stone2021. Nodes rejected as off topic included a study of accounting firms in Jing Zhou and a study of the indenture system in Fiji.
- Graph with origin rambaud2010: built. Nodes kept: nehmer1997, rambaud2005.
- Graph with origin arya2000: blocked. Message: log in to view more graphs; monthly graph limit reached.
- Graph with origin "Momentum Accounting and Triple Entry Bookkeeping: Exploring the Dynamic Structure of Accounting Measurements": blocked with the same message.

## Semantic Scholar Academic Graph API

- Unauthenticated `paper/search` requests: refused with "Too Many Requests."

## Google Scholar

- Query: `"double-entry" bookkeeping "category theory" OR categorical accounting monoidal`
  - Results included Katis, Sabadini, Walters, "On partita doppia." Kept: katis2008.
- Query: `accounting "graph theory" OR "network" double-entry Arya Fellingham linear algebra`
  - Results included Liang, "Bookkeeping graphs: Computational theory and applications," and Arya et al. 2000 and 2004. Kept: liang2023.
- Query: `axiomatization accounting Mattessich OR Ijiri OR Tippett double entry axioms`
  - Results included Ijiri, "Axioms and structures of conventional accounting measurement." Kept: ijiri1965.
- Query (Japanese): `簿記 代数 構造 OR 複式簿記 数学 群`
  - Results included three papers by 小澤圭都 in the Waseda University repository.
- Query (Japanese): `小澤圭都 複式簿記`
  - Three papers by this author with PDFs, and one co-authored paper without a PDF. Kept: ozawa2023matrix, ozawa2023cashflow, ozawa2026.

## arXiv API

- `au:Ellerman AND abs:bookkeeping`: 1 result, arXiv:1407.1898.
- `ti:"partita doppia"`: 1 result, arXiv:0803.2429.

## Crossref API

- Free-text queries (`query.bibliographic`) for every journal article and conference paper in `references.bib`.
- Ijiri 1965: the best match without a date filter was a 2018 reprint in *Accounting, Economics, and Law: A Convivium*. With `filter=until-pub-date:1966`, the best match was the original in *The Accounting Review* 40(1), with the author recorded as "Tjiri."
- Rambaud et al. 2010: found with `filter=from-pub-date:2009,until-pub-date:2011` (World Scientific, DOI 10.1142/7445).
- Some browser requests were refused with HTTP 429; the same queries succeeded later from the command line.

## CiNii Research

- `簿記代数` (all record types): 1 result, ozawa2023matrix (商学研究科紀要 97, pp. 79–96, 2023-11-21).
- Title of ozawa2026: 1 result (The Bulletin of the Graduate School of Commerce 102, pp. 167–183, 2026-03-18).

## Internet Archive

- Advanced search, title "philosophy of accounts", creator "Sprague": 8 records, dated 1908, 1920, 1922, 1972.
- Advanced search, title "book-keeper", years 1879–1882: 2 records (The Book Keeper vol. 2 no. 19, 24 May 1881; a microform of The practical book-keeper, 1882). No 1880 issue.
- Search "algebra of accounts": the catalog record of *Four classics on the theory of double-entry bookkeeping* (Garland, 1982), whose contents list Sprague's "The algebra of accounts."

## Publisher pages

- Taylor & Francis, DOI 10.4324/9781315886411: edited by Richard Brief, first published 1982, eBook 2013-11-26. The table of contents lists "The Algebra of Accounts." with the note "(Written expressly for The Book-keeper.)" and the author shown as "Charles E. Spraoue."

## Full texts downloaded

- Downloaded with the user's permission: arXiv:1407.1898, arXiv:0803.2429, and the three Ozawa papers from the Waseda University repository.
