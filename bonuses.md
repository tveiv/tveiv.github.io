---
layout: default
title: "Бонусы и механики VoidGame"
permalink: /bonuses/
---

<style>
/* CSS для интерактивной энциклопедии бонусов VoidGame */
.wiki-container {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    color: #e0e0e0;
    margin: 20px 0;
}

.search-filter-section {
    background: #10121e;
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 25px;
    box-shadow: 0 4px 25px rgba(0, 0, 0, 0.6);
}

.search-wrapper {
    position: relative;
    margin-bottom: 15px;
}

.search-input {
    width: 100%;
    padding: 12px 15px;
    background: rgba(15, 17, 28, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #fff;
    font-size: 16px;
    outline: none;
    transition: all 0.3s ease;
}

.search-input:focus {
    border-color: #2196f3;
    box-shadow: 0 0 10px rgba(33, 150, 243, 0.3);
}

.filter-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

.filter-btn {
    padding: 8px 16px;
    background: rgba(15, 17, 28, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    color: #aaa;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s ease;
}

.filter-btn:hover {
    color: #fff;
    border-color: rgba(255, 255, 255, 0.3);
}

.filter-btn.active {
    background: #2196f3;
    color: #fff;
    border-color: #2196f3;
    box-shadow: 0 0 10px rgba(33, 150, 243, 0.4);
}

.filter-btn.active[data-filter="green"] { background: #2e7d32; border-color: #2e7d32; box-shadow: 0 0 10px rgba(46, 125, 80, 0.4); }
.filter-btn.active[data-filter="blue"] { background: #1565c0; border-color: #1565c0; box-shadow: 0 0 10px rgba(21, 101, 192, 0.4); }
.filter-btn.active[data-filter="legendary"] { background: #ff9800; border-color: #ff9800; box-shadow: 0 0 10px rgba(255, 152, 0, 0.4); }
.filter-btn.active[data-filter="curse"] { background: #c62828; border-color: #c62828; box-shadow: 0 0 10px rgba(198, 40, 40, 0.4); }
.filter-btn.active[data-filter="set"] { background: #9c27b0; border-color: #9c27b0; box-shadow: 0 0 10px rgba(156, 39, 176, 0.4); }

/* Сетка бонусов */
.bonuses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
    margin-top: 15px;
}

.bonus-card {
    background: rgba(20, 22, 30, 0.75);
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

.bonus-card.rarity-green { border: 1px solid rgba(46, 125, 50, 0.25); }
.bonus-card.rarity-green::after { background: #2e7d32; }
.bonus-card.rarity-green:hover {
    box-shadow: 0 8px 24px rgba(46, 125, 50, 0.25);
    border-color: rgba(46, 125, 50, 0.6);
}

.bonus-card.rarity-blue { border: 1px solid rgba(21, 101, 192, 0.25); }
.bonus-card.rarity-blue::after { background: #1565c0; }
.bonus-card.rarity-blue:hover {
    box-shadow: 0 8px 24px rgba(21, 101, 192, 0.25);
    border-color: rgba(21, 101, 192, 0.6);
}

.bonus-card.rarity-legendary { border: 1px solid rgba(255, 152, 0, 0.25); }
.bonus-card.rarity-legendary::after { background: #ff9800; }
.bonus-card.rarity-legendary:hover {
    box-shadow: 0 8px 24px rgba(255, 152, 0, 0.3);
    border-color: rgba(255, 152, 0, 0.7);
}

.bonus-card.rarity-curse { border: 1px solid rgba(198, 40, 40, 0.25); }
.bonus-card.rarity-curse::after { background: #c62828; }
.bonus-card.rarity-curse:hover {
    box-shadow: 0 8px 24px rgba(198, 40, 40, 0.3);
    border-color: rgba(198, 40, 40, 0.7);
}

.bonus-card.rarity-set { border: 1px solid rgba(156, 39, 176, 0.25); }
.bonus-card.rarity-set::after { background: #9c27b0; }
.bonus-card.rarity-set:hover {
    box-shadow: 0 8px 24px rgba(156, 39, 176, 0.3);
    border-color: rgba(156, 39, 176, 0.7);
}

.card-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 12px;
}

.card-icon {
    width: 40px;
    height: 40px;
    image-rendering: pixelated;
    background: rgba(255, 255, 255, 0.05);
    padding: 4px;
    border-radius: 8px;
    object-fit: contain;
}

.card-title {
    font-size: 18px;
    font-weight: bold;
    color: #ffffff;
    margin: 0;
}

.card-desc {
    font-size: 14px;
    color: #b0b0b0;
    line-height: 1.5;
    margin-bottom: 15px;
    flex-grow: 1;
}

.card-footer {
    border-top: 1px solid rgba(255, 255, 255, 0.05);
    padding-top: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
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
.badge-legendary { background: rgba(255, 152, 0, 0.15); color: #ffb74d; }
.badge-curse { background: rgba(198, 40, 40, 0.15); color: #e57373; }
.badge-set { background: rgba(156, 39, 176, 0.15); color: #ba68c8; }

.card-type {
    font-size: 12px;
    color: #888;
}

.no-results {
    grid-column: 1 / -1;
    text-align: center;
    padding: 40px;
    color: #888;
    display: none;
}
</style>

# Энциклопедия Бонусов и Механик VoidGame

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

    <!-- Сетка бонусов -->
    <div class="bonuses-grid" id="bonuses-grid">
        {% for bonus in site.data.voidgame_bonuses %}
        <div class="bonus-card rarity-{{ bonus.rarity }}" data-category="{{ bonus.rarity }}" data-name="{{ bonus.name | downcase }}" data-desc="{{ bonus.description | downcase }}">
            <div>
                <div class="card-header">
                    <img src="/assets/img/bonuses/{{ bonus.icon }}" class="card-icon" onerror="this.onerror=null; this.src='/assets/img/unknown.jpg';">
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
                    {% else %}{{ bonus.rarity }}{% endif %}
                </span>
                <span class="card-type">{{ bonus.type }}</span>
            </div>
        </div>
        {% endfor %}
        <div class="no-results" id="no-results">Ничего не найдено. Попробуйте изменить поисковый запрос или фильтр.</div>
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
        const activeFilterBtn = document.querySelector(".filter-btn.active");
        const activeFilter = activeFilterBtn ? activeFilterBtn.getAttribute("data-filter") : "all";
        let visibleCount = 0;

        cards.forEach(card => {
            const name = card.getAttribute("data-name") || "";
            const desc = card.getAttribute("data-desc") || "";
            const cat = card.getAttribute("data-category") || "";

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

## Особенности механики наград на аренах

В процессе прохождения арен Бездны игроки регулярно сталкиваются с выбором наград между волнами. Здесь действует несколько ключевых правил, определяющих выигрышную стратегию:

1. **Синергия «Небытие + Ничего»**: Как только вам выпадает перк **«Небытие»** (который теперь стал синим бонусом), всегда проверяйте наличие варианта **«Ничего»** в выборе наград. Это комбо даёт мощнейший прирост сразу двух характеристик — вы одновременно повышаете урон и получаете уклонение без каких-либо дебаффов.
2. **Метки и комплекты (Сеты)**: Для активации эффектов меток необходимо собирать снаряжение из одного комплекта (например, сет **Целителя** дарует неуязвимость и лечение после возрождения, а сет **Убийцы** разгоняет DPS за убийства). Перк **«Ключ к победе»** — идеальное дополнение, повышающее уровень всех собранных сетов на +1.
3. **Риск проклятий**: Проклятые бонусы дают сильные награды в двойном объёме или увеличивают локальную награду за волну, но могут сильно усложнить игру за счёт штрафов на характеристики или непроизвольные уклонения врагов.
