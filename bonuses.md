---
layout: default
title: "Энциклопедия Эффектов"
permalink: /bonuses/
---

<style>
/* CSS для интерактивной Вики-таблицы VoidGame */
.wiki-container {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    color: #e0e0e0;
    margin: 20px 0;
}

/* Секция поиска и фильтрации */
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
    box-sizing: border-box; /* КРИТИЧЕСКИЙ ФИКС: упаковывает padding внутрь 100% ширины */
    transition: all 0.3s ease;
}

.search-input:focus {
    border-color: #ffd54f;
    box-shadow: 0 0 10px rgba(255, 213, 79, 0.3);
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
    background: #ffd54f;
    color: #10121e;
    border-color: #ffd54f;
    font-weight: bold;
    box-shadow: 0 0 12px rgba(255, 213, 79, 0.4);
}

.filter-btn.active[data-filter="green"] { background: #2e7d32; color: #fff; border-color: #2e7d32; box-shadow: 0 0 10px rgba(46, 125, 80, 0.4); }
.filter-btn.active[data-filter="blue"] { background: #1565c0; color: #fff; border-color: #1565c0; box-shadow: 0 0 10px rgba(21, 101, 192, 0.4); }
.filter-btn.active[data-filter="legendary"] { background: #ff9800; color: #fff; border-color: #ff9800; box-shadow: 0 0 10px rgba(255, 152, 0, 0.4); }
.filter-btn.active[data-filter="curse"] { background: #c62828; color: #fff; border-color: #c62828; box-shadow: 0 0 10px rgba(198, 40, 40, 0.4); }

/* Таблица на десктопе */
.wiki-table-container {
    background: rgba(20, 22, 30, 0.75);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0,0,0,0.5);
}

.wiki-table {
    width: 100%;
    border-collapse: collapse;
    text-align: left;
}

.wiki-table th, .wiki-table td {
    padding: 12px 18px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.wiki-table th {
    background: rgba(15, 17, 28, 0.95);
    color: #fff;
    font-weight: bold;
    text-transform: uppercase;
    font-size: 13px;
    letter-spacing: 0.8px;
}

.wiki-table tr:last-child td {
    border-bottom: none;
}

.wiki-icon {
    width: 32px;
    height: 32px;
    image-rendering: pixelated;
    background: rgba(255, 255, 255, 0.05);
    padding: 4px;
    border-radius: 6px;
    object-fit: contain;
    vertical-align: middle;
}

.wiki-name {
    font-size: 16px;
    font-weight: bold;
    color: #fff;
}

.wiki-desc {
    font-size: 14px;
    color: #b0b0b0;
    line-height: 1.5;
    margin: 0;
}

/* Minecraft Gold Highlight Styles */
.wiki-desc b, .wiki-desc strong {
    color: #ffd54f !important;
    text-shadow: 0 0 8px rgba(255, 213, 79, 0.4);
    font-weight: bold;
}

.wiki-desc u {
    color: #ffd54f !important;
    text-shadow: 0 0 8px rgba(255, 213, 79, 0.4);
    text-decoration: underline;
}

/* Баджики редкостей */
.wiki-badge {
    font-size: 11px;
    text-transform: uppercase;
    font-weight: bold;
    letter-spacing: 0.5px;
    padding: 4px 10px;
    border-radius: 6px;
    display: inline-block;
    text-align: center;
}

.badge-green { background: rgba(46, 125, 50, 0.15); color: #81c784; border: 1px solid rgba(46, 125, 50, 0.3); }
.badge-blue { background: rgba(21, 101, 192, 0.15); color: #64b5f6; border: 1px solid rgba(21, 101, 192, 0.3); }
.badge-legendary { background: rgba(255, 152, 0, 0.15); color: #ffb74d; border: 1px solid rgba(255, 152, 0, 0.3); }
.badge-curse { background: rgba(198, 40, 40, 0.15); color: #e57373; border: 1px solid rgba(198, 40, 40, 0.3); }

/* Интерактивная подсветка строк в зависимости от редкости */
.wiki-table tr {
    transition: background-color 0.25s ease, box-shadow 0.25s ease;
}

.wiki-table tr.rarity-green:hover { background-color: rgba(46, 125, 50, 0.08); }
.wiki-table tr.rarity-blue:hover { background-color: rgba(21, 101, 192, 0.08); }
.wiki-table tr.rarity-legendary:hover { background-color: rgba(255, 152, 0, 0.08); }
.wiki-table tr.rarity-curse:hover { background-color: rgba(198, 40, 40, 0.08); }

.no-results {
    text-align: center;
    padding: 40px;
    color: #888;
    background: rgba(20, 22, 30, 0.75);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    display: none;
    font-size: 15px;
}

/* ===== МОБИЛЬНАЯ АДАПТАЦИЯ (Специально для Android 7.0 и старых WebView) ===== */
@media (max-width: 768px) {
    .wiki-table-container {
        background: transparent;
        border: none;
        box-shadow: none;
    }
    
    .wiki-table, .wiki-table thead, .wiki-table tbody, .wiki-table tr, .wiki-table td {
        display: block;
        width: 100%;
        box-sizing: border-box;
    }
    
    .wiki-table thead {
        display: none; /* Скрываем заголовки столбцов */
    }
    
    .wiki-table tr {
        background: rgba(20, 22, 30, 0.85);
        border: 1px solid rgba(255, 255, 255, 0.08);
        border-radius: 12px;
        padding: 16px;
        margin-bottom: 15px;
        position: relative;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.4);
    }
    
    .wiki-table td {
        border: none;
        padding: 0;
        margin-bottom: 8px;
    }
    
    .wiki-table td:last-child {
        margin-bottom: 0;
    }
    
    /* Иконка слева */
    .td-icon {
        float: left;
        width: auto;
        margin-right: 12px;
        margin-bottom: 0;
    }
    
    /* Название справа от иконки */
    .td-name {
        display: block;
        padding-top: 2px;
        margin-bottom: 4px;
    }
    
    .wiki-name {
        font-size: 18px;
    }
    
    /* Редкость */
    .td-rarity {
        display: block;
        margin-bottom: 12px;
    }
    
    /* Описание на полную ширину снизу */
    .td-desc {
        clear: both;
        padding-top: 12px !important;
        border-top: 1px solid rgba(255, 255, 255, 0.08);
    }
}
</style>

# Энциклопедия Бонусов и Эффектов Бездны

Добро пожаловать в структурированную базу данных всех бонусов, перков и проклятий в режиме **VoidGame на Cristalix**. 

Пользуйтесь удобной интерактивной Вики-таблицей ниже, чтобы моментально находить точное описание, иконку и свойства любого игрового эффекта!

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
        </div>
    </div>

    <!-- Таблица бонусов -->
    <div class="wiki-table-container">
        <table class="wiki-table" id="bonuses-table">
            <thead>
                <tr>
                    <th style="width: 70px; text-align: center;">Иконка</th>
                    <th style="width: 220px;">Название</th>
                    <th style="width: 150px; text-align: center;">Редкость</th>
                    <th>Описание эффекта</th>
                </tr>
            </thead>
            <tbody>
                {% for bonus in site.data.voidgame_bonuses %}
                <tr class="bonus-row rarity-{{ bonus.rarity }}" data-category="{{ bonus.rarity }}" data-name="{{ bonus.name | downcase }}" data-desc="{{ bonus.description | downcase }}">
                    <td class="td-icon" style="text-align: center;">
                        <img src="/assets/img/bonuses/{{ bonus.icon }}" class="wiki-icon" onerror="this.onerror=null; this.src='/assets/img/unknown.jpg';">
                    </td>
                    <td class="td-name">
                        <span class="wiki-name">{{ bonus.name }}</span>
                    </td>
                    <td class="td-rarity" style="text-align: center;">
                        <span class="wiki-badge badge-{{ bonus.rarity }}">
                            {% if bonus.rarity == 'green' %}🟢 Зелёный
                            {% elsif bonus.rarity == 'blue' %}🔵 Синий
                            {% elsif bonus.rarity == 'legendary' %}🟡 Легендарный
                            {% elsif bonus.rarity == 'curse' %}🔴 Проклятие
                            {% else %}{{ bonus.rarity_ru }}{% endif %}
                        </span>
                    </td>
                    <td class="td-desc">
                        <p class="wiki-desc">{{ bonus.description | markdownify }}</p>
                    </td>
                </tr>
                {% endfor %}
            </tbody>
        </table>
    </div>
    
    <div class="no-results" id="no-results">
        Ничего не найдено. Попробуйте изменить поисковый запрос или фильтр Бездны.
    </div>
</div>

<script>
// ПОЛНОСТЬЮ СОВМЕСТИМЫЙ ES5 СЦЕНАРИЙ (БЕЗ СТРЕЛОЧНЫХ ФУНКЦИЙ И FOREACH НА NODELIST)
document.addEventListener("DOMContentLoaded", function() {
    var searchInput = document.getElementById("wiki-search");
    var filterButtons = document.querySelectorAll(".filter-btn");
    var rows = document.querySelectorAll(".bonus-row");
    var noResults = document.getElementById("no-results");
    var tableContainer = document.querySelector(".wiki-table-container");

    function filterCards() {
        var query = searchInput ? searchInput.value.toLowerCase().trim() : "";
        var activeFilterBtn = document.querySelector(".filter-btn.active");
        var activeFilter = activeFilterBtn ? activeFilterBtn.getAttribute("data-filter") : "all";
        var visibleCount = 0;
        var i;

        for (i = 0; i < rows.length; i++) {
            var row = rows[i];
            var name = row.getAttribute("data-name") || "";
            var desc = row.getAttribute("data-desc") || "";
            var cat = row.getAttribute("data-category") || "";

            var matchesSearch = name.indexOf(query) !== -1 || desc.indexOf(query) !== -1;
            var matchesFilter = activeFilter === "all" || cat === activeFilter;

            if (matchesSearch && matchesFilter) {
                row.style.display = "";
                visibleCount++;
            } else {
                row.style.display = "none";
            }
        }

        if (visibleCount === 0) {
            noResults.style.display = "block";
            if (tableContainer) tableContainer.style.display = "none";
        } else {
            noResults.style.display = "none";
            if (tableContainer) tableContainer.style.display = "block";
        }
    }

    if (searchInput) {
        searchInput.addEventListener("input", filterCards);
    }

    var j;
    for (j = 0; j < filterButtons.length; j++) {
        var btn = filterButtons[j];
        btn.addEventListener("click", function() {
            var k;
            for (k = 0; k < filterButtons.length; k++) {
                filterButtons[k].classList.remove("active");
            }
            this.classList.add("active");
            filterCards();
        });
    }
});
</script>

## Особенности механики наград на аренах

В процессе прохождения арен Бездны игроки регулярно сталкиваются с выбором наград между волнами. Здесь действует несколько ключевых правил, определяющих выигрышную стратегию:

1. **Синергия «Небытие + Ничего»** [51]: Как только вам выпадает перк **«Небытие»** (зелёная/синяя редкость), всегда проверяйте наличие варианта **«Ничего»** в выборе наград. Это комбо даёт мощнейший прирост сразу двух характеристик — вы одновременно повышаете урон и получаете уклонение без каких-либо дебаффов.
2. **Риск проклятий**: Проклятые бонусы (например, **«Паранойя победителя»** [2] или **«Унижение»** [3]) дают сильные награды в двойном объёме или увеличивают локальную награду за волну, но могут сильно усложнить игру за счёт штрафов на характеристики или непроизвольные уклонения врагов.
