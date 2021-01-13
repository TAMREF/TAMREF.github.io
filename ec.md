---
layout: page
title: EC@MWT
permalink: /ec/
---

## Enumerative Combinatorics Study @SSHS MWT


{%assign lecs = site.static_files | where: "pdf/enumcomb", true%}

{%assign sorted_lecs = lecs | sort: file.basename%}

{%for lec in sorted_lecs%}

- <a href = "{{ site.baseurl }}{{ lec.path }}">{{lec.basename}}</a> </li>

{%endfor%}


