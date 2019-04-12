---
layout: default
---
# Semana a semana

{% assign semanas = site.data.semanas | sort %}
{% for semana_hash in semanas reversed %}
{% assign numero_semana = semana_hash[0] %}
{% assign semana = semana_hash[1] %}

## Semana {{numero_semana}}
{{semana.descripcion}}

{% if semana.entrega %}

### Para entregar
{% assign fecha = semana.entrega.fecha %}
La fecha límite para la entrega de esta semana es el <strong>{% include fecha-formato-humano.md fecha=fecha %}</strong>.

**Mumuki**
{% assign guias = semana.entrega.mumuki %}
{% include ejercicios-mumuki.md guias=guias %}

{% endif %}

{% if semana.ejercicios %}

### Ejercicios para trabajar en clase
{% assign ejercicios = semana.ejercicios %}
{% include ejercicios-github.html ejercicios=ejercicios %}

{% endif %}

{% if semana.mumuki %}

### Mumuki

Te recomendamos resolver las guías:
{% assign guias = semana.mumuki %}
{% include ejercicios-mumuki.md guias=guias %}

{% endif %}

{% if forloop.last == false %}
<hr class="titulo-semana">
{% endif %}

{% endfor %}
