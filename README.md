# MSCA-DN: LaTeX Template

> [!NOTE]
> This is an unofficial template based on the unofficial [MSCA-PF](https://github.com/alexfikl/msca-pf).


LaTeX class and template for Marie Skłodowska-Curie Actions Postdoctoral Fellow
grant applications.

* Details and original template is provided
  [here](https://rea.ec.europa.eu/funding-and-grants/horizon-europe-marie-sklodowska-curie-actions/msca-postdoctoral-fellowships_en)
  (calls are updated each year).

* For the official editable version of the template, you must start the submission
  process. The template will then be available on the left-hand side in a section
  named "Download Part B templates".

* For a similar template for the Doctoral Network see
  [msca-dn](https://github.com/pgarner/msca-dn).

Compilation
-----------

The resulting PDF files are included for easy viewing. The template is compatible
with both PDFLaTeX and LuaLaTeX/XeLaTeX. It can be easily build with e.g. `latexmk`
```sh
latexmk -pdflua msca-pf-part-b1-template.tex
latexmk -pdflua msca-pf-part-b2-template.tex
```

Documentation
-------------

This packages provides the `msca-pf` class that is based on the
KOMA-script `scrartcl` class and accepts any options meant for it. It can
be used as
```tex
\documentclass[12pt,layoutgrid,draftproposal]{msca-pf}

% ... preamble ...

\begin{document}

% ... content ...

\end{document}
```

The class has two options meant for drafting:

* `layoutgrid`: overlays a grid on top of each page to check margins and
  other alignment issues.
* `draftproposal`: adds helpful drafting options, such as line numbers and
  a time stamp.

It also provides a few useful commands that can be used in the proposal. The
following commands are mandatory:

* `mscaidentifier`: the call identifier, e.g. `HORIZON-MSCA-2022-PF-01`. This
  should be set to the appropriate version by default.
* `mscaproject`: the acronym for the project.

Additionally, there are also some commands to help constructing the CV and other
little tables in the submission:

* `mscaorgoverview`: an environment (wrapper around `tabular`) that defines
  the table template from Section 5.1 for participating organisations. This is a
  fixed 6 column table.
* `mscaorgcapacity`: an environment (wrapper around `longtable`) that defines
  the table template from Section 5.2 for participating organisations. This is a
  fixed 2 column table.
* `cvitem`: an environment to define a nicely aligned CV item.
* `\cventry{dates}{name}{details}{location}`: a generic entry in the CV. Use
  `\cventryitem` to get one already wrapped in the `cvitem` environment.
* `\cvpub{date}{authors}{title}{journal}`: a publication. Use
  `\cvpubitem` to get one already wrapped in the `cvitem` environment.
* `\cvdetail{name}{description}`: a additional description for an entry. This
  must be added in the same `cvitem` environment as the entry itself to use the
  same alignment.

A Gantt chart must also be provided in the proposal. There are some LaTeX packages,
e.g. [pgfgantt](https://ctan.org/pkg/pgfgantt?lang=en), that can be used to
create such charts. However, you can also just use a third party application,
export the chart as a PNG or PDF, and include it like that.

Fonts
-----

The official MSCA guidelines require the Times New Roman font on Windows or
macOS and the Nimbus Roman font on Linux. When using PDFLaTeX this package
uses the `newtx` fonts. When using XeLaTeX or LuaLaTeX, we try to load
the Times New Roman font and, if it is not available, the Nimbus Roman font.

If these do not work for you, you can load fonts yourself using e.g.
```tex
% on PDFLaTeX
\usepackage{newtxtext}
\usepackage{newtxmath}

% on XeLaTeX / LuaLaTeX
\setmainfont{Times New Roman}
```

## License

[Creative Commons Zero v1.0 Universal](https://creativecommons.org/public-domain/cc0/) (CC0-1.0).
