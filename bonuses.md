---
layout: default
title: "Бонусы и Проклятия"
permalink: /bonuses/
---

<style>
/* Стильные карточки и фильтрация, идеально подходящие под дизайн Wiki */
.wiki-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

.wiki-header {
    text-align: center;
    margin-bottom: 40px;
}

.wiki-title {
    font-size: 2.5rem;
    font-weight: 800;
    margin-bottom: 10px;
}

.wiki-subtitle {
    color: #666;
    font-size: 1.1rem;
}

/* Панель поиска и фильтрации */
.search-filter-panel {
    display: flex;
    flex-direction: column;
    gap: 15px;
    margin-bottom: 30px;
    background: rgba(0, 0, 0, 0.03);
    padding: 20px;
    border-radius: 12px;
}

@media(min-width: 768px) {
    .search-filter-panel {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
    }
}

.search-input-wrapper {
    flex-grow: 1;
    position: relative;
}

.search-input {
    width: 100%;
    padding: 12px 20px;
    font-size: 1rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    background: #fff;
    color: #333;
    outline: none;
    transition: border-color 0.2s;
}

.search-input:focus {
    border-color: #1565c0;
}

.filter-buttons {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
}

.filter-btn {
    padding: 8px 16px;
    border: 1px solid #ddd;
    background: #fff;
    color: #555;
    border-radius: 20px;
    font-size: 0.9rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
}

.filter-btn:hover {
    background: #f0f0f0;
}

.filter-btn.active {
    background: #1565c0;
    color: #fff;
    border-color: #1565c0;
}

/* Грид карточек */
.bonuses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
}

/* Карточка бонуса */
.bonus-card {
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.06);
    padding: 20px;
    border-top: 5px solid #ddd;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    transition: transform 0.2s, box-shadow 0.2s;
    position: relative;
    overflow: hidden;
}

.bonus-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.12);
}

/* Цвета редкостей */
.bonus-card.rarity-green { border-top-color: #2e7d32; }
.bonus-card.rarity-blue { border-top-color: #1565c0; }
.bonus-card.rarity-legendary { border-top-color: #ff9800; }
.bonus-card.rarity-curse { border-top-color: #c62828; }
.bonus-card.rarity-set { border-top-color: #9c27b0; }

.bonus-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 15px;
}

.bonus-icon-wrapper {
    width: 48px;
    height: 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(0,0,0,0.03);
    border-radius: 8px;
}

.bonus-icon {
    width: 32px;
    height: 32px;
    image-rendering: pixelated;
}

.bonus-meta {
    display: flex;
    flex-direction: column;
}

.bonus-name {
    font-size: 1.15rem;
    font-weight: 700;
    color: #111;
    margin: 0;
}

.bonus-badge {
    display: inline-block;
    padding: 3px 8px;
    border-radius: 12px;
    font-size: 0.75rem;
    font-weight: 700;
    margin-top: 4px;
    text-transform: uppercase;
}

.badge-green { background: #e8f5e9; color: #2e7d32; }
.badge-blue { background: #e3f2fd; color: #1565c0; }
.badge-legendary { background: #fff3e0; color: #e65100; }
.badge-curse { background: #ffebee; color: #c62828; }
.badge-set { background: #f3e5f5; color: #8e24aa; }

.bonus-description {
    color: #444;
    font-size: 0.95rem;
    line-height: 1.45;
    margin-top: 10px;
    flex-grow: 1;
}

.bonus-type {
    font-size: 0.8rem;
    color: #888;
    margin-top: 15px;
    font-weight: 600;
}

/* Ночной режим сайта */
@media (prefers-color-scheme: dark) {
    .wiki-container { color: #f5f5f5; }
    .search-filter-panel { background: rgba(255,255,255,0.05); }
    .search-input { background: #222; border-color: #444; color: #fff; }
    .filter-btn { background: #222; border-color: #444; color: #ccc; }
    .filter-btn:hover { background: #333; }
    .bonus-card { background: #1e1e1e; box-shadow: 0 4px 10px rgba(0,0,0,0.3); }
    .bonus-name { color: #fff; }
    .bonus-description { color: #ccc; }
    .bonus-icon-wrapper { background: rgba(255,255,255,0.05); }
}
</style>

<div class="wiki-container">
    <div class="wiki-header">
        <h1 class="wiki-title">Бонусы и Проклятия</h1>
        <p class="wiki-subtitle">Полная интерактивная база игровых эффектов VoidGame на Cristalix</p>
    </div>

    <!-- Поиск и фильтрация -->
    <div class="search-filter-panel">
        <div class="search-input-wrapper">
            <input type="text" id="wikiSearch" class="search-input" placeholder="🔍 Поиск бонуса по названию или описанию..." onkeyup="filterBonuses()">
        </div>
        <div class="filter-buttons">
            <button class="filter-btn active" onclick="setFilter('all', this)">Все</button>
            <button class="filter-btn" onclick="setFilter('green', this)">🟢 Зелёные</button>
            <button class="filter-btn" onclick="setFilter('blue', this)">🔵 Синие</button>
            <button class="filter-btn" onclick="setFilter('legendary', this)">🟡 Легендарные</button>
            <button class="filter-btn" onclick="setFilter('curse', this)">🔴 Проклятия</button>
            <button class="filter-btn" onclick="setFilter('set', this)">🟣 Метки (Сеты)</button>
        </div>
    </div>

    <!-- Список бонусов -->
    <div class="bonuses-grid" id="bonusesGrid">
        {% for bonus in site.data.voidgame_bonuses %}
        <div class="bonus-card rarity-{{ bonus.rarity }}" data-rarity="{{ bonus.rarity }}" data-name="{{ bonus.name | downcase }}" data-desc="{{ bonus.description | downcase }}">
            <div class="bonus-content-top">
                <div class="bonus-header">
                    <div class="bonus-icon-wrapper">
                        <img src="/assets/img/bonuses/{{ bonus.icon }}" alt="{{ bonus.name }}" class="bonus-icon" onerror="this.src='/assets/img/icon_voidgame.jpeg'">
                    </div>
                    <div class="bonus-meta">
                        <h3 class="bonus-name">{{ bonus.name }}</h3>
                        <span class="bonus-badge badge-{{ bonus.rarity }}">{{ bonus.rarity_ru }}</span>
                    </div>
                </div>
                <div class="bonus-description">
                    {{ bonus.description }}
                </div>
            </div>
            <div class="bonus-type">
                {{ bonus.type }}
            </div>
        </div>
        {% endfor %}
    </div>
</div>

<script>
let currentFilter = 'all';

function setFilter(rarity, btn) {
    // Сбросить активную кнопку
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    
    currentFilter = rarity;
    filterBonuses();
}

function filterBonuses() {
    const searchVal = document.getElementById('wikiSearch').value.toLowerCase();
    const cards = document.querySelectorAll('.bonus-card');
    
    cards.forEach(card => {
        const cardRarity = card.getAttribute('data-rarity');
        const name = card.getAttribute('data-name');
        const desc = card.getAttribute('data-desc');
        
        const matchesSearch = name.includes(searchVal) || desc.includes(searchVal);
        const matchesFilter = currentFilter === 'all' || cardRarity === currentFilter;
        
        if (matchesSearch && matchesFilter) {
            card.style.display = 'flex';
        } else {
            card.style.display = 'none';
        }
    });
}
</script>
