---
layout: default
title: "Энциклопедия эффектов VoidGame"
permalink: /bonuses/
---

<style>
/* CSS для энциклопедической Вики-таблицы VoidGame */
.wiki-container {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    color: #e4e8f1;
    margin: 20px 0;
}

/* Поиск и Фильтрация */
.wiki-controls {
    background: rgba(16, 18, 27, 0.95);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 25px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
}

.search-wrapper {
    position: relative;
    margin-bottom: 15px;
}

.search-input {
    width: 100%;
    padding: 14px 16px 14px 44px;
    background: rgba(10, 11, 18, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #fff;
    font-size: 16px;
    outline: none;
    box-sizing: border-box;
    transition: all 0.3s ease;
}

.search-input:focus {
    border-color: #ffd54f;
    box-shadow: 0 0 12px rgba(255, 213, 79, 0.25);
}

.search-icon {
    position: absolute;
    left: 15px;
    top: 50%;
    transform: translateY(-50%);
    color: rgba(255, 255, 255, 0.4);
    pointer-events: none;
    font-size: 18px;
}

.filter-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
}

.filter-btn {
    padding: 8px 16px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 20px;
    color: #aeb8d8;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s ease;
    display: flex;
    align-items: center;
    gap: 6px;
}

.filter-btn:hover {
    color: #fff;
    background: rgba(255, 255, 255, 0.1);
    border-color: rgba(255, 255, 255, 0.2);
}

.filter-btn.active {
    color: #fff;
    font-weight: 600;
}

.filter-btn.active[data-filter="all"] { background: rgba(255, 255, 255, 0.15); border-color: rgba(255, 255, 255, 0.3); }
.filter-btn.active[data-filter="green"] { background: rgba(46, 125, 50, 0.3); border-color: #2e7d32; box-shadow: 0 0 10px rgba(46, 125, 50, 0.3); }
.filter-btn.active[data-filter="blue"] { background: rgba(21, 101, 192, 0.3); border-color: #1565c0; box-shadow: 0 0 10px rgba(21, 101, 192, 0.3); }
.filter-btn.active[data-filter="legendary"] { background: rgba(230, 81, 0, 0.3); border-color: #ff9800; box-shadow: 0 0 10px rgba(230, 81, 0, 0.3); }
.filter-btn.active[data-filter="curse"] { background: rgba(198, 40, 40, 0.3); border-color: #c62828; box-shadow: 0 0 10px rgba(198, 40, 40, 0.3); }

/* Вики-таблица */
.wiki-table-wrapper {
    background: rgba(16, 18, 27, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 12px 40px rgba(0, 0, 0, 0.6);
    margin-bottom: 30px;
}

.wiki-table {
    width: 100%;
    border-collapse: collapse;
    text-align: left;
    font-size: 15px;
}

.wiki-table th {
    background: rgba(10, 11, 18, 0.95);
    color: #8fa0dd;
    font-weight: 700;
    text-transform: uppercase;
    font-size: 13px;
    letter-spacing: 1px;
    padding: 16px 20px;
    border-bottom: 2px solid rgba(255, 255, 255, 0.08);
}

.wiki-table tbody tr {
    border-bottom: 1px solid rgba(255, 255, 255, 0.04);
    transition: background-color 0.25s ease;
}

/* Эффекты свечения строк при наведении */
.wiki-table tbody tr:hover {
    background: rgba(255, 255, 255, 0.02);
}

.wiki-table tbody tr.rarity-row-green:hover {
    background: rgba(46, 125, 50, 0.05);
}
.wiki-table tbody tr.rarity-row-blue:hover {
    background: rgba(21, 101, 192, 0.05);
}
.wiki-table tbody tr.rarity-row-legendary:hover {
    background: rgba(230, 81, 0, 0.05);
}
.wiki-table tbody tr.rarity-row-curse:hover {
    background: rgba(198, 40, 40, 0.05);
}

.wiki-table td {
    padding: 14px 20px;
    vertical-align: middle;
}

/* Колонки */
.col-icon {
    width: 48px;
    text-align: center;
    padding-right: 0 !important;
}

.wiki-icon {
    width: 36px;
    height: 36px;
    image-rendering: pixelated;
    background: rgba(255, 255, 255, 0.03);
    padding: 3px;
    border-radius: 6px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    object-fit: contain;
    transition: transform 0.2s ease;
}

tr:hover .wiki-icon {
    transform: scale(1.1);
    border-color: rgba(255, 255, 255, 0.25);
}

.col-name {
    width: 220px;
    font-weight: 700;
}

.bonus-name-link {
    font-size: 16px;
    color: #ffffff;
    text-decoration: none;
    transition: text-shadow 0.2s ease;
}

/* Цвета редкостей */
.text-green { color: #81c784 !important; }
.text-blue { color: #64b5f6 !important; }
.text-legendary { color: #ffb74d !important; }
.text-curse { color: #e57373 !important; }

tr.rarity-row-green:hover .bonus-name-link { text-shadow: 0 0 8px rgba(129, 199, 132, 0.6); }
tr.rarity-row-blue:hover .bonus-name-link { text-shadow: 0 0 8px rgba(100, 181, 246, 0.6); }
tr.rarity-row-legendary:hover .bonus-name-link { text-shadow: 0 0 8px rgba(255, 183, 77, 0.6); }
tr.rarity-row-curse:hover .bonus-name-link { text-shadow: 0 0 8px rgba(229, 115, 115, 0.6); }

.col-rarity {
    width: 140px;
}

.col-type {
    width: 150px;
    font-size: 13px;
    color: #8fa0dd;
    opacity: 0.8;
}

.col-desc {
    line-height: 1.5;
    color: #cbd3ef;
}

/* Золотые выделения (как в игре) */
.col-desc b, .col-desc strong, .col-desc u {
    color: #ffd54f !important;
    font-weight: 700;
    text-shadow: 0 0 4px rgba(255, 213, 79, 0.2);
}

.col-desc u {
    text-decoration: underline;
}

/* Бейджи редкости */
.wiki-badge {
    font-size: 11px;
    text-transform: uppercase;
    font-weight: 700;
    letter-spacing: 0.5px;
    padding: 4px 8px;
    border-radius: 4px;
    display: inline-block;
    text-align: center;
}

.badge-green { background: rgba(46, 125, 50, 0.15); color: #81c784; border: 1px solid rgba(46, 125, 50, 0.3); }
.badge-blue { background: rgba(21, 101, 192, 0.15); color: #64b5f6; border: 1px solid rgba(21, 101, 192, 0.3); }
.badge-legendary { background: rgba(230, 81, 0, 0.15); color: #ffb74d; border: 1px solid rgba(230, 81, 0, 0.3); }
.badge-curse { background: rgba(198, 40, 40, 0.15); color: #e57373; border: 1px solid rgba(198, 40, 40, 0.3); }

.no-results {
    text-align: center;
    padding: 40px;
    color: #8fa0dd;
    font-size: 16px;
    display: none;
    border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

/* АДАПТИВНОСТЬ ПОД ТЕЛЕФОНЫ (Включая Android 7.0) */
@media (max-width: 768px) {
    .wiki-table th {
        display: none; /* Скрываем заголовки на мобилках */
    }
    
    .wiki-table tbody tr {
        display: block;
        padding: 15px;
        border-bottom: 1px solid rgba(255, 255, 255, 0.08);
    }
    
    .wiki-table td {
        display: block;
        padding: 5px 0 !important;
        width: 100% !important;
        box-sizing: border-box;
    }
    
    .col-icon {
        float: left;
        width: 45px !important;
        margin-right: 15px;
        padding-top: 0 !important;
    }
    
    .col-name {
        margin-left: 60px;
        padding-top: 0 !important;
    }
    
    .col-rarity {
        margin-left: 60px;
        display: inline-block !important;
        width: auto !important;
        margin-right: 10px;
    }
    
    .col-type {
        display: inline-block !important;
        width: auto !important;
        font-size: 12px;
    }
    
    .col-desc {
        clear: both; /* Сбрасываем обтекание картинки */
        padding-top: 10px !important;
        font-size: 14px;
    }
    
    .wiki-controls {
        padding: 15px;
    }
    
    .filter-pills {
        justify-content: center;
    }
    
    .filter-btn {
        font-size: 12px;
        padding: 6px 12px;
    }
}
</style>

# Энциклопедия Эффектов Бездны

Добро пожаловать в структурированную Вики-таблицу эффектов **VoidGame на Cristalix**! Здесь собраны все виды пассивных и активных бонусов, а также проклятий Бездны. 

Используйте поиск и панель фильтрации редкости, чтобы мгновенно просмотреть характеристики нужного предмета.

<div class="wiki-container">
    <!-- Поиск и Фильтрация -->
    <div class="wiki-controls">
        <div class="search-wrapper">
            <span class="search-icon">🔍</span>
            <input type="text" id="wiki-search" class="search-input" placeholder="Поиск по названию эффекта или описанию...">
        </div>
        <div class="filter-pills">
            <button class="filter-btn active" data-filter="all">📂 Все эффекты</button>
            <button class="filter-btn" data-filter="green">🟢 Обычные (Зелёные)</button>
            <button class="filter-btn" data-filter="blue">🔵 Редкие (Синие)</button>
            <button class="filter-btn" data-filter="legendary">🟡 Легендарные</button>
            <button class="filter-btn" data-filter="curse">🔴 Проклятия</button>
        </div>
    </div>

    <!-- Вики-таблица -->
    <div class="wiki-table-wrapper">
        <table class="wiki-table" id="wiki-table">
            <thead>
                <tr>
                    <th colspan="2">Эффект / Название</th>
                    <th>Редкость</th>
                    <th>Категория</th>
                    <th>Описание и характеристики</th>
                </tr>
            </thead>
            <tbody>
                {% for bonus in site.data.voidgame_bonuses %}
                <tr class="wiki-row rarity-row-{{ bonus.rarity }}" data-rarity="{{ bonus.rarity }}" data-name="{{ bonus.name | downcase }}" data-desc="{{ bonus.description | downcase }}">
                    <td class="col-icon">
                        <img src="/assets/img/bonuses/{{ bonus.icon }}" class="wiki-icon" onerror="this.onerror=null; this.src='/assets/img/unknown.jpg';">
                    </td>
                    <td class="col-name">
                        <span class="bonus-name-link {% if bonus.rarity == 'green' %}text-green{% elsif bonus.rarity == 'blue' %}text-blue{% elsif bonus.rarity == 'legendary' %}text-legendary{% elsif bonus.rarity == 'curse' %}text-curse{% endif %}">
                            {{ bonus.name }}
                        </span>
                    </td>
                    <td class="col-rarity">
                        <span class="wiki-badge {% if bonus.rarity == 'green' %}badge-green{% elsif bonus.rarity == 'blue' %}badge-blue{% elsif bonus.rarity == 'legendary' %}badge-legendary{% elsif bonus.rarity == 'curse' %}badge-curse{% endif %}">
                            {% if bonus.rarity == 'green' %}🟢 Зелёный
                            {% elsif bonus.rarity == 'blue' %}🔵 Синий
                            {% elsif bonus.rarity == 'legendary' %}🟡 Легендарный
                            {% elsif bonus.rarity == 'curse' %}🔴 Проклятие
                            {% else %}{{ bonus.rarity }}{% endif %}
                        </span>
                    </td>
                    <td class="col-type">
                        {{ bonus.type }}
                    </td>
                    <td class="col-desc">
                        {{ bonus.description | markdownify }}
                    </td>
                </tr>
                {% endfor %}
            </tbody>
        </table>
        <div class="no-results" id="no-results">Ничего не найдено. Попробуйте изменить поисковый запрос или фильтр.</div>
    </div>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const searchInput = document.getElementById("wiki-search");
    const filterButtons = document.querySelectorAll(".filter-btn");
    const rows = document.querySelectorAll(".wiki-row");
    const noResults = document.getElementById("no-results");

    function filterTable() {
        const query = searchInput.value.toLowerCase().trim();
        const activeFilterBtn = document.querySelector(".filter-btn.active");
        const activeFilter = activeFilterBtn ? activeFilterBtn.getAttribute("data-filter") : "all";
        let visibleCount = 0;

        rows.forEach(row => {
            const name = row.getAttribute("data-name") || "";
            const desc = row.getAttribute("data-desc") || "";
            const rarity = row.getAttribute("data-rarity") || "";

            const matchesSearch = name.includes(query) || desc.includes(query);
            const matchesFilter = activeFilter === 'all' || rarity === activeFilter;

            if (matchesSearch && matchesFilter) {
                row.style.display = '';
                visibleCount++;
            } else {
                row.style.display = 'none';
            }
        });

        if (visibleCount === 0) {
            noResults.style.display = 'block';
        } else {
            noResults.style.display = 'none';
        }
    }

    searchInput.addEventListener("input", filterTable);

    filterButtons.forEach(btn => {
        btn.addEventListener("click", function() {
            filterButtons.forEach(b => b.classList.remove("active"));
            this.classList.add("active");
            filterTable();
        });
    });
});
</script>

## Особенности механики наград на аренах Бездны

В процессе прохождения арен игроки регулярно сталкиваются с выбором наград между волнами. Здесь действует несколько ключевых правил, определяющих выигрышную стратегию:

1. **Синергия «Небытие + Ничего»**: Как только вам выпадает перк **«Небытие»** (редкий синий бонус), всегда проверяйте наличие варианта **«Ничего»** в выборе наград. Это комбо даёт мощнейший прирост сразу двух характеристик — вы одновременно повышаете урон и получаете уклонение без каких-либо дебаффов.
2. **Риск проклятий**: Проклятые бонусы дают сильные награды в двойном объёме или увеличивают локальную награду за волну, но могут сильно усложнить игру за счёт штрафов на характеристики или непроизвольные уклонения врагов.
3. **Губка и Воронка проклятий**: Отличные способы борьбы со штрафами. **«Губка»** способна впитывать дебаффы, а **«Воронка проклятий»** снижает время их действия и дарует полный иммунитет к опасному проклятию крови.
