---
layout: page
title: EC@MWT
permalink: /ec/
---

## Enumerative Combinatorics Study @SSHS MWT

```liquid
{%assign lecs = site.static_files | where: “pdf/enumcomb”, true%}

{%assign sorted_lecs = lecs | sort: file.basename%}

<ul>

{%for lec in sorted_lecs%}

<li> <a href = “{{ site.baseurl }}{{ file.path }}”>{{file.basename}}</a> </li>

{%endfor%}

</ul>
```

