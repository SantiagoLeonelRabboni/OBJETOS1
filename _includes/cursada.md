{% assign semanas = cursada | sort %}
{% for semana_hash in semanas reversed %}
{% assign numero_semana = semana_hash[0] | plus:0 %}
{% assign semana = semana_hash[1] %}

## [Semana {{numero_semana}}](#semana-{{numero_semana}}){: .titulo-semana}
{{semana.descripcion}}

{% if semana.videos %}
### Videos

{% for video in semana.videos %}
* [{{video.nombre}}]({{video.url}}). 
{% endfor %}
{% endif %}

{% if semana.conferencia %}
### Conferencia

**Link**: [entrar acá]({{semana.conferencia.url}})

{% if semana.conferencia.horarios %}
**Horarios**: {{semana.conferencia.horarios}}
{% endif %}

{% if semana.conferencia.horario0 %}
**Horarios**: {{semana.conferencia.horario0}}

{% if semana.conferencia.horario1 %}
{{semana.conferencia.horario1}}
{% endif %}

{% if semana.conferencia.horario2 %}
{{semana.conferencia.horario2}}
{% endif %}

{% if semana.conferencia.horario3 %}
{{semana.conferencia.horario3}}
{% endif %}

{% endif %}

{% endif %}

{% if semana.entrega %}

### Para entregar
{% assign fecha = semana.entrega.fecha %}
La fecha límite para la entrega de esta semana es el <strong>{% include fecha-formato-humano.md fecha=fecha %}</strong>.

{% assign guias = semana.entrega.mumuki %}
{% if guias %}
**Mumuki**
{% include ejercicios-mumuki.md guias=guias %}
{% endif %}

{% assign ejercicios = semana.entrega.ejercicios %}
{% if ejercicios %}
{% include ejercicios-github.html ejercicios=ejercicios %}
{% endif %}



{{semana.entrega.descripcion}}

{% endif %}

{% if semana.ejercicios %}

### Ejercicios para trabajar en clase
{% assign ejercicios = semana.ejercicios %}
{% include ejercicios-github.html ejercicios=ejercicios %}

{% if semana.textoEjercicios %}
{{semana.textoEjercicios}}
{% endif %}

{% endif %}

{% if semana.mumuki %}

### Ejercicios de Mumuki

Te recomendamos resolver las guías:
{% assign guias = semana.mumuki %}
{% include ejercicios-mumuki.md guias=guias %}

{% endif %}

{% if forloop.last == false %}
<hr class="titulo-semana">
{% endif %}

{% endfor %}
