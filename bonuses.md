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
    background: #141414;
    border: 1px solid #2d2d2d;
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 25px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
}

.search-wrapper {
    position: relative;
    margin-bottom: 15px;
}

.search-input {
    width: 100%;
    padding: 12px 15px;
    background: #1d1d1d;
    border: 1px solid #444;
    border-radius: 8px;
    color: #fff;
    font-size: 16px;
    outline: none;
    transition: all 0.3s ease;
}

.search-input:focus {
    border-color: #9c27b0;
    box-shadow: 0 0 10px rgba(156, 39, 176, 0.3);
}

.filter-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

.filter-btn {
    padding: 8px 16px;
    background: #1d1d1d;
    border: 1px solid #333;
    border-radius: 20px;
    color: #aaa;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s ease;
}

.filter-btn:hover {
    color: #fff;
    border-color: #666;
}

.filter-btn.active {
    background: #9c27b0;
    color: #fff;
    border-color: #9c27b0;
    box-shadow: 0 0 10px rgba(156, 39, 176, 0.4);
}

/* Стили вкладок и карточек */
.bonuses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
    margin-top: 15px;
}

.bonus-card {
    background: #141414;
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

.bonus-card.rarity-green {
    border: 1px solid rgba(46, 125, 50, 0.3);
}
.bonus-card.rarity-green::after {
    background: #2e7d32;
}
.bonus-card.rarity-green:hover {
    box-shadow: 0 8px 24px rgba(46, 125, 50, 0.15);
    border-color: rgba(46, 125, 50, 0.6);
}

.bonus-card.rarity-blue {
    border: 1px solid rgba(21, 101, 192, 0.3);
}
.bonus-card.rarity-blue::after {
    background: #1565c0;
}
.bonus-card.rarity-blue:hover {
    box-shadow: 0 8px 24px rgba(21, 101, 192, 0.15);
    border-color: rgba(21, 101, 192, 0.6);
}

.bonus-card.rarity-legendary {
    border: 1px solid rgba(230, 81, 0, 0.3);
}
.bonus-card.rarity-legendary::after {
    background: #ff9800;
}
.bonus-card.rarity-legendary:hover {
    box-shadow: 0 8px 24px rgba(230, 81, 0, 0.2);
    border-color: rgba(230, 81, 0, 0.7);
}

.bonus-card.rarity-cursed {
    border: 1px solid rgba(198, 40, 40, 0.3);
}
.bonus-card.rarity-cursed::after {
    background: #c62828;
}
.bonus-card.rarity-cursed:hover {
    box-shadow: 0 8px 24px rgba(198, 40, 40, 0.2);
    border-color: rgba(198, 40, 40, 0.7);
}

.bonus-card.rarity-sets {
    border: 1px solid rgba(106, 27, 154, 0.3);
}
.bonus-card.rarity-sets::after {
    background: #9c27b0;
}
.bonus-card.rarity-sets:hover {
    box-shadow: 0 8px 24px rgba(106, 27, 154, 0.2);
    border-color: rgba(106, 27, 154, 0.7);
}

.card-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 12px;
}

.card-emoji {
    font-size: 24px;
    background: rgba(255, 255, 255, 0.05);
    padding: 6px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
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
    border-top: 1px solid #222;
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
.badge-legendary { background: rgba(230, 81, 0, 0.15); color: #ffb74d; }
.badge-cursed { background: rgba(198, 40, 40, 0.15); color: #e57373; }
.badge-sets { background: rgba(106, 27, 154, 0.15); color: #ba68c8; }

.card-stats {
    font-size: 13px;
    font-weight: 500;
    color: #e0e0e0;
}
</style>

# Энциклопедия Бонусов и Механик VoidGame

Добро пожаловать в раздел энциклопедии, посвящённый всем видам бонусов, перков, меток комплектов снаряжения и проклятий, которые вы встретите в **VoidGame на Cristalix**. 

Пользуйтесь удобной интерактивной таблицей ниже, чтобы моментально находить описание, характеристики и классификацию любого эффекта!

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
            <button class="filter-btn" data-filter="cursed">🔴 Проклятия</button>
            <button class="filter-btn" data-filter="sets">🟣 Метки (Сеты)</button>
        </div>
    </div>

    <!-- Сетка бонусов -->
    <div class="bonuses-grid" id="bonuses-grid">
        <div class="bonus-card rarity-green" data-category="green">
            <div>
                <div class="card-header">
                    <div class="card-emoji">⚔️</div>
                    <h3 class="card-title">Бонус урона</h3>
                </div>
                <p class="card-desc">Увеличивает наносимый персонажем урон на фиксированные 12%. В комбинации со способностью «Генезис» даёт дополнительные +4% за каждую активную способность в течение 10 секунд.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-green">Зелёный</span>
                <span class="card-stats">+12% урона</span>
            </div>
        </div>
        <div class="bonus-card rarity-green" data-category="green">
            <div>
                <div class="card-header">
                    <div class="card-emoji">💨</div>
                    <h3 class="card-title">Бонус уклонения</h3>
                </div>
                <p class="card-desc">Повышает вероятность полностью уклониться от вражеских атак. Шанс увеличивается по мере прокачки (составляет 10%, 20%, 30%, 40%, вплоть до 50%).</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-green">Зелёный</span>
                <span class="card-stats">+10% ... +50% уклонения</span>
            </div>
        </div>
        <div class="bonus-card rarity-green" data-category="green">
            <div>
                <div class="card-header">
                    <div class="card-emoji">❤️</div>
                    <h3 class="card-title">Бонус здоровья</h3>
                </div>
                <p class="card-desc">Увеличивает максимальный запас здоровья вашего героя (например, на +6% или на фиксированные +18 единиц).</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-green">Зелёный</span>
                <span class="card-stats">+6% или +18 HP</span>
            </div>
        </div>
        <div class="bonus-card rarity-green" data-category="green">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🏃</div>
                    <h3 class="card-title">Бонус скорости</h3>
                </div>
                <p class="card-desc">Увеличивает базовую скорость передвижения вашего персонажа, позволяя более эффективно маневрировать вокруг опасных монстров Бездны.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-green">Зелёный</span>
                <span class="card-stats">+Скорость бега</span>
            </div>
        </div>
        <div class="bonus-card rarity-green" data-category="green">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🗡️</div>
                    <h3 class="card-title">Острый клинок</h3>
                </div>
                <p class="card-desc">Затачивает оружие ближнего боя, значительно повышая вероятность нанести критический удар.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-green">Зелёный</span>
                <span class="card-stats">+Шанс крита</span>
            </div>
        </div>
        <div class="bonus-card rarity-green" data-category="green">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🧛</div>
                    <h3 class="card-title">Кровопролитие (Кровопитие)</h3>
                </div>
                <p class="card-desc">Дарует процентный вампиризм при нанесении урона любым оружием. Позволяет восстанавливать здоровье прямо в гуще боя.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-green">Зелёный</span>
                <span class="card-stats">+Вампиризм</span>
            </div>
        </div>
        <div class="bonus-card rarity-green" data-category="green">
            <div>
                <div class="card-header">
                    <div class="card-emoji">❓</div>
                    <h3 class="card-title">Ничего</h3>
                </div>
                <p class="card-desc">Сам по себе выбор пустой награды ничего не даёт, но при наличии активированной пассивной способности «Небытие» мгновенно дарует и бонус урона, и бонус уклонения.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-green">Зелёный</span>
                <span class="card-stats">Скрытая синергия</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌀</div>
                    <h3 class="card-title">Небытие (Многословие)</h3>
                </div>
                <p class="card-desc">Один из лучших пассивных перков. Полностью меняет суть выбора «Ничего»: теперь при выборе пустого слота вы получаете одновременно и бонус урона, и бонус уклонения.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Бафф слота «Ничего»</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🔗</div>
                    <h3 class="card-title">Связь с душой</h3>
                </div>
                <p class="card-desc">Связывает душу с союзником. Пока он находится в радиусе 8 блоков, ваш урон увеличивается. Дополнительно дарует 15% шанс полностью поглотить входящий урон (снижает до 0).</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+Урон у напарника, 15% уклона</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🔥</div>
                    <h3 class="card-title">Внутренние силы</h3>
                </div>
                <p class="card-desc">Пробуждает внутренний потенциал вашего героя, временно усиливая его боевые возможности.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+Боевой потенциал</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">⏳</div>
                    <h3 class="card-title">Теневой перезаряд</h3>
                </div>
                <p class="card-desc">Существенно ускоряет скорость перезарядки (колдаун) всех активных заклинаний и способностей персонажа.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+Ускорение способностей</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🐷</div>
                    <h3 class="card-title">Спокойствие разума</h3>
                </div>
                <p class="card-desc">Призывает верных свинок, которые следуют за персонажем, отвлекают агрессивных мобов и восстанавливают здоровье при их убийстве.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Отвлечение + Исцеление</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🧹</div>
                    <h3 class="card-title">Собиратель мусора</h3>
                </div>
                <p class="card-desc">Выбор любого обычного (зелёного) бонуса во время волн навсегда увеличивает ваше максимальное здоровье и исходящий урон на 2%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Перманентно +2% ХП/Урона</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🪐</div>
                    <h3 class="card-title">Мышь на Венере</h3>
                </div>
                <p class="card-desc">Полностью отключает получение любого урона от падения с любой высоты. Идеально сочетается со способностью «Возвышение на Юпитере».</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Иммунитет к падению</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🎭</div>
                    <h3 class="card-title">Приманка</h3>
                </div>
                <p class="card-desc">С шансом 50% дублирует спавнящихся обычных или элитных монстров, удваивая нагрузку, но увеличивая получаемую награду.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">50% шанс дублирования волн</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🧾</div>
                    <h3 class="card-title">Долг боли</h3>
                </div>
                <p class="card-desc">Накапливает 25% получаемого персонажем урона в виде отложенного значения («долга») для последующей активации эффектов.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Запись 25% урона</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🧪</div>
                    <h3 class="card-title">Секрет алхимиков</h3>
                </div>
                <p class="card-desc">Редкое древнее знание, напрямую увеличивающее силу применяемых вами заклинаний.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+Сила заклинаний</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🔮</div>
                    <h3 class="card-title">Эпическая фантазия</h3>
                </div>
                <p class="card-desc">Усиливает магические потоки персонажа, увеличивая общую эффективность всех заклинаний.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+Магический урон</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🤝</div>
                    <h3 class="card-title">Раб души</h3>
                </div>
                <p class="card-desc">Позволяет подчинить волю враждебного моба (например, кролика или громилы), превращая его во временного союзника, сражающегося на вашей стороне.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Подчинение мобов</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌱</div>
                    <h3 class="card-title">Генезис</h3>
                </div>
                <p class="card-desc">Каждое использование активных способностей увеличивает наносимый вами урон на 4%. Эффект складывается до 5 раз и длится 10 секунд.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+4%...20% урона от умений</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">✂️</div>
                    <h3 class="card-title">Ножницы пространства</h3>
                </div>
                <p class="card-desc">Каждые 10 секунд во время прохождения волны на арене спавнит свинку, которую можно быстро убить для восполнения здоровья.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Регулярный спавн свинок</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌌</div>
                    <h3 class="card-title">Звёздная завеса</h3>
                </div>
                <p class="card-desc">Окружает персонажа звёздной завесой: снижает получаемый урон на 100%, но полностью лишает вас возможности наносить урон противникам.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">100% неуязвимость, 0% урона</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🏳️</div>
                    <h3 class="card-title">Дух предстоящей победы</h3>
                </div>
                <p class="card-desc">В начале каждой волны снижает получаемый урон на 30%. Каждую секунду сила эффекта плавно затухает до нуля.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">-30% урона на старте волны</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">💥</div>
                    <h3 class="card-title">Добивание противника</h3>
                </div>
                <p class="card-desc">Также известен как эффект «Пожирателя энергии». Убийство врага с шансом 20% увеличивает максимальное здоровье и урон на 1% (стакается до 20%).</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">До +20% ХП/Урона за киллы</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🚨</div>
                    <h3 class="card-title">Снижение урона при низком HP</h3>
                </div>
                <p class="card-desc">В критический момент, когда здоровье падает ниже 30%, входящий урон снижается на 50% на протяжении 5 секунд.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">-50% урона на лоу-HP</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🤏</div>
                    <h3 class="card-title">Минимир</h3>
                </div>
                <p class="card-desc">Сжимает пространство вокруг персонажа, увеличивая его максимальный запас здоровья на стабильные 11%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+11% макс. HP</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌙</div>
                    <h3 class="card-title">Башна яркой Луны</h3>
                </div>
                <p class="card-desc">Поверженный вами враг взрывается в радиусе 12 блоков, нанося всем задетым противникам урон, равный значению последнего удара по нему.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Взрыв мобов при смерти</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🗿</div>
                    <h3 class="card-title">Двигайся как камень</h3>
                </div>
                <p class="card-desc">Опасный перк: при выборе наград с шансом 20% выбранный бонус превратится в коварного мимика, нападающего на игрока.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">20% шанс спавна мимика</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">📌</div>
                    <h3 class="card-title">Игла ярости</h3>
                </div>
                <p class="card-desc">Повышает шанс критического удара (или урон) на 10%, но взамен снижает эффективность любого входящего исцеления на 5%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+10% крита, -5% лечения</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">💎</div>
                    <h3 class="card-title">Росток алмазного дерева</h3>
                </div>
                <p class="card-desc">Каждые 10 секунд накапливает до 10 зарядов. При получении урона заряды расходуются, снижая входящие повреждения.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Щит из стакающихся зарядов</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🏆</div>
                    <h3 class="card-title">Чаша победителей</h3>
                </div>
                <p class="card-desc">Призывает усиленных врагов. Обычный монстр при спавне с шансом 10% превращается в грозного двухзвёздного чемпиона.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+Сложность, +Награда</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🧊</div>
                    <h3 class="card-title">Куб неуязвимости</h3>
                </div>
                <p class="card-desc">Каждый пятый полученный персонажем удар от любого источника наносит на 40% меньше входящего урона.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Защита каждого 5-го удара</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🕶️</div>
                    <h3 class="card-title">Сплетение теней</h3>
                </div>
                <p class="card-desc">Полностью скрывает названия и описания бонусов при выборе наград. Повторный выбор этого перка также скроет их цветовую редкость.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Слепой выбор наград</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">📣</div>
                    <h3 class="card-title">Эхо волшебства</h3>
                </div>
                <p class="card-desc">Когда вы применяете заклинание, ближайший противник с шансом 20% мгновенно повторяет и кастует его в ответ.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">20% шанс эха заклинания у врага</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">⬛</div>
                    <h3 class="card-title">Чёрный прямоугольник</h3>
                </div>
                <p class="card-desc">Увеличивает максимальное здоровье на 10%, а физический размер тела — на 20%. Если здоровье падает ниже 30%, входящий урон снижается на 20%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+10% ХП, +20% к размеру хитбокса</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌩️</div>
                    <h3 class="card-title">Прострел с Юпитера</h3>
                </div>
                <p class="card-desc">Каждые 10 секунд во время волны персонажа поражает молния, нанося урон в размере 5% от его максимального здоровья.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Постоянный урон молнией</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">⭐</div>
                    <h3 class="card-title">Эффект звездного чемпиона</h3>
                </div>
                <p class="card-desc">Обычные мобы при спавне с шансом 15% получают звезду чемпиона. Каждая звезда увеличивает наносимый им урон на 10%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+Сложность волны</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">😨</div>
                    <h3 class="card-title">Панифобия</h3>
                </div>
                <p class="card-desc">Если количество накопленных звёзд у персонажа падает ниже 200 единиц, сила ваших заклинаний снижается на 15%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Штраф магии при низком балансе</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🏪</div>
                    <h3 class="card-title">Эффект торгового обмена</h3>
                </div>
                <p class="card-desc">При покупке в магазине вы теряете 10% от стоимости бонуса, но при прокрутке колеса фортуны получаете звёзды обратно в эквиваленте цены.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Экономическая синергия</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🔪</div>
                    <h3 class="card-title">Нож на перестрелке</h3>
                </div>
                <p class="card-desc">Боевой тактический перк, меняющий стиль игры и наносимый физический урон в ближнем бою.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+Ближний бой</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">💤</div>
                    <h3 class="card-title">Мирный сон</h3>
                </div>
                <p class="card-desc">Увеличивает все критические характеристики вашего персонажа на +1, но снижает локальную награду за волну на 1.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+1 к криту, -1 к награде</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌦️</div>
                    <h3 class="card-title">Прогноз погоды</h3>
                </div>
                <p class="card-desc">Каждую секунду случайный противник в радиусе 3 блоков получает урон в размере 20% от текущего уровня здоровья игрока.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">Пассивное АуЕ выжигание мобов</span>
            </div>
        </div>
        <div class="bonus-card rarity-blue" data-category="blue">
            <div>
                <div class="card-header">
                    <div class="card-emoji">💧</div>
                    <h3 class="card-title">Бонус маны</h3>
                </div>
                <p class="card-desc">Увеличивает максимальный запас маны на 8 единиц и снижает затраты на использование заклинаний на стабильные 2%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-blue">Синий</span>
                <span class="card-stats">+8 маны, -2% стоимости магии</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌟</div>
                    <h3 class="card-title">Моё последнее перерождение (в мире звёзд)</h3>
                </div>
                <p class="card-desc">После гибели персонаж мгновенно возрождается с неуязвимостью на 5 секунд. Однако максимальный запас здоровья снижается на 10%. Наносимый урон увеличивается на 35%, а шанс крита падает на 25%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">Реанимация, +35% урона, -10% HP</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">❄️</div>
                    <h3 class="card-title">Ледяная колыбель (Ледяной куб)</h3>
                </div>
                <p class="card-desc">Помещает персонажа в ледяной куб. В нём нельзя бить мечом, но восстанавливает 100% ХП, даёт неуязвимость, +23% к шансу крита и игнорирует любые запреты на магию.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">Полное восстановление и неуязвимость</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">☄️</div>
                    <h3 class="card-title">Квазар</h3>
                </div>
                <p class="card-desc">После секундной задержки выпускает вокруг персонажа 8 лучей, наносящих урон в x2 от дополнительных характеристик оружия. С луком количество лучей удваивается до 16.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">8 или 16 мощных лучей урона</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🚀</div>
                    <h3 class="card-title">Возвышение на Юпитере</h3>
                </div>
                <p class="card-desc">Позволяет совершать двойной прыжок и снижает урон от падения. Увеличивает критшанс на 15% за каждый пролеченный блок (при падении выше 4 блоков). Нанесение урона восстанавливает 10 маны.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">Двойной прыжок, крит от высоты</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">💀</div>
                    <h3 class="card-title">Взгляд убийцы</h3>
                </div>
                <p class="card-desc">Полностью уничтожает случайную часть надетой экипировки, но взамен дарует колоссальные боевые баффы: +25% к шансу крита и +10% к вампиризму.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">Потеря брони взамен на крит и отжор</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">👥</div>
                    <h3 class="card-title">Мрачная тень (Друг боли)</h3>
                </div>
                <p class="card-desc">В начале каждой волны призывает вашу теневую копию, здоровье которой равно 40% от вашего глобального запаса здоровья.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">Призыв теневого двойника</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🧪</div>
                    <h3 class="card-title">Посох слизней</h3>
                </div>
                <p class="card-desc">Призывает на арену маленьких дружественных слизней, которые атакуют противников и наносят урон, равный урону самого игрока.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">Призыв боевых слизней</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🏹</div>
                    <h3 class="card-title">Эффект вексов (Свойства лука)</h3>
                </div>
                <p class="card-desc">Особое свойство редкого лука: каждое убийство противника призывает тени (вексов), которые наносят 400% от вашего максимального урона в течение 3 секунд.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">Призыв теней с 400% урона за убийство</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🗺️</div>
                    <h3 class="card-title">Карта созвездия</h3>
                </div>
                <p class="card-desc">Легендарный предмет модификации: даёт огромный перманентный буст к добыче ресурсов, увеличивая бонус лута на 100% и количество лута на 5%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">+100% бонуса лута, +5% количества</span>
            </div>
        </div>
        <div class="bonus-card rarity-legendary" data-category="legendary">
            <div>
                <div class="card-header">
                    <div class="card-emoji">📖</div>
                    <h3 class="card-title">Сказки о звёздах</h3>
                </div>
                <p class="card-desc">Предмет во вторую руку. Увеличивает максимальный запас здоровья на 1 единицу и накладывает постоянный эффект регенерации.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-legendary">Легендарный</span>
                <span class="card-stats">+1 HP, постоянный реген</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">👹</div>
                    <h3 class="card-title">Паранойя победителя</h3>
                </div>
                <p class="card-desc">Заставляет игрока всегда автоматически выбирать первый вариант из всех предложенных наград. Взамен выбранный бонус выдаётся в двойном объёме (X2).</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">Автовыбор первого бонуса x2</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">📉</div>
                    <h3 class="card-title">Унижение</h3>
                </div>
                <p class="card-desc">Дает врагам 15% шанс уклониться от ваших ударов. Любой урон по вам с шансом 10% резонирует по союзникам в размере 25%. Каждые 15 сек здоровье скрывается.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">+15% уклона у мобов, урон по союзникам</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🩸</div>
                    <h3 class="card-title">Проклятие крови</h3>
                </div>
                <p class="card-desc">Опасное дебафф-проклятие, негативно влияющее на здоровье персонажа во время прохождения арен Бездны.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">Ослабление крови</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">💔</div>
                    <h3 class="card-title">Проклятие мультивыбора</h3>
                </div>
                <p class="card-desc">Ограничивает гибкость прокачки: навсегда уменьшает количество доступных карт наград при выборе после волны на 1.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">На 1 выбор награды меньше</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">👁️</div>
                    <h3 class="card-title">Фатальная бессонница</h3>
                </div>
                <p class="card-desc">Каждую волну даёт +20% к криту. Но если за 5 волн вы не выберете копию этого проклятия, ваш герой мгновенно получит смертельный урон.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">+20% крит урона, таймер смерти на 5 волн</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🧿</div>
                    <h3 class="card-title">Взгляд бездны 2 (Взгляд Расимы)</h3>
                </div>
                <p class="card-desc">Каждые 10 секунд во время прохождения волны взгляд (камера) игрока жестко фиксируется в одной точке на 1 секунду, лишая обзора.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">Фиксация камеры на 1 сек каждые 10 сек</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🎭</div>
                    <h3 class="card-title">Паранойя предателя</h3>
                </div>
                <p class="card-desc">Скрытый психологический дебафф, встречающийся при исследовании глубин Кошмара Чёрной дыры.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">Проклятие Кошмара</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🤐</div>
                    <h3 class="card-title">Социофобия</h3>
                </div>
                <p class="card-desc">Если вы находитесь в радиусе 5 блоков рядом со своим союзником, ваш наносимый урон принудительно снижается на 20%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">-20% урона рядом с союзником</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌋</div>
                    <h3 class="card-title">Зеркальный</h3>
                </div>
                <p class="card-desc">При выборе наград пол под игроками заливается смертоносной магмой. Игроки вынуждены постоянно бегать и прыгать при выборе бонуса.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">Магма под ногами во время выбора</span>
            </div>
        </div>
        <div class="bonus-card rarity-cursed" data-category="cursed">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🐘</div>
                    <h3 class="card-title">Свинцовый слоник</h3>
                </div>
                <p class="card-desc">Дебафф характеристик: снижает HP на 10%, урон на 15%, а скорость бега — на 50%. Взамен даёт +5% вампиризма и снижает получаемый урон на 10%.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-cursed">Проклятие</span>
                <span class="card-stats">-10% HP, -15% урона, -50% скорости, +5% вампа</span>
            </div>
        </div>
        <div class="bonus-card rarity-sets" data-category="sets">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🧙</div>
                    <h3 class="card-title">Метка волшебника</h3>
                </div>
                <p class="card-desc">Сетовый бонус талисмана/комплекта снаряжения. Напрямую дарует персонажу +4 к броне и значительно ускоряет регенерацию здоровья на +7 единиц.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-sets">Метка</span>
                <span class="card-stats">+4 брони, +7 регенерации</span>
            </div>
        </div>
        <div class="bonus-card rarity-sets" data-category="sets">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🌋</div>
                    <h3 class="card-title">Метка бедствия</h3>
                </div>
                <p class="card-desc">Сетовый бонус снаряжения Бедствия. Увеличивает физический размер и площадь поражения всех заклинаний на 20%, а также продлевает их длительность.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-sets">Метка</span>
                <span class="card-stats">+20% к размеру и длительности магии</span>
            </div>
        </div>
        <div class="bonus-card rarity-sets" data-category="sets">
            <div>
                <div class="card-header">
                    <div class="card-emoji">💚</div>
                    <h3 class="card-title">Метка целителя</h3>
                </div>
                <p class="card-desc">Мощный сет выживания: +10% здоровья, +2% вампиризма. После гибели возрождает с 20% здоровья, даёт неуязвимость на 3 секунды и +20% к лечению на 20 сек.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-sets">Метка</span>
                <span class="card-stats">Реанимация, +10% HP, +2% вампа</span>
            </div>
        </div>
        <div class="bonus-card rarity-sets" data-category="sets">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🩸</div>
                    <h3 class="card-title">Метка убийцы</h3>
                </div>
                <p class="card-desc">Сет для DPS-героев: увеличивает критшанс на 5%. Каждое убийство повышает урон на определённый процент (складывается до 10 раз, длится 30 сек).</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-sets">Метка</span>
                <span class="card-stats">+5% крита, стакающийся урон за киллы</span>
            </div>
        </div>
        <div class="bonus-card rarity-sets" data-category="sets">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🛡️</div>
                    <h3 class="card-title">Метка победителя</h3>
                </div>
                <p class="card-desc">Сетовый бонус, сосредоточенный на минимизации входящего урона. Постоянно и пассивно снижает любой получаемый персонажем урон.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-sets">Метка</span>
                <span class="card-stats">Снижение входящего урона</span>
            </div>
        </div>
        <div class="bonus-card rarity-sets" data-category="sets">
            <div>
                <div class="card-header">
                    <div class="card-emoji">🔑</div>
                    <h3 class="card-title">Ключ к победе</h3>
                </div>
                <p class="card-desc">Особый сетовый катализатор. Увеличивает количество эффектов для абсолютно всех бонусов собранного вами активного сета на +1 уровень.</p>
            </div>
            <div class="card-footer">
                <span class="card-badge badge-sets">Метка</span>
                <span class="card-stats">Усиление всех бонусов активного сета на +1</span>
            </div>
        </div>
    </div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const searchInput = document.getElementById('wiki-search');
    const filterButtons = document.querySelectorAll('.filter-btn');
    const cards = document.querySelectorAll('.bonus-card');

    function filterCards() {
        const query = searchInput.value.toLowerCase().trim();
        const activeFilter = document.querySelector('.filter-btn.active').getAttribute('data-filter');

        cards.forEach(card => {
            const name = card.querySelector('.card-title').textContent.toLowerCase();
            const desc = card.querySelector('.card-desc').textContent.toLowerCase();
            const cat = card.getAttribute('data-category');

            const matchesSearch = name.includes(query) || desc.includes(query);
            const matchesFilter = activeFilter === 'all' || cat === activeFilter;

            if (matchesSearch && matchesFilter) {
                card.style.display = 'flex';
            } else {
                card.style.display = 'none';
            }
        });
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

## Особенности механики наград на аренах

В процессе прохождения арен Бездны игроки регулярно сталкиваются с выбором наград между волнами. Здесь действует несколько ключевых правил, определяющих выигрышную стратегию:

1. **Синергия «Небытие + Ничего»** [51]: Как только вам выпадает перк **«Небытие»** (зелёная/синяя редкость), всегда проверяйте наличие варианта **«Ничего»** в выборе наград. Это комбо даёт мощнейший прирост сразу двух характеристик — вы одновременно повышаете урон и получаете уклонение без каких-либо дебаффов.
2. **Метки и комплекты (Сеты)** [172, 275]: Для активации эффектов меток необходимо собирать снаряжение из одного комплекта (например, сет **Целителя** дарует неуязвимость и лечение после возрождения, а сет **Убийцы** разгоняет DPS за убийства). Перк **«Ключ к победе»** [279] — идеальное дополнение, повышающее уровень всех собранных сетов на +1.
3. **Риск проклятий**: Проклятые бонусы (например, **«Паранойя победителя»** [2] или **«Унижение»** [3]) дают сильные награды в двойном объёме или увеличивают локальную награду за волну, но могут сильно усложнить игру за счёт штрафов на характеристики или непроизвольные уклонения врагов.
