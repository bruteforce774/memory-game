# Memory game

- Hvilke komponenter ser dere? For hver komponent:
    - Hvilke data inn (props)
    - Hvilke data ut (emit)
    - Hvilke tilstand i komponenten

- Hvilken tilstand i appen

- Hvordan er hierarkiet - hvilken komponenter inni hvilke komponenter?


Komponenter:
- GameControls
  - emits
    - restarted
- GameBoard
  - tilstand
    - liste over bildene: objekt med bilde + isOpen
      🎈🍎⭐🧩🐶🎈🚗⭐🧩🍎🐶🚗
    - poeng
    - player turn
  - computed property
    - isFinished (=sjekke om alle er åpne)
  - lytter på emits
    - restarted => generere nytt tilfeldig brett + lukke alle rutene + poeng = 0
    - opened => logikk: 
      - to forskjellige åpnet => lukkes
      - to like => forblir åpnet + oppdatere poeng
- Card
  - props
    - bilde
    - isOpen : bool
  - emits
    - opened
- ScorePanel
  - props
    - score1 og score2




