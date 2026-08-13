---
layout: default
title: "Бонусы и Проклятия"
permalink: /bonuses/
---

<style>
/* CSS для интерактивной энциклопедии бонусов VoidGame */
.wiki-container {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    color: #e4e8f1;
    margin: 20px 0;
}

.search-filter-section {
    background: rgba(20, 22, 30, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 25px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.6);
    backdrop-filter: blur(8px);
    -webkit-backdrop-filter: blur(8px);
}

.search-wrapper {
    position: relative;
    margin-bottom: 15px;
}

.search-input {
    width: 100%;
    padding: 12px 15px;
    background: rgba(10, 12, 20, 0.95);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #fff;
    font-size: 16px;
    outline: none;
    transition: all 0.3s ease;
}

.search-input:focus {
    border-color: #9cb4ff;
    box-shadow: 0 0 12px rgba(157, 180, 255, 0.3);
}

.filter-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
}

.filter-btn {
    padding: 8px 16px;
    background: rgba(20, 22, 30, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    color: #aeb8d8;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s ease;
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
    box-shadow: 0 0 10px rgba(157, 180, 255, 0.3);
}

/* Сетка бонусов */
.bonuses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
    margin-top: 15px;
}

.bonus-card {
    background: rgba(10, 12, 20, 0.9);
    border-radius: 12px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    position: relative;
    overflow: hidden;
    height: 100%;
}

.bonus-card::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 3px;
}

/* Подсветка карточек в зависимости от редкости */
.bonus-card.rarity-green {
    border: 1px solid rgba(46, 125, 50, 0.25);
}
.bonus-card.rarity-green::after {
    background: #2e7d32;
}
.bonus-card.rarity-green:hover {
    box-shadow: 0 8px 24px rgba(46, 125, 50, 0.2);
    border-color: rgba(46, 125, 50, 0.6);
}

.bonus-card.rarity-blue {
    border: 1px solid rgba(21, 101, 192, 0.25);
}
.bonus-card.rarity-blue::after {
    background: #1565c0;
}
.bonus-card.rarity-blue:hover {
    box-shadow: 0 8px 24px rgba(21, 101, 192, 0.2);
    border-color: rgba(21, 101, 192, 0.6);
}

.bonus-card.rarity-legendary {
    border: 1px solid rgba(230, 81, 0, 0.25);
}
.bonus-card.rarity-legendary::after {
    background: #ff9800;
}
.bonus-card.rarity-legendary:hover {
    box-shadow: 0 8px 24px rgba(230, 81, 0, 0.25);
    border-color: rgba(230, 81, 0, 0.7);
}

.bonus-card.rarity-curse {
    border: 1px solid rgba(198, 40, 40, 0.25);
}
.bonus-card.rarity-curse::after {
    background: #c62828;
}
.bonus-card.rarity-curse:hover {
    box-shadow: 0 8px 24px rgba(198, 40, 40, 0.25);
    border-color: rgba(198, 40, 40, 0.7);
}

.bonus-card.rarity-set {
    border: 1px solid rgba(106, 27, 154, 0.25);
}
.bonus-card.rarity-set::after {
    background: #9c27b0;
}
.bonus-card.rarity-set:hover {
    box-shadow: 0 8px 24px rgba(106, 27, 154, 0.25);
    border-color: rgba(106, 27, 154, 0.7);
}

.card-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 15px;
}

.card-icon-container {
    background: rgba(255, 255, 255, 0.05);
    padding: 4px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 44px;
    height: 44px;
    border: 1px solid rgba(255, 255, 255, 0.08);
}

.card-icon {
    width: 32px;
    height: 32px;
    object-fit: contain;
    image-rendering: pixelated;
}

.card-title {
    font-size: 18px;
    font-weight: bold;
    color: #ffffff;
    margin: 0;
    line-height: 1.2;
}

.card-desc {
    font-size: 14px;
    color: #b0b8db;
    line-height: 1.6;
    margin-bottom: 15px;
    flex-grow: 1;
}

.card-desc strong {
    color: #ffffff;
}

.card-footer {
    border-top: 1px solid rgba(255, 255, 255, 0.05);
    padding-top: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: auto;
}

.card-badge {
    font-size: 11px;
    text-transform: uppercase;
    font-weight: bold;
    letter-spacing: 0.5px;
    padding: 3px 8px;
    border-radius: 4px;
}

.badge-green { background: rgba(46, 125, 50, 0.15); color: #81c784; }
.badge-blue { background: rgba(21, 101, 192, 0.15); color: #64b5f6; }
.badge-legendary { background: rgba(230, 81, 0, 0.15); color: #ffb74d; }
.badge-curse { background: rgba(198, 40, 40, 0.15); color: #e57373; }
.badge-set { background: rgba(106, 27, 154, 0.15); color: #ba68c8; }

.card-type {
    font-size: 12px;
    font-weight: 500;
    color: #9aa3c2;
}

.no-results {
    text-align: center;
    padding: 40px;
    font-size: 16px;
    color: #9aa3c2;
    background: rgba(20, 22, 30, 0.6);
    border-radius: 8px;
    border: 1px dashed rgba(255, 255, 255, 0.1);
    display: none;
    width: 100%;
}
</style>

# Энциклопедия Бонусов и Эффектов

Добро пожаловать в наиболее полную интерактивную энциклопедию всех бонусов, меток сущностей (комплектов) и проклятий в режиме **VoidGame на Cristalix**. 

Воспользуйтесь поиском или удобной панелью фильтрации по редкости, чтобы быстро найти точное описание и иконку любого игрового эффекта!

<div class="wiki-container">
    <!-- Поиск и Фильтрация -->
    <div class="search-filter-section">
        <div class="search-wrapper">
            <input type="text" id="wiki-search" class="search-input" placeholder="Поиск бонуса по названию или описанию...">
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

    <!-- Сетка бонусов (Динамически генерируется через Jekyll Liquid из _data/voidgame_bonuses.json) -->
    <div class="bonuses-grid" id="bonuses-grid">
        {% for bonus in site.data.voidgame_bonuses %}
        <div class="bonus-card rarity-{{ bonus.rarity }}" data-category="{{ bonus.rarity }}" data-name="{{ bonus.name | downcase }}" data-desc="{{ bonus.description | downcase }}">
            <div>
                <div class="card-header">
                    <div class="card-icon-container">
                        <img src="/assets/img/bonuses/{{ bonus.icon }}" class="card-icon" onerror="this.onerror=null; this.src='/assets/img/bonuses/unknown.jpg';">
                    </div>
                    <h3 class="card-title">{{ bonus.name }}</h3>
                </div>
                <p class="card-desc">{{ bonus.description }}</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-{{ bonus.rarity }}">
                    {% if bonus.rarity == 'green' %}🟢 Зелёный
                    {% elsif bonus.rarity == 'blue' %}🔵 Синий
                    {% elsif bonus.rarity == 'legendary' %}🟡 Легендарный
                    {% elsif bonus.rarity == 'curse' %}🔴 Проклятие
                    {% elsif bonus.rarity == 'set' %}🟣 Сет
                    {% else %}{{ bonus.rarity_ru }}{% endif %}
                </span>
                <span class="card-type">{{ bonus.type }}</span>
            </div>
        </div>
        {% endfor %}
        
        <div class="no-results" id="no-results">
            Ничего не найдено. Попробуйте изменить поисковый запрос или фильтр.
        </div>
    </div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const searchInput = document.getElementById('wiki-search');
    const filterButtons = document.querySelectorAll('.filter-btn');
    const cards = document.querySelectorAll('.bonus-card');
    const noResults = document.getElementById('no-results');

    function filterCards() {
        const query = searchInput.value.toLowerCase().trim();
        const activeFilter = document.querySelector('.filter-btn.active').getAttribute('data-filter');
        let visibleCount = 0;

        cards.forEach(card => {
            const name = card.getAttribute('data-name');
            const desc = card.getAttribute('data-desc');
            const cat = card.getAttribute('data-category');

            const matchesSearch = name.includes(query) || desc.includes(query);
            const matchesFilter = activeFilter === 'all' || cat === activeFilter;

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

    searchInput.addEventListener('input', filterCards);

    filterButtons.forEach(btn => {
        btn.addEventListener('click', function() {
            filterButtons.forEach(b => b.classList.remove('active'));
            this.classList.add('active');
            filterCards();
        });
    });
});
</script>
