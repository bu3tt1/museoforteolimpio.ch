---
title: Modulo di contatto
form:
    name: contact-form
    fields:
        - name: name
          label: Nome
          type: text
          validate:
            required: true
        - name: surname
          label: Cognome
          type: text
          validate:
            required: true
        - name: email
          label: E-mail
          type: email
          validate:
            required: true
        - name: phone
          label: Telefono
          type: text
        - name: group
          label: Tipo di gruppo
          type: select
          options:
            scuola: Scuola
            associazione: Associazione
            gruppo_privato: Gruppo privato
          validate:
            required: true
        - name: number_adult
          label: Numero di partecipanti adulti
          type: number
        - name: number_kid
          label: Numero di partecipanti ragazzi (8-16 anni)
          type: number
        - name: visit
          label: Tipo di visita
          type: select
          options:
            solo_museo: Solo museo
            museo_e_forte_sottoroccia_quartino: Museo e Forte sottoroccia Quartino 
          validate:
            required: true
        - name: date
          label: Data desiderata
          type: date
          validate:
            required: true
        - name: hour
          label: Ora desiderata
          type: time
          validate:
            required: true
        - name: other
          label: Altre informazioni
          type: textarea
    buttons:
        - type: submit
          value: Invia richiesta

    process:
        - email:
            from: "{{ config.plugins.email.from }}"
            to: "{{ config.plugins.email.to }}"
            subject: "Modulo di contatto museoforteolimpio.ch"
            body: "{% include 'forms/data.html.twig' %}"
        - save:
            fileprefix: feedback-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        - message: Grazie per la sua richiesta!
        - reset: true

---