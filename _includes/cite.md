{% if biblist %}
{% assign biblist = biblist | sort %}
#### References

{:#bibliography}
{% for bibitem in biblist %}
{% assign ref = site.data.bibliography[bibitem] %}
1. {:#{{ bibitem }}}{{ ref.authors | join: ", " }}, {{ ref.year }}: _{{ ref.title }}_, {{ ref.cite }}.

   {:.hlist}
   {% if ref.mr %}
   * mr: <a href="https://www.ams.org/mathscinet-getitem?mr={{ ref.mr }}">{{ ref.mr }}</a>
   {% endif %}
   {% if ref.zbl %}
   * zbl: <a href="https://zbmath.org/?q=an:{{ ref.zbl }}">{{ ref.zbl }}</a>
   {% endif %}
   {% if ref.arxiv %}
   * arxiv: <a href="https://arxiv.org/abs/{{ ref.arxiv }}">{{ ref.arxiv }}</a>
   {% endif %}
   {% if ref.isbn %}
   * isbn: <a href="https://books.google.com/books?isbn={{ ref.isbn }}">{{ ref.isbn }}</a>
   {% endif %}
   {% if ref.doi %}
   * doi: <a href="https://doi.org/{{ ref.doi | uri_escape }}">{{ ref.doi }}</a>
   {% elsif ref.url %}
   * <a href="{{ ref.url | uri_escape }}">{{ ref.url | remove_first: 'http://' | remove_first: 'https://' }}</a>
   {% endif %}

{% endfor %}
{% endif %}
