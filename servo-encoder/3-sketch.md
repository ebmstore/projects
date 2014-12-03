---
title: Analisi dello sketch

---

### Reimparare a gestire l'encoder

Visto che Timer1 e Servo utilizzano lo stesso timer e quindi vanno in conflitto, in questo sketch utilizzeremo una nuova libreria per gestire l'encoder.
Scaricabile da qui, Encoder può gestire un encoder collegato ai pin di interrupt di arduino.

| Option                          | Description                               |
|---------------------------------|-------------------------------------------|
| `octopress init <PATH>`         |  Adds Octopress scaffolding to your site  |
| `octopress new post <TITLE>`    |  Add a new post to your site              |
| `octopress new page <PATH>`     |  Add a new page to your site              |
| `octopress new draft <TITLE>`   |  Add a new draft post to your site        |
| `octopress publish <PATH>`      |  Publish a draft from _drafts to _posts   |
| `octopress new <PATH>`          |  works just like `jekyll new`             |
| `octopress build`               |  works just like `jekyll build`           |
| `octopress serve`               |  works just like `jekyll serve`           |
| `octopress doctor`              |  works just like `jekyll doctor`          |
