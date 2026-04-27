---
title: "News"
layout: textlay
excerpt: "Allan Lab at Leiden University."
sitemap: false
permalink: /allnews.html
---

<style>
.allnews-item {
  border-bottom: 1px solid #e0e0e0;
  padding-bottom: 20px;
  margin-bottom: 20px;
}
.allnews-item-date {
  font-weight: bold;
  font-size: 1.1em;
  margin-bottom: 5px;
}
.allnews-item-content {
  font-size: 1.1em;
}
.allnews-item-content p {
  margin: 0;
}
.allnews-item:last-of-type {
  border-bottom: none;
}
</style>

# News

<div class="allnews-container" markdown="0">
{% for article in site.data.news %}
{% include news_item.html article=article css_prefix="allnews" %}
{% endfor %}
</div>

<div id="pagination-controls" class="pagination" markdown="0"></div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const itemsPerPage = 20;
    const items = document.querySelectorAll('.allnews-item');
    const totalPages = Math.ceil(items.length / itemsPerPage);
    let currentPage = 1;

    function showPage(page) {
        currentPage = page;
        items.forEach((item, index) => {
            if (index >= (page - 1) * itemsPerPage && index < page * itemsPerPage) {
                item.style.display = 'block';
                // Clean up any dynamically removed borders from previous pages
                item.style.borderBottom = '';
                item.style.marginBottom = '';
            } else {
                item.style.display = 'none';
            }
        });
        
        // Remove border from the last visible item
        const visibleItems = Array.from(items).filter(item => item.style.display === 'block');
        if (visibleItems.length > 0) {
            visibleItems[visibleItems.length - 1].style.borderBottom = 'none';
            visibleItems[visibleItems.length - 1].style.marginBottom = '0';
        }

        renderControls();
        
        // Only scroll if we aren't loading the first page initially
        if (page > 1 || (performance && performance.navigation.type !== 1)) {
           window.scrollTo({ top: 0, behavior: 'smooth' });
        }
    }

    function renderControls() {
        const controls = document.getElementById('pagination-controls');
        controls.innerHTML = '';
        
        if (totalPages <= 1) return;

        for (let i = 1; i <= totalPages; i++) {
            const btn = document.createElement('button');
            btn.innerText = i;
            btn.className = i === currentPage ? 'active' : '';
            btn.onclick = () => {
                showPage(i);
                window.scrollTo({ top: 0, behavior: 'smooth' });
            };
            controls.appendChild(btn);
        }
    }

    if (items.length > 0) {
        showPage(1);
    }
});
</script>

<style>
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
