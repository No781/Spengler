---
title: Kontakt
menu: Kontakt
shown_in_footer: true
background_image: img-page-title.jpg
content:
    items: '@self.modular'
    order:
        by: default
        dir: asc
        custom:
            - _contact
            - _map
form:
    action: /contact
    name: contact-form
    fields:
        -
            name: name
            label: Name
            placeholder: Name
            type: text
            validate:
                required: true
            classes: form-control
        -
            name: email
            label: Email
            placeholder: 'Email Address'
            type: email
            validate:
                required: true
            classes: form-control
        -
            name: phone
            label: Telefon
            placeholder: Telefon
            type: text
            validate:
                required: true
            classes: form-control
        -
            name: message
            label: Nachricht
            placeholder: 'Schreiben Sie uns eine Nachricht'
            type: textarea
            rows: 6
            validate:
                required: true
            classes: form-control
    buttons:
        -
            type: submit
            value: Senden
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.from }}']
                subject: '[Kontakt Metall] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: contact-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            display: 'Danke vielmals'
---

