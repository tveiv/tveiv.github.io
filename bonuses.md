---
layout: default
title: "Бонусы и Проклятия"
permalink: /bonuses/
---

<style>
/* CSS для интерактивной энциклопедии бонусов VoidGame */
.wiki-container {
    max-width: 1200px;
    margin: 0 auto;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    color: #e4e8f1;
}

.search-filter-section {
    background: rgba(10, 12, 20, 0.6);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 30px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
}

.search-wrapper {
    position: relative;
    margin-bottom: 20px;
}

.search-input {
    width: 100%;
    padding: 14px 18px;
    background: rgba(5, 7, 18, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #fff;
    font-size: 16px;
    outline: none;
    transition: all 0.3s ease;
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.3);
}

.search-input:focus {
    border-color: #9db4ff;
    box-shadow: 0 0 12px rgba(157, 180, 255, 0.3), inset 0 2px 4px rgba(0, 0, 0, 0.3);
}

.filter-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
}

.filter-btn {
    padding: 10px 18px;
    background: rgba(18, 20, 30, 0.8);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    color: #aeb8d8;
    font-size: 14px;
    cursor: pointer;
    font-weight: 500;
    transition: all 0.25s ease;
}

.filter-btn:hover {
    color: #fff;
    border-color: rgba(255, 255, 255, 0.3);
    background: rgba(255, 255, 255, 0.05);
}

.filter-btn.active {
    background: rgba(157, 180, 255, 0.15);
    color: #ffffff;
    border-color: #9db4ff;
    box-shadow: 0 0 15px rgba(157, 180, 255, 0.25);
    text-shadow: 0 0 8px rgba(157, 180, 255, 0.5);
}

/* Сетка карточек */
.bonuses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(290px, 1fr));
    gap: 24px;
    margin-top: 20px;
}

.bonus-card {
    background: rgba(10, 12, 20, 0.85);
    border-radius: 12px;
    padding: 24px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    position: relative;
    overflow: hidden;
    height: 100%;
    box-sizing: border-box;
}

/* Верхняя полоска-индикатор редкости */
.bonus-card::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 4px;
    transition: all 0.3s ease;
}

/* Зелёные (Обычные) */
.bonus-card.rarity-green {
    border: 1px solid rgba(46, 125, 50, 0.2);
}
.bonus-card.rarity-green::after {
    background: #2e7d32;
}
.bonus-card.rarity-green:hover {
    box-shadow: 0 10px 28px rgba(46, 125, 50, 0.15);
    border-color: rgba(46, 125, 50, 0.6);
}

/* Синие (Редкие) */
.bonus-card.rarity-blue {
    border: 1px solid rgba(33, 150, 243, 0.2);
}
.bonus-card.rarity-blue::after {
    background: #2196f3;
}
.bonus-card.rarity-blue:hover {
    box-shadow: 0 10px 28px rgba(33, 150, 243, 0.15);
    border-color: rgba(33, 150, 243, 0.6);
}

/* Легендарные */
.bonus-card.rarity-legendary {
    border: 1px solid rgba(255, 152, 0, 0.2);
}
.bonus-card.rarity-legendary::after {
    background: #ff9800;
}
.bonus-card.rarity-legendary:hover {
    box-shadow: 0 10px 28px rgba(255, 152, 0, 0.2);
    border-color: rgba(255, 152, 0, 0.6);
}

/* Проклятия */
.bonus-card.rarity-curse {
    border: 1px solid rgba(244, 67, 54, 0.2);
}
.bonus-card.rarity-curse::after {
    background: #f44336;
}
.bonus-card.rarity-curse:hover {
    box-shadow: 0 10px 28px rgba(244, 67, 54, 0.2);
    border-color: rgba(244, 67, 54, 0.6);
}

/* Метки / Сеты */
.bonus-card.rarity-set {
    border: 1px solid rgba(156, 39, 176, 0.2);
}
.bonus-card.rarity-set::after {
    background: #9c27b0;
}
.bonus-card.rarity-set:hover {
    box-shadow: 0 10px 28px rgba(156, 39, 176, 0.2);
    border-color: rgba(156, 39, 176, 0.6);
}

/* Контент карточки */
.card-content {
    flex-grow: 1;
}

.card-header {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 14px;
}

.card-icon-wrapper {
    background: rgba(255, 255, 255, 0.04);
    border: 1px solid rgba(255, 255, 255, 0.08);
    padding: 8px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 42px;
    height: 42px;
    box-sizing: border-box;
}

.card-icon {
    width: 26px;
    height: 26px;
    object-fit: contain;
    image-rendering: pixelated;
    image-rendering: crisp-edges;
}

.card-title {
    font-size: 17px;
    font-weight: 700;
    color: #ffffff;
    margin: 0;
    line-height: 1.3;
}

.card-desc {
    font-size: 13.5px;
    color: #b9bfd0;
    line-height: 1.5;
    margin: 0 0 18px 0;
}

/* Футер карточки */
.card-footer {
    border-top: 1px solid rgba(255, 255, 255, 0.06);
    padding-top: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 12px;
}

.card-badge {
    font-size: 11px;
    text-transform: uppercase;
    font-weight: 700;
    letter-spacing: 0.5px;
    padding: 3px 8px;
    border-radius: 4px;
}

.badge-green { background: rgba(46, 125, 50, 0.12); color: #a5d6a7; }
.badge-blue { background: rgba(33, 150, 243, 0.12); color: #90caf9; }
.badge-legendary { background: rgba(255, 152, 0, 0.12); color: #ffe082; }
.badge-curse { background: rgba(244, 67, 54, 0.12); color: #ef9a9a; }
.badge-set { background: rgba(156, 39, 176, 0.12); color: #e1bee7; }

.card-type {
    color: #8fa0c0;
    font-weight: 500;
}

.no-results {
    text-align: center;
    padding: 40px;
    font-size: 16px;
    color: #8fa0c0;
    grid-column: 1 / -1;
    display: none;
}
</style>

# Энциклопедия Бонусов и Эффектов VoidGame

Добро пожаловать в наиболее полную интерактивную энциклопедию всех бонусов, меток сущностей (комплектов) и проклятий в режиме **VoidGame на Cristalix**. 

Воспользуйтесь поиском или удобной панелью фильтрации по редкости, чтобы быстро найти точное описание и иконку любого игрового эффекта!

<div class="wiki-container">
    <!-- Поиск и Фильтрация -->
    <div class="search-filter-section">
        <div class="search-wrapper">
            <input type="text" id="wiki-search" class="search-input" placeholder="Введите название бонуса или ключевые слова из описания...">
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

    <!-- Сетка бонусов -->
    <div class="bonuses-grid" id="bonuses-grid">
        {% for bonus in site.data.voidgame_bonuses %}
        <div class="bonus-card rarity-{{ bonus.rarity }}" data-category="{{ bonus.rarity }}" data-name="{{ bonus.name | downcase }}" data-desc="{{ bonus.description | downcase }}">
            <div class="card-content">
                <div class="card-header">
                    <div class="card-icon-wrapper">
                        <img src="/assets/img/bonuses/{{ bonus.icon }}" class="card-icon" onerror="this.src='/assets/img/unknown.jpg'">
                    </div>
                    <h3 class="card-title">{{ bonus.name }}</h3>
                </div>
                <p class="card-desc">{{ bonus.description }}</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-{{ bonus.rarity }}">
                    {% if bonus.rarity == 'green' %}🟢 Зелёный
                    {% elif bonus.rarity == 'blue' %}🔵 Синий
                    {% elif bonus.rarity == 'legendary' %}🟡 Легендарный
                    {% elif bonus.rarity == 'curse' %}🔴 Проклятие
                    {% elif bonus.rarity == 'set' %}🟣 Сет
                    {% else %}{{ bonus.rarity_ru }}{% endif %}
                </span>
                <span class="card-type">{{ bonus.type }}</span>
            </div>
        </div>
        {% endfor %}
        <div class="no-results" id="no-results-msg">Ничего не найдено. Попробуйте изменить поисковый запрос или фильтр.</div>
    </div>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const searchInput = document.getElementById("wiki-search");
    const filterBtns = document.querySelectorAll(".filter-btn");
    const cards = document.querySelectorAll(".bonus-card");
    const noResults = document.getElementById("no-results-msg");

    let currentFilter = "all";
    let searchQuery = "";

    function filterWiki() {
        let visibleCount = 0;
        cards.forEach(card => {
            const category = card.getAttribute("data-category");
            const name = card.getAttribute("data-name");
            const desc = card.getAttribute("data-desc");

            const matchesFilter = (currentFilter === "all" || category === currentFilter);
            const matchesSearch = (name.includes(searchQuery) || desc.includes(searchQuery));

            if (matchesFilter && matchesSearch) {
                card.style.display = "flex";
                visibleCount++;
            } else {
                card.style.display = "none";
            }
        });

        if (visibleCount === 0) {
            noResults.style.display = "block";
        } else {
            noResults.style.display = "none";
        }
    }

    searchInput.addEventListener("input", function(e) {
        searchQuery = e.target.value.toLowerCase().trim();
        filterWiki();
    });

    filterBtns.forEach(btn => {
        btn.addEventListener("click", function() {
            filterBtns.forEach(b => b.classList.remove("active"));
            btn.classList.add("active");
            currentFilter = btn.getAttribute("data-filter");
            filterWiki();
        });
    });
});
</script>
