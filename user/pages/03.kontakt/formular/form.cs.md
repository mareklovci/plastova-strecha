---
title: 'Kontaktní formulář'
metadata:
    description: 'Pošlete nám zprávu nebo na sebe zanechte kontakt. Ozveme se vám.'
form:
    name: kontaktni-formular
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
            name: email
            label: Email
            placeholder: 'Napište nám svoji emailovou adresu'
            type: email
            validate:
                required: true
        -
            name: message
            label: Zpráva
            placeholder: 'Zanechte nám vzkaz'
            type: textarea
            validate:
                required: true
    buttons:
        -
            type: submit
            value: Odeslat
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.from }}', '{{ config.plugins.email.to }}', '{{ form.value.email }}']
                subject: '[Kontaktní formulář] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: contact-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            message: 'Děkujeme za Vaši zprávu!'
---

# Kontaktní formulář