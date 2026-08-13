---
layout: default
title: "Бонусы и Проклятия"
permalink: /bonuses/
---

<style>
/* Стили для страницы бонусов и проклятий VoidGame */
.wiki-header {
    text-align: center;
    margin-bottom: 40px;
}

.wiki-header h1 {
    font-size: 36px;
    font-weight: 800;
    letter-spacing: 2px;
    text-transform: uppercase;
    background: linear-gradient(90deg, #f5d78a, #ffffff, #f5d78a);
    -webkit-background-clip: text;
    color: transparent;
    -webkit-text-fill-color: transparent;
    margin-bottom: 10px;
}

.wiki-header p {
    color: #aeb8d8;
    font-size: 16px;
    letter-spacing: 0.5px;
}

/* Секция поиска и фильтров */
.search-filter-section {
    background: rgba(15, 17, 28, 0.7);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 30px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
    backdrop-filter: blur(8px);
    -webkit-backdrop-filter: blur(8px);
}

.search-wrapper {
    position: relative;
    margin-bottom: 20px;
}

.search-input {
    width: 100%;
    padding: 14px 20px;
    background: rgba(5, 7, 18, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #fff;
    font-size: 16px;
    outline: none;
    transition: all 0.3s ease;
    box-sizing: border-box;
}

.search-input:focus {
    border-color: #f5d78a;
    box-shadow: 0 0 12px rgba(245, 215, 138, 0.25);
}

.filter-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
}

.filter-btn {
    padding: 10px 20px;
    background: rgba(255, 255, 255, 0.04);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    color: #cbd3ef;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.25s ease;
    display: flex;
    align-items: center;
    gap: 6px;
}

.filter-btn:hover {
    color: #ffffff;
    border-color: rgba(255, 255, 255, 0.25);
    background: rgba(255, 255, 255, 0.08);
}

.filter-btn.active {
    background: rgba(245, 215, 138, 0.15);
    color: #f5d78a;
    border-color: #f5d78a;
    text-shadow: 0 0 8px rgba(245, 215, 138, 0.4);
    box-shadow: 0 0 12px rgba(245, 215, 138, 0.15);
}

/* Сетка карточек */
.bonuses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(290px, 1fr));
    gap: 24px;
}

.bonus-card {
    background: rgba(15, 17, 28, 0.65);
    border: 1px solid rgba(255, 255, 255, 0.05);
    border-radius: 12px;
    padding: 24px;
    display: flex;
    flex-direction: column;
    position: relative;
    overflow: hidden;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    backdrop-filter: blur(5px);
    -webkit-backdrop-filter: blur(5px);
    height: 100%;
    box-sizing: border-box;
}

/* Цветная плашка редкости сверху */
.bonus-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 4px;
    opacity: 0.8;
}

/* Стили для разных редкостей */
.bonus-card[data-category="green"]::before { background: #4caf50; }
.bonus-card[data-category="green"] { border-color: rgba(76, 175, 80, 0.15); }
.bonus-card[data-category="green"]:hover { 
    border-color: rgba(76, 175, 80, 0.4); 
    box-shadow: 0 8px 25px rgba(76, 175, 80, 0.12);
}

.bonus-card[data-category="blue"]::before { background: #2196f3; }
.bonus-card[data-category="blue"] { border-color: rgba(33, 150, 243, 0.15); }
.bonus-card[data-category="blue"]:hover { 
    border-color: rgba(33, 150, 243, 0.4); 
    box-shadow: 0 8px 25px rgba(33, 150, 243, 0.12);
}

.bonus-card[data-category="legendary"]::before { background: #ff9800; }
.bonus-card[data-category="legendary"] { border-color: rgba(255, 152, 0, 0.15); }
.bonus-card[data-category="legendary"]:hover { 
    border-color: rgba(255, 152, 0, 0.4); 
    box-shadow: 0 8px 25px rgba(255, 152, 0, 0.15);
}

.bonus-card[data-category="curse"]::before { background: #f44336; }
.bonus-card[data-category="curse"] { border-color: rgba(244, 67, 54, 0.15); }
.bonus-card[data-category="curse"]:hover { 
    border-color: rgba(244, 67, 54, 0.4); 
    box-shadow: 0 8px 25px rgba(244, 67, 54, 0.15);
}

.bonus-card[data-category="set"]::before { background: #9c27b0; }
.bonus-card[data-category="set"] { border-color: rgba(156, 39, 176, 0.15); }
.bonus-card[data-category="set"]:hover { 
    border-color: rgba(156, 39, 176, 0.4); 
    box-shadow: 0 8px 25px rgba(156, 39, 176, 0.15);
}

.card-top {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 16px;
}

.bonus-icon {
    width: 38px;
    height: 38px;
    object-fit: contain;
    image-rendering: pixelated;
    background: rgba(255, 255, 255, 0.03);
    padding: 6px;
    border-radius: 8px;
    border: 1px solid rgba(255, 255, 255, 0.08);
}

.bonus-card-title {
    font-size: 18px;
    font-weight: 700;
    color: #ffffff;
    margin: 0;
    line-height: 1.3;
}

.bonus-description {
    font-size: 14px;
    color: #c2c7d8;
    line-height: 1.6;
    margin: 0 0 20px 0;
    flex-grow: 1;
}

.bonus-description strong {
    color: #f5d78a;
}

.card-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 14px;
    border-top: 1px solid rgba(255, 255, 255, 0.05);
    margin-top: auto;
}

.rarity-badge {
    font-size: 11px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    padding: 4px 10px;
    border-radius: 4px;
}

.rarity-badge.green { background: rgba(76, 175, 80, 0.12); color: #81c784; }
.rarity-badge.blue { background: rgba(33, 150, 243, 0.12); color: #64b5f6; }
.rarity-badge.legendary { background: rgba(255, 152, 0, 0.12); color: #ffb74d; }
.rarity-badge.curse { background: rgba(244, 67, 54, 0.12); color: #e57373; }
.rarity-badge.set { background: rgba(156, 39, 176, 0.12); color: #ba68c8; }

.bonus-type {
    font-size: 12px;
    color: #8c96a8;
    font-weight: 500;
}
</style>

<div class="wiki-container">
    <div class="wiki-header">
        <h1>Бонусы и Проклятия</h1>
        <p>Полная интерактивная база игровых эффектов VoidGame на Cristalix</p>
    </div>

    <!-- Поиск и Фильтрация -->
    <div class="search-filter-section">
        <div class="search-wrapper">
            <input type="text" id="wiki-search" class="search-input" placeholder="Поиск бонуса по названию или описанию...">
        </div>
        <div class="filter-pills">
            <button class="filter-btn active" data-filter="all">Все</button>
            <button class="filter-btn" data-filter="green">🟢 Зелёные</button>
            <button class="filter-btn" data-filter="blue">🔵 Синие</button>
            <button class="filter-btn" data-filter="legendary">🟡 Легендарные</button>
            <button class="filter-btn" data-filter="curse">🔴 Проклятия</button>
            <button class="filter-btn" data-filter="set">🟣 Метки (Сеты)</button>
        </div>
    </div>

    <!-- Сетка бонусов из Jekyll Data -->
    <div class="bonuses-grid" id="bonuses-grid">
        {% for bonus in site.data.voidgame_bonuses %}
        <div class="bonus-card" data-category="{{ bonus.rarity }}" data-name="{{ bonus.name | downcase }}" data-desc="{{ bonus.description | downcase }}">
            <div>
                <div class="card-top">
                    <img src="/assets/img/bonuses/{{ bonus.icon }}" class="bonus-icon" alt="{{ bonus.name }}" onerror="this.src='/assets/img/bonuses/unknown.png'">
                    <h3 class="bonus-card-title">{{ bonus.name }}</h3>
                </div>
                <p class="bonus-description">{{ bonus.description }}</p>
            </div>
            <div class="card-footer">
                <span class="rarity-badge {{ bonus.rarity }}">{{ bonus.rarity_ru }}</span>
                <span class="bonus-type">{{ bonus.type }}</span>
            </div>
        </div>
        {% endfor %}
    </div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const searchInput = document.getElementById('wiki-search');
    const filterButtons = document.querySelectorAll('.filter-btn');
    const cards = document.querySelectorAll('.bonus-card');

    let currentFilter = 'all';
    let searchQuery = '';

    function filterCards() {
        cards.forEach(card => {
            const cardCategory = card.getAttribute('data-category');
            const cardName = card.getAttribute('data-name') || '';
            const cardDesc = card.getAttribute('data-desc') || '';

            const matchesFilter = (currentFilter === 'all' || cardCategory === currentFilter);
            const matchesSearch = (searchQuery === '' || cardName.includes(searchQuery) || cardDesc.includes(searchQuery));

            if (matchesFilter && matchesSearch) {
                card.style.display = 'flex';
            } else {
                card.style.display = 'none';
            }
        });
    }

    searchInput.addEventListener('input', function(e) {
        searchQuery = e.target.value.toLowerCase().trim();
        filterCards();
    });

    filterButtons.forEach(button => {
        button.addEventListener('click', function() {
            filterButtons.forEach(btn => btn.classList.remove('active'));
            this.classList.add('active');
            currentFilter = this.getAttribute('data-filter');
            filterCards();
        });
    });
});
</script>
