---
title: "tinlab - Fun"
layout: textlay
excerpt: "Fun"
sitemap: false
permalink: /fun
---

<h3>Photos</h3>

<style>
.gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 15px;
    margin-bottom: 30px;
}
.gallery-item {
    position: relative;
    width: 100%;
    aspect-ratio: 1 / 1;
    overflow: hidden;
    border-radius: 8px;
    cursor: pointer;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.gallery-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 15px rgba(0,0,0,0.2);
}
.gallery-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
}
.gallery-item:hover img {
    transform: scale(1.05);
}
.gallery-caption {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    background: linear-gradient(to top, rgba(0,0,0,0.8), transparent);
    color: white;
    padding: 20px 10px 10px;
    font-size: 14px;
    text-align: center;
    opacity: 0;
    transition: opacity 0.3s ease;
}
.gallery-item:hover .gallery-caption {
    opacity: 1;
}

/* Modal styling */
.gallery-modal {
    display: none;
    position: fixed;
    z-index: 1050;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.9);
    align-items: center;
    justify-content: center;
    flex-direction: column;
    opacity: 0;
    transition: opacity 0.3s ease;
}
.gallery-modal.show {
    display: flex;
    opacity: 1;
}
.gallery-modal-content {
    margin: 0 auto;
    display: block;
    max-width: 90%;
    max-height: 80vh;
    border-radius: 4px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.3);
    object-fit: contain;
}
.gallery-modal-close {
    position: absolute;
    top: 20px;
    right: 30px;
    color: white;
    font-size: 40px;
    font-weight: bold;
    cursor: pointer;
    transition: color 0.3s;
}
.gallery-modal-close:hover {
    color: #ccc;
}
.gallery-modal-caption {
    margin-top: 15px;
    text-align: center;
    color: white;
    font-size: 18px;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.8);
}
</style>

<div class="gallery-grid" markdown="0">
    {% for photo in site.data.photos %}
    <div class="gallery-item" onclick="openModal('{{ site.url }}{{ site.baseurl }}/{{ photo.image }}', '{{ photo.caption }}')">
        <img src="{{ site.url }}{{ site.baseurl }}/{{ photo.image }}" alt="{{ photo.caption }}" />
        <div class="gallery-caption">{{ photo.caption }}</div>
    </div>
    {% endfor %}
</div>

<div id="galleryModal" class="gallery-modal" onclick="closeModal(event)" markdown="0">
    <span class="gallery-modal-close" onclick="closeModal(event)">&times;</span>
    <img class="gallery-modal-content" id="modalImg">
    <div id="modalCaption" class="gallery-modal-caption"></div>
</div>

<script>
function openModal(src, caption) {
    const modal = document.getElementById('galleryModal');
    const modalImg = document.getElementById('modalImg');
    const modalCaption = document.getElementById('modalCaption');
    
    modalImg.src = src;
    modalCaption.innerHTML = caption;
    
    modal.style.display = 'flex';
    // Small delay to allow display to apply before opacity transition
    setTimeout(() => {
        modal.classList.add('show');
    }, 10);
    
    // Prevent scrolling on body
    document.body.style.overflow = 'hidden';
}

function closeModal(event) {
    // Only close if clicking the background or close button, not the image
    if (event && event.target.id === 'modalImg') return;
    
    const modal = document.getElementById('galleryModal');
    modal.classList.remove('show');
    
    setTimeout(() => {
        modal.style.display = 'none';
        document.body.style.overflow = 'auto';
    }, 300); // Wait for transition
}

// Add escape key listener
document.addEventListener('keydown', function(event) {
    if (event.key === "Escape") {
        closeModal();
    }
});
</script>


<h3>Non-human members and friends of tinlab</h3>

{% assign number_printed = 0 %}
{% for member in site.data.nonhumans %}

{% assign even_odd = number_printed | modulo: 3 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-4 clearfix" style="text-align: center; margin-bottom: 30px;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" style="display: block; width: 150px; height: 150px; object-fit: cover; margin: 0 auto 15px auto !important;" />
  <h4>{% if member.website %}<a href="{{ member.website }}">{{ member.name }}</a>{% else %}{{ member.name }}{% endif %}</h4>
  <b>{{ member.info }}</b>
  {% if member.interests %}<br><i>{{ member.interests }}</i>{% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 2 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 3 %}
{% if even_odd != 0 %}
</div>
{% endif %}