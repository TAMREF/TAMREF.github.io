---
layout: page
title: EC@MWT
permalink: /ec/
---

## Enumerative Combinatorics Study @SSHS MWT

{% for lec in site.static_files %}
- {{lec.path}} {{lec.basename}}
{% endfor %}

{%assign sorted_lecs = site.static_files | sort: file.basename%}

{%for lec in sorted_lecs%}
{%if lec.path contains "/pdf/enumcomb"%}
- <a href = "{{ site.baseurl }}{{ lec.path }}">{{lec.basename}}</a>
{% endif %}
{% endfor %}


