# Combina! — joc d'operacions combinades

Fitxer únic (`index.html`, 54 kB), sense build ni dependències de npm.

## Decisions de disseny

**Aritmètica exacta amb BigInt.** Tot el càlcul i la validació treballen amb fraccions racionals exactes; no hi ha cap coma flotant. La resposta de l'usuari es compara amb producte creuat (n₁·d₂ = n₂·d₁) i després es comprova la irreductibilitat: −14/24 es rebutja amb la pista de simplificar.

**Entrada adaptativa.** Fins al nivell 4 no hi ha fraccions, així que només apareix un camp; la barra i el denominador surten al nivell 5, quan tenen sentit. El botó de signe només apareix on hi pot haver resultats negatius (nivells 3–4 i 7–10).

**Escriptura escolar.** Mai dos signes seguits: tot negatiu darrere d'un operador va entre parèntesis, i la imbricació segueix ( ) → [ ] → { } comptant també els parèntesis de signe, com als llibres de text. Divisió amb «:», producte amb «·», fraccions amb \dfrac de KaTeX.

**Mode «caça l'error».** L'error injectat és sempre una concepció errònia real (signe en treure parèntesis, sumar denominadors, invertir la fracció equivocada, −a² vs (−a)², signes del producte); l'error de càlcul pur queda com a últim recurs. A partir de la línia errònia, el desenvolupament continua coherent amb l'error: cal trobar la primera línia dolenta, no «la que no quadra». Els errors que es cancel·len es descarten perquè serien indetectables.

**Degradació.** Si KaTeX no carrega, un renderitzador HTML/CSS dibuixa les mateixes fraccions. Si localStorage està bloquejat (iframe de tercers), el progrés passa a memòria i el joc segueix.

## Publicació i incrustació

1. Puja `index.html` a un repositori de GitHub.
2. Settings ▸ Pages ▸ Deploy from a branch ▸ `main`, `/root`.
3. Incrusta amb:

```html
<iframe src="https://ELTEUUSUARI.github.io/ELREPOSITORI/"
        width="100%" height="780" style="border:0;max-width:920px"
        title="Combina! Joc d'operacions combinades" loading="lazy"></iframe>
```

Alçada mínima recomanada: 700 px.

## Limitacions conegudes

Les expressions generades per procediment poden semblar de tant en tant poc «de llibre» (p. ex. multiplicar per 1). Les potències del mode B només s'injecten com a error de signe. La primera càrrega necessita internet per a KaTeX i les tipografies; després el navegador les té en memòria cau.
