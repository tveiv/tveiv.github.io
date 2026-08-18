---
layout: default
title: "Викторина Монксельда"
permalink: /trivia/
---

<style>
/* CSS для интерактивной шпаргалки Викторины Монксельда */
.trivia-container {
    max-width: 800px;
    margin: 20px auto;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    color: #e0e0e0;
}

.warning-banner {
    background: rgba(198, 40, 40, 0.15);
    border: 1px solid rgba(198, 40, 40, 0.4);
    border-left: 5px solid #ff5252;
    border-radius: 8px;
    padding: 16px 20px;
    margin-bottom: 25px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

.warning-title {
    font-size: 18px;
    color: #ff5252;
    font-weight: bold;
    margin: 0 0 8px 0;
    display: flex;
    align-items: center;
    gap: 8px;
}

.warning-desc {
    font-size: 14px;
    line-height: 1.5;
    color: #cccccc;
    margin: 0;
}

.warning-desc strong {
    color: #ffd54f;
}

.search-section {
    background: #10121e;
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 16px;
    margin-bottom: 25px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.5);
}

.search-input {
    width: 100%;
    padding: 12px 16px;
    background: rgba(15, 17, 28, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #fff;
    font-size: 16px;
    outline: none;
    box-sizing: border-box;
    transition: all 0.3s ease;
}

.search-input:focus {
    border-color: #ff5252;
    box-shadow: 0 0 10px rgba(255, 82, 82, 0.3);
}

.section-divider {
    font-size: 22px;
    color: #ffd54f;
    border-bottom: 2px solid rgba(255, 213, 79, 0.2);
    padding-bottom: 8px;
    margin: 40px 0 20px 0;
    font-weight: bold;
    text-shadow: 0 0 8px rgba(255, 213, 79, 0.25);
}

.trivia-list, .faq-list {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.trivia-card {
    background: rgba(20, 22, 30, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 10px;
    padding: 18px 24px;
    transition: all 0.25s ease;
    box-shadow: 0 4px 12px rgba(0,0,0,0.3);
}

.trivia-card:hover {
    transform: translateY(-2px);
    border-color: rgba(255, 82, 82, 0.3);
    box-shadow: 0 6px 18px rgba(255, 82, 82, 0.1);
}

.question-row {
    display: flex;
    gap: 12px;
    align-items: flex-start;
    margin-bottom: 12px;
}

.q-badge {
    background: #ff5252;
    color: #fff;
    font-weight: bold;
    font-size: 13px;
    padding: 3px 8px;
    border-radius: 4px;
    text-transform: uppercase;
}

.question-text {
    font-size: 16px;
    font-weight: bold;
    color: #ffffff;
    margin: 0;
    line-height: 1.4;
}

.answer-row {
    display: flex;
    gap: 12px;
    align-items: flex-start;
    padding-top: 12px;
    border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.a-badge {
    background: #4caf50;
    color: #fff;
    font-weight: bold;
    font-size: 13px;
    padding: 3px 8px;
    border-radius: 4px;
    text-transform: uppercase;
}

.answer-text {
    font-size: 16px;
    font-weight: bold;
    color: #ffd54f; /* Золотой цвет Minecraft */
    text-shadow: 0 0 8px rgba(255, 213, 79, 0.3);
    margin: 0;
    line-height: 1.4;
}

.trivia-note {
    font-size: 13px;
    color: #888888;
    margin: 8px 0 0 0;
    line-height: 1.4;
    padding-left: 56px;
}

.trivia-note strong {
    color: #bbb;
}

/* FAQ Styles */
.faq-card {
    background: rgba(15, 17, 26, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.05);
    border-radius: 8px;
    padding: 16px 20px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.25);
    transition: all 0.2s ease;
}

.faq-card:hover {
    border-color: rgba(255, 213, 79, 0.25);
    background: rgba(20, 22, 33, 0.9);
}

.faq-question {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 8px;
}

.faq-icon {
    font-size: 18px;
}

.faq-question h4 {
    margin: 0;
    font-size: 15px;
    color: #ffffff;
    font-weight: bold;
}

.faq-answer {
    font-size: 14px;
    color: #b0b0b0;
    line-height: 1.5;
    padding-left: 28px;
}

.faq-answer b {
    color: #ffd54f;
}

.no-results {
    text-align: center;
    padding: 40px;
    color: #888888;
    background: rgba(20, 22, 30, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 10px;
    display: none;
    font-size: 16px;
}

/* Адаптивность для мобильных телефонов Android 7.0 */
@media (max-width: 600px) {
    .trivia-card, .faq-card {
        padding: 14px 16px;
    }
    .question-text, .answer-text, .faq-question h4 {
        font-size: 15px;
    }
    .trivia-note, .faq-answer {
        padding-left: 0;
        margin-top: 12px;
        border-top: 1px dashed rgba(255, 255, 255, 0.05);
        padding-top: 8px;
    }
}
</style>

# Шпаргалка: Викторина Монксельда

Шпаргалка для моментального прохождения викторин от **Монксельда, Тегона и Вазора** во время арен Бездны.

<div class="trivia-container">
    <!-- Баннер с предупреждением -->
    <div class="warning-banner">
        <h3 class="warning-title">⚠️ Внимание: Множитель Наказания X5!</h3>
        <p class="warning-desc">
            Если у вас активен синий бонус <strong>«Викторина Монксельда»</strong>, все случайные события заменяются вопросами. 
            Правильный ответ удваивает награду (<strong>X2</strong>), но за любую ошибку штрафные дебаффы накладываются в 5 раз сильнее (<strong>X5</strong>). Пользуйтесь поиском, чтобы не слить катку!
        </p>
    </div>

    <!-- Поиск по ключевым словам -->
    <div class="search-section">
        <input type="text" id="trivia-search" class="search-input" placeholder="Введите ключевое слово (например: корова, яблоко, комар, связь)...">
    </div>

    <div class="section-divider">🔮 Вопросы Викторины</div>

    <!-- Список вопросов и ответов -->
    <div class="trivia-list" id="trivia-list">
        
        <div class="trivia-card" data-keywords="сколько зеленых бонусов обычных рулетка монксельд аккреционном диске">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Сколько всего зелёных бонусов в аккреционном диске?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">4</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Имеется в виду количество базовых обычных бонусов, которые падают на регулярных волнах первого подземелья «Аккреционный диск» (Бонус здоровья, Бонус маны, Бонус скорости, Бонус урона). Многие ошибаются, пытаясь прибавить «Ничего» или «Спокойствие разума».</p>
        </div>

        <div class="trivia-card" data-keywords="грибная корова молния тип грибов коричневая">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">В грибную корову бьёт молния. Что с ней произойдёт?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Тип грибов поменяется</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Корова превратится из обычной красной грибной коровы в коричневую грибную корову.</p>
        </div>

        <div class="trivia-card" data-keywords="скелет иссушитель лук свойство стрелы горение огненные поджог">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Скелет-иссушитель стреляет из лука. Каким свойством обладает его стрела?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Горение</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Вопреки ванильной логике иссушения, в игре его стрелы поджигают цель.</p>
        </div>

        <div class="trivia-card" data-keywords="сколько летучих мышей событие левитации шифт">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Сколько летучих мышей появляется в событии левитации?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">10</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Появляется ровно 10 летучих мышей, которых нужно поймать, зажимая клавишу Shift.</p>
        </div>

        <div class="trivia-card" data-keywords="точильный камень зачарованное золотое яблоко grinder grindstone">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Что произойдёт, если положить в точильный камень зачарованное золотое яблоко?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Ничего не произойдёт</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Точильный камень не взаимодействует с яблоками.</p>
        </div>

        <div class="trivia-card" data-keywords="зельеварочная стойка зелье силы светокаменная пыль пыльца сила эффекта">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">В зельеварочную стойку к зелью силы вы кладёте светокаменную пыль. Что произойдёт?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Сила эффекта увеличится, а длительность уменьшится</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Классический крафт усиленного зелья (Сила II) в Minecraft.</p>
        </div>

        <div class="trivia-card" data-keywords="зельеварочная стойка сахар ничего">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">В зельеварочную стойку вы кладёте сахар. Что произойдёт?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Ничего не произойдёт</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Сахар без предварительного приготовления основы (неловкого зелья) не сварит зелье скорости.</p>
        </div>

        <div class="trivia-card" data-keywords="зомби максимальный запас хп падение высота жив">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Зомби с максимальным запасом здоровья падает с максимальной высоты. Останется ли он жив?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Да, останется жив</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Зомби обладает высоким базовым здоровьем и естественной броней, что позволяет ему пережить падение.</p>
        </div>

        <div class="trivia-card" data-keywords="молния бьет в звезду незера пропадает звезда">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Молния бьёт в звезду Незера. Что произойдёт?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Она пропадёт</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Физический объект звезды уничтожается молнией.</p>
        </div>

        <div class="trivia-card" data-keywords="базовый критический крит урон процент по умолчанию">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Каков базовый критический урон по умолчанию?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">75%☆</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> По умолчанию критический удар наносит 75%☆ дополнительного урона.</p>
        </div>

        <div class="trivia-card" data-keywords="скелет максимальный запас хп падение высота жив умрет">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Скелет с максимальным запасом здоровья (20 HP) падает с максимальной высоты. Останется ли он жив?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Нет, он погибнет</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Скелет имеет 20 единиц здоровья и не обладает врождённой бронёй, поэтому падение с максимальной высоты нанесёт ему смертельный урон.</p>
        </div>

        <div class="trivia-card" data-keywords="зомби максимальный запас хп бьют мечом 20 урона жив">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Зомби с максимальным запасом здоровья бьют мечом на 20 единиц урона. Останется ли он жив?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Да, останется жив</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> У зомби есть врождённая броня в 2 единицы, которая поглощает 8%☆ входящего урона. Удар на 20 урона нанесёт ему лишь 18.4 урона, оставив его с 1.6 ХП☆.</p>
        </div>

        <div class="trivia-card" data-keywords="связь душой сколько критического крит урона дает">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Сколько критического урона даёт бонус «Связь душой»?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">0</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Этот бонус увеличивает обычный урон на 15%☆ и шанс критического удара на 15%☆, но сам критический урон не увеличивает.</p>
        </div>

        <div class="trivia-card" data-keywords="связь душой сколько шанса крит крита шанса дает">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Сколько шанса критического удара даёт бонус «Связь душой»?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">15</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> При нахождении в радиусе 8 блоков от союзника, ваш шанс критического удара увеличивается на 15☆ (15%☆).</p>
        </div>

        <div class="trivia-card" data-keywords="свинцовый слоник сколько защиты дает монксельд">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Сколько защиты даёт свинцовый слоник?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">10%☆</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Редкий синий бонус «Свинцовый слоник» снижает весь входящий урон на 10%☆ и повышает вампиризм на 5%☆, но урезает вашу скорость передвижения на 50%☆ и наносимый урон на 15%☆.</p>
        </div>

        <div class="trivia-card" data-keywords="сколько всего фантазий шкатулке этоля монксельд">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Сколько всего фантазий в шкатулке Этоля?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">16</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> В шкатулке Этоля находится ровно 16 фантазий, которые можно разблокировать.</p>
        </div>

    </div>

    <div class="section-divider">💬 Вопросы Игроков (FAQ)</div>

    <!-- Список FAQ -->
    <div class="faq-list" id="faq-list">
        
        <div class="faq-card" data-keywords="передать предмет другу обмен торговать трейд дюп">
            <div class="faq-question">
                <span class="faq-icon">❓</span>
                <h4>Как передать предмет другу или торговать в игре?</h4>
            </div>
            <div class="faq-answer">
                <p><b>Никак☆</b>. Передача предметов и свободный трейд между игроками полностью заблокированы разработчиком во избежание дюпов и уязвимостей.</p>
            </div>
        </div>

        <div class="faq-card" data-keywords="команда пати друг вместе зайти party warp">
            <div class="faq-question">
                <span class="faq-icon">❓</span>
                <h4>Как добавить друга в свою команду (пати)?</h4>
            </div>
            <div class="faq-answer">
                <p>Используйте команду <b>/party [ник]☆</b> для создания группы, а затем команду <b>/party warp☆</b>, чтобы перенести всю команду в ваше лобби или подземелье.</p>
            </div>
        </div>

        <div class="faq-card" data-keywords="использовать способность заклинание мана бинд клавиша">
            <div class="faq-question">
                <span class="faq-icon">❓</span>
                <h4>Как использовать активные способности предметов (заклинания)?</h4>
            </div>
            <div class="faq-answer">
                <p>Вам необходимо зайти в настройки управления или радиальное меню и назначить (забиндьте) активную способность на удобную клавишу (обычно по умолчанию используется <b>G☆</b> или <b>Q☆</b>). На использование способностей расходуется мана.</p>
            </div>
        </div>

        <div class="faq-card" data-keywords="броня зеленый бонус защита собиратель мусора">
            <div class="faq-question">
                <span class="faq-icon">❓</span>
                <h4>Есть ли смысл покупать обычный (зелёный) бонус брони?</h4>
            </div>
            <div class="faq-answer">
                <p>Да! Он навсегда увеличивает вашу базовую защиту на <b>6%☆</b>. Данный бонус невероятно силён в связке с редким бонусом <b>«Собиратель мусора»</b>, который дарует перманентные характеристики при поднятии зелёных перков.</p>
            </div>
        </div>

        <div class="faq-card" data-keywords="никтофобия векс досаждатель толкает спину">
            <div class="faq-question">
                <span class="faq-icon">❓</span>
                <h4>Что делает проклятие «Никтофобия»?</h4>
            </div>
            <div class="faq-answer">
                <p>Оно призывает на арену невидимого векса (досаждателя), который не наносит урона напрямую, но постоянно и очень неприятно <b>толкает вашего персонажа в спину☆</b> во время боя.</p>
            </div>
        </div>

        <div class="faq-card" data-keywords="паранойя победителя скрыть здоровье хп бар">
            <div class="faq-question">
                <span class="faq-icon">❓</span>
                <h4>Что делает проклятие «Паранойя победителя»?</h4>
            </div>
            <div class="faq-answer">
                <p>Оно скрывает отображение вашей полоски здоровья на <b>5☆</b> секунд каждые 15 секунд, заставляя драться «вслепую».</p>
            </div>
        </div>

    </div>

    <div class="no-results" id="no-results">
        Ни один вопрос не соответствует вашему поисковому запросу. Попробуйте ввести другое ключевое слово.
    </div>
</div>

<script>
// ПОЛНОСТЬЮ СОВМЕСТИМЫЙ ES5 СЦЕНАРИЙ (БЕЗ СТРЕЛОЧНЫХ ФУНКЦИЙ И FOREACH НА NODELIST)
document.addEventListener("DOMContentLoaded", function() {
    var searchInput = document.getElementById("trivia-search");
    var cards = document.querySelectorAll(".trivia-card");
    var faqs = document.querySelectorAll(".faq-card");
    var noResults = document.getElementById("no-results");

    if (searchInput) {
        searchInput.addEventListener("input", function() {
            var query = searchInput.value.toLowerCase().trim();
            var visibleCount = 0;
            var i, j;

            for (i = 0; i < cards.length; i++) {
                var card = cards[i];
                var keywords = card.getAttribute("data-keywords") || "";
                var question = card.querySelector(".question-text").textContent.toLowerCase();
                var answer = card.querySelector(".answer-text").textContent.toLowerCase();

                var matches = keywords.indexOf(query) !== -1 || 
                              question.indexOf(query) !== -1 || 
                              answer.indexOf(query) !== -1;

                if (matches) {
                    card.style.display = "block";
                    visibleCount++;
                } else {
                    card.style.display = "none";
                }
            }

            for (j = 0; j < faqs.length; j++) {
                var faq = faqs[j];
                var faqKeywords = faq.getAttribute("data-keywords") || "";
                var faqQuestion = faq.querySelector(".faq-question h4").textContent.toLowerCase();
                var faqAnswer = faq.querySelector(".faq-answer").textContent.toLowerCase();

                var faqMatches = faqKeywords.indexOf(query) !== -1 || 
                                 faqQuestion.indexOf(query) !== -1 || 
                                 faqAnswer.indexOf(query) !== -1;

                if (faqMatches) {
                    faq.style.display = "block";
                    visibleCount++;
                } else {
                    faq.style.display = "none";
                }
            }

            if (visibleCount === 0) {
                noResults.style.display = "block";
            } else {
                noResults.style.display = "none";
            }
        });
    }
});
</script>
