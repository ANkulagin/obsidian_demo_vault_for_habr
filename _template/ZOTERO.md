---
date: {{date}}
tags: 
authors: {{authors}}

Abstract:  {{abstractNote}}
---

### {{title}}
{{pdfZoteroLink}}

### Notes
{% for annotation in annotations -%}
  {%- if annotation.annotatedText -%}
    {%- if "Gray" in annotation.colorCategory %}
```
{{annotation.annotatedText | escape}}
```


    {%- elif "Magenta" in annotation.colorCategory %}
# {{ annotation.annotatedText | escape }}
([{{ annotation.page }}](zotero://open-pdf/library/items/{{ annotation.attachment.itemKey }}?page={{ annotation.page }}&annotation={{ annotation.id }}))

    {%- elif "Yellow" in annotation.colorCategory %}
## {{ annotation.annotatedText | escape }}
([{{ annotation.page }}](zotero://open-pdf/library/items/{{ annotation.attachment.itemKey }}?page={{ annotation.page }}&annotation={{ annotation.id }}))

    {%- elif "Red" in annotation.colorCategory %}
### {{ annotation.annotatedText | escape }}
([{{ annotation.page }}](zotero://open-pdf/library/items/{{ annotation.attachment.itemKey }}?page={{ annotation.page }}&annotation={{ annotation.id }}))

    {%- elif "Orange" in annotation.colorCategory %}
`{{ annotation.annotatedText | escape }}`


    {%- elif "Purple" in annotation.colorCategory %}
**{{ annotation.annotatedText | escape }}**

    {%- elif "Blue" in annotation.colorCategory %}
> {{ annotation.annotatedText | escape }}


    {%- elif "Green" in annotation.colorCategory %}
{{ annotation.annotatedText | escape }}


    {%- else %}
{{ annotation.annotatedText | escape }}

    {%- endif %}
  {%- endif %}

  {%- if annotation.imageRelativePath %}
![[{{ annotation.imageRelativePath }}]]
  {%- endif %}

{%- if annotation.comment %}
<div class="custom-comment">
  <p class="comment-label">Мой комментарий:</p>
  <p class="comment-text">{{ annotation.comment }}</p>
</div>
{%- endif %}
{% endfor -%}