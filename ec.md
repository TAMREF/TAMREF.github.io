---
layout: page
title: EC@MWT
permalink: /ec/
---

## Enumerative Combinatorics Study @SSHS MWT

{%assign sorted_lecs = site.static_files | sort: "path"%}

{%for lec in sorted_lecs%}
{%if lec.path contains "/pdf/enumcomb"%}
- <a href = "{{ site.baseurl }}{{ lec.path }}"> {{lec.basename}} </a>
{% endif %}
{% endfor %}


