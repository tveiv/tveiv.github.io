---
layout: default
title: "Бонусы и Проклятия"
permalink: /bonuses/
---

<style>
/* Стили для интеграции со звёздной темой сайта */
.wiki-bonuses-container {
    max-width: 1000px;
    margin: 0 auto;
}

.search-filter-section {
    background: rgba(20, 22, 30, 0.6);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 30px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
    backdrop-filter: blur(8px);
}

.search-input-wrapper {
    position: relative;
    margin-bottom: 20px;
}

.search-input {
    width: 100%;
    padding: 12px 20px;
    background: rgba(10, 12, 20, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #ffffff;
    font-size: 16px;
    outline: none;
    transition: all 0.3s ease;
}

.search-input:focus {
    border-color: #9db4ff;
    box-shadow: 0 0 12px rgba(157, 180, 255, 0.4);
}

.filter-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
}

.filter-btn {
    padding: 8px 16px;
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    color: #aeb8d8;
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s ease;
}

.filter-btn:hover {
    color: #ffffff;
    background: rgba(255, 255, 255, 0.08);
    border-color: rgba(255, 255, 255, 0.2);
}

.filter-btn.active {
    background: rgba(157, 180, 255, 0.15);
    color: #ffffff;
    border-color: #9db4ff;
    box-shadow: 0 0 10px rgba(157, 180, 255, 0.3);
}

/* Сетка бонусов */
.bonuses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
    margin-top: 20px;
}

.bonus-card {
    background: rgba(15, 17, 26, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.06);
    border-radius: 12px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    position: relative;
    overflow: hidden;
    height: 100%;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

/* Цветная полоса редкости сверху */
.bonus-card::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 4px;
    transition: all 0.3s ease;
}

/* Стилизация в зависимости от редкости */
.bonus-card.rarity-green { border-color: rgba(46, 125, 50, 0.25); }
.bonus-card.rarity-green::after { background: #2e7d32; }
.bonus-card.rarity-green:hover {
    box-shadow: 0 8px 24px rgba(46, 125, 50, 0.25);
    border-color: rgba(46, 125, 50, 0.6);
}

.bonus-card.rarity-blue { border-color: rgba(21, 101, 192, 0.25); }
.bonus-card.rarity-blue::after { background: #1565c0; }
.bonus-card.rarity-blue:hover {
    box-shadow: 0 8px 24px rgba(21, 101, 192, 0.3);
    border-color: rgba(21, 101, 192, 0.6);
}

.bonus-card.rarity-legendary { border-color: rgba(230, 81, 0, 0.25); }
.bonus-card.rarity-legendary::after { background: #ff9800; }
.bonus-card.rarity-legendary:hover {
    box-shadow: 0 8px 24px rgba(230, 81, 0, 0.35);
    border-color: rgba(230, 81, 0, 0.7);
}

.bonus-card.rarity-curse { border-color: rgba(198, 40, 40, 0.25); }
.bonus-card.rarity-curse::after { background: #c62828; }
.bonus-card.rarity-curse:hover {
    box-shadow: 0 8px 24px rgba(198, 40, 40, 0.35);
    border-color: rgba(198, 40, 40, 0.7);
}

.bonus-card.rarity-set { border-color: rgba(106, 27, 154, 0.25); }
.bonus-card.rarity-set::after { background: #9c27b0; }
.bonus-card.rarity-set:hover {
    box-shadow: 0 8px 24px rgba(106, 27, 154, 0.3);
    border-color: rgba(106, 27, 154, 0.7);
}

.card-header-block {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 12px;
}

.card-icon-container {
    width: 44px;
    height: 44px;
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
}

.card-icon-img {
    width: 32px;
    height: 32px;
    object-fit: contain;
    image-rendering: pixelated;
    image-rendering: crisp-edges;
}

.card-title-text {
    font-size: 18px;
    font-weight: 700;
    color: #ffffff;
    margin: 0;
}

.card-description-text {
    font-size: 14px;
    color: #c2c7d8;
    line-height: 1.5;
    margin-bottom: 15px;
    flex-grow: 1;
}

.card-footer-block {
    border-top: 1px solid rgba(255, 255, 255, 0.05);
    padding-top: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.card-badge {
    font-size: 11px;
    text-transform: uppercase;
    font-weight: 700;
    letter-spacing: 0.5px;
    padding: 3px 8px;
    border-radius: 4px;
}

.badge-green { background: rgba(46, 125, 50, 0.15); color: #81c784; }
.badge-blue { background: rgba(21, 101, 192, 0.15); color: #64b5f6; }
.badge-legendary { background: rgba(230, 81, 0, 0.15); color: #ffb74d; }
.badge-curse { background: rgba(198, 40, 40, 0.15); color: #e57373; }
.badge-set { background: rgba(106, 27, 154, 0.15); color: #ba68c8; }

.card-type-text {
    font-size: 12px;
    color: #9aa3b2;
    font-weight: 500;
}

.no-results-block {
    text-align: center;
    padding: 40px;
    color: #9aa3b2;
    font-size: 16px;
    display: none;
}
</style>

<div class="wiki-bonuses-container">
    <div class="search-filter-section">
        <div class="search-input-wrapper">
            <input type="text" id="wiki-search" class="search-input" placeholder="Поиск по названию или описанию...">
        </div>
        <div class="filter-pills">
            <button class="filter-btn active" data-filter="all">Все эффекты</button>
            <button class="filter-btn" data-filter="green">🟢 Обычные (Зелёные)</button>
            <button class="filter-btn" data-filter="blue">🔵 Редкие (Синие)</button>
            <button class="filter-btn" data-filter="legendary">🟡 Легендарные</button>
            <button class="filter-btn" data-filter="curse">🔴 Проклятия</button>
            <button class="filter-btn" data-filter="set">🟣 Метки (Сеты)</button>
        </div>
    </div>

    <!-- Сетка бонусов из базы данных -->
    <div class="bonuses-grid" id="bonuses-grid">
        {% for bonus in site.data.voidgame_bonuses %}
        <div class="bonus-card rarity-{{ bonus.rarity }}" data-category="{{ bonus.rarity }}" data-name="{{ bonus.name | downcase }}" data-desc="{{ bonus.description | downcase }}">
            <div>
                <div class="card-header-block">
                    <div class="card-icon-container">
                        <img class="card-icon-img" src="/assets/img/bonuses/{{ bonus.icon }}" onerror="this.onerror=null; this.src='/assets/img/unknown.jpg';" alt="{{ bonus.name }}">
                    </div>
                    <h3 class="card-title-text">{{ bonus.name }}</h3>
                </div>
                <p class="card-description-text">{{ bonus.description }}</p>
            </div>
            <div class="card-footer-block">
                {% if bonus.rarity == 'green' %}
                <span class="card-badge badge-green">Зелёный</span>
                {% elsif bonus.rarity == 'blue' %}
                <span class="card-badge badge-blue">Синий</span>
                {% elsif bonus.rarity == 'legendary' %}
                <span class="card-badge badge-legendary">Легендарный</span>
                {% elsif bonus.rarity == 'curse' %}
                <span class="card-badge badge-curse">Проклятие</span>
                {% elsif bonus.rarity == 'set' %}
                <span class="card-badge badge-set">Метка</span>
                {% else %}
                <span class="card-badge">{{ bonus.rarity_ru }}</span>
                {% endif %}
                <span class="card-type-text">{{ bonus.type }}</span>
            </div>
        </div>
        {% endfor %}
    </div>

    <div class="no-results-block" id="no-results">
        Ничего не найдено. Попробуйте изменить поисковый запрос или фильтр.
    </div>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const searchInput = document.getElementById("wiki-search");
    const filterButtons = document.querySelectorAll(".filter-btn");
    const cards = document.querySelectorAll(".bonus-card");
    const noResults = document.getElementById("no-results");

    function filterCards() {
        const query = searchInput.value.toLowerCase().trim();
        const activeFilter = document.querySelector(".filter-btn.active").getAttribute("data-filter");
        let visibleCount = 0;

        cards.forEach(card => {
            const name = card.getAttribute("data-name");
            const desc = card.getAttribute("data-desc");
            const category = card.getAttribute("data-category");

            const matchesSearch = name.includes(query) || desc.includes(query);
            const matchesFilter = activeFilter === 'all' || category === activeFilter;

            if (matchesSearch && matchesFilter) {
                card.style.display = 'flex';
                visibleCount++;
            } else {
                card.style.display = 'none';
            }
        });

        if (visibleCount === 0) {
            noResults.style.display = 'block';
        } else {
            noResults.style.display = 'none';
        }
    }

    searchInput.addEventListener("input", filterCards);

    filterButtons.forEach(btn => {
        btn.addEventListener("click", function() {
            filterButtons.forEach(b => b.classList.remove("active"));
            this.classList.add("active");
            filterCards();
        });
    });
});
</script>
