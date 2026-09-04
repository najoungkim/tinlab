---
title: "tinlab - Research"
layout: gridlay
excerpt: "tinlab -- Research"
sitemap: false
permalink: /research/
---

# Research

Publications and presentations from tinlab are listed below. Lab members are highlighted.

<div class="pub-container" markdown="0">
{% assign pub_groups = site.data.publist | group_by: "year" %}
{% for group in pub_groups %}
<div class="pub-year-group" data-year="{{ group.name }}">
<h2 class="pub-year-heading">{{ group.name }}</h2>
{% for publi in group.items %}
  {% if publi.url and publi.url != "" %}<a href="{{ publi.url }}">{{ publi.title }}</a>{% else %}{{ publi.title }}{% endif %} <br />
  <span class="author-list">{{ publi.authors | markdownify | remove: '<p>' | remove: '</p>' | strip_newlines }}</span> <br />
  <span class="pub-venue">{{ publi.venue }}</span>{% if publi.award %} <span class="pub-award">👑 {{ publi.award }}</span>{% endif %} <br />
  <hr style="margin-top: 10px; margin-bottom: 20px; border-top: 1px solid #ccc;"/>
{% endfor %}
</div>
{% endfor %}
</div>

<div id="pagination-controls" class="pagination" markdown="0"></div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const yearsPerPage = 5;
    const allGroups = Array.from(document.querySelectorAll('.pub-year-group'));
    // "Work in Progress" is pinned to the top of page 1 and doesn't count toward the 5 years
    const pinnedGroups = allGroups.filter(g => g.dataset.year === 'Work in Progress');
    const yearGroups = allGroups.filter(g => g.dataset.year !== 'Work in Progress');
    const totalPages = Math.ceil(yearGroups.length / yearsPerPage);
    let currentPage = 1;

    function showPage(page) {
        currentPage = page;
        pinnedGroups.forEach(g => { g.style.display = page === 1 ? 'block' : 'none'; });
        yearGroups.forEach((group, index) => {
            if (index >= (page - 1) * yearsPerPage && index < page * yearsPerPage) {
                group.style.display = 'block';
            } else {
                group.style.display = 'none';
            }
        });
        renderControls();
    }

    function renderControls() {
        const controls = document.getElementById('pagination-controls');
        controls.innerHTML = '';

        if (totalPages <= 1) return;

        for (let i = 1; i <= totalPages; i++) {
            const first = yearGroups[(i - 1) * yearsPerPage].dataset.year;
            const last = yearGroups[Math.min(i * yearsPerPage, yearGroups.length) - 1].dataset.year;
            const btn = document.createElement('button');
            btn.innerText = first === last ? first : first + '–' + last;
            btn.className = i === currentPage ? 'active' : '';
            btn.onclick = () => {
                showPage(i);
                window.scrollTo({ top: 0, behavior: 'smooth' });
            };
            controls.appendChild(btn);
        }
    }

    if (yearGroups.length > 0) {
        showPage(1);
    }
});
</script>

<style>
.pub-year-heading {
    font-size: 1.1em;
    font-weight: 600;
    color: #666;
    margin-top: 28px;
    margin-bottom: 16px;
    padding-bottom: 5px;
    border-bottom: 1px solid #e0e0e0;
}
.pagination {
    display: flex;
    justify-content: center;
    gap: 8px;
    margin-top: 40px;
    margin-bottom: 20px;
}
.pagination button {
    padding: 8px 14px;
    border: 1px solid #ccc;
    background: #fff;
    cursor: pointer;
    border-radius: 4px;
    font-size: 16px;
    font-weight: 500;
    transition: all 0.2s;
    color: #333;
}
.pagination button:hover {
    background: #f4f4f4;
    border-color: #aaa;
}
.pagination button.active {
    background: #007bff;
    color: white;
    border-color: #007bff;
}
</style>
