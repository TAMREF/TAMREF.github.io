---
layout: page
title: EC@MWT
permalink: /ec/
---

## Enumerative Combinatorics Study @SSHS MWT

{% for lec in site.static_files %}
- {{lec.path}} {{lec.basename}}
{% endfor %}

{%assign lecs = site.static_files | where: "path", "/pdf/enumcomb/"%}

{%assign sorted_lecs = lecs | sort: file.basename%}

{%for lec in sorted_lecs%}
{%if lec.path includes "/pdf/enumcomb"%}
- <a href = "{{ site.baseurl }}{{ lec.path }}">{{lec.basename}}</a>
{% endif %}
{% endfor %}


