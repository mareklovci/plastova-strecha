---
title: 'Vzorek zdarma'
published: true
visible: true
form:
    name: vzorek-zdarma
    fields:
        -
            name: firstname
            label: Jméno
            placeholder: 'Zadejte prosím svoje křestní jméno'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: lastname
            label: Příjmení
            placeholder: 'Zadejte svoje příjmení'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: address
            label: 'Ulice a č.p.'
            placeholder: 'Ulice a číslo popisné'
            type: text
            validate:
                required: true
        -
            name: town
            label: Město
            placeholder: Město
            type: text
            validate:
                required: true
        -
            name: post
            label: PSČ
            placeholder: 'Poštovní směrovací číslo'
            type: text
            validate:
                required: true
        -
            name: email
            label: Email
            placeholder: 'Napište nám svoji emailovou adresu'
            type: email
            validate:
                required: true
        -
            name: phone
            label: Telefon
            placeholder: 'Můžete nám zanechat i telefonní číslo'
            type: text
            validate:
                required: false
    buttons:
        -
            type: submit
            value: Odeslat
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.to }}', '{{ form.value.email }}', '{{ config.plugins.email.from }}']
                subject: '[Vzorek zdarma] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: vzorek-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            message: 'Děkujeme za Váš zájem. Již brzy očekávejte vzorek naší střechy'
---

# Vzorek zdarma

Děkujeme, že jste se rozhodli vyzkoušet Tachovskou břidlu.
Věříme, že budete plně spokojeni. Nyní prosím vyplňte alespoň údaje označené hvězdičkou.