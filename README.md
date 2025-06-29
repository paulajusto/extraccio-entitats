# Reconeixement d’Entitats Anomenades amb Conditional Random Fields

Aquest projecte implementa un sistema de reconeixement d’entitats anomenades (NER) per textos en espanyol i neerlandès mitjançant models de **Conditional Random Fields (CRF)**. També s’inclou una extensió opcional per a l’extracció d’entitats mèdiques en el corpus CADEC.

## Objectius

- Entrenar models de CRF amb conjunts de dades etiquetats en format BIO.
- Experimentar amb diverses combinacions de **feature functions** per millorar la precisió.
- Comparar diferents esquemes de codificació d’etiquetes (BIO, BIOW, BIOE, BIOEU, BIOE+, IO).
- Optimitzar hiperparàmetres de regularització (`c1`, `c2`) per maximitzar el rendiment.
- Avaluar el model amb mètriques detallades i analitzar els errors de classificació.

## Conjunt de Dades

S’han utilitzat els corpus **CoNLL-2002** per espanyol i neerlandès, formats per textos etiquetats amb entitats de tipus PER, LOC, ORG i MISC. Addicionalment, es pot aplicar el sistema sobre el corpus **CADEC**, especialitzat en entitats clíniques.

## Preprocessament

Abans de l’entrenament, s’ha aplicat un preprocessament uniforme:

1. Conversió dels conjunts d’entrenament i validació a diferents codificacions d’etiquetes.
2. Simplificació d’etiquetes en el corpus CADEC per agrupar entitats en categories generals.
3. Definició de funcions de característiques per capturar informació lèxica, morfològica i contextual.

## Model CRF i Features

El sistema permet:

- Configurar quines **feature functions** incloure (paraula, majúscules, dígits, sufixos, prefixos, longitud, context i POS).
- Utilitzar **gazetteers** específics per ajudar en la detecció d’entitats.
- Provar diferents estratègies de codificació (BIO, BIOW, etc.) per optimitzar la segmentació.

Els models s’han entrenat amb la llibreria **pycrfsuite** i inclouen una cerca automàtica de la millor combinació de features i hiperparàmetres.

## Avaluació i Anàlisi

L’avaluació es basa en:

- **Precisió, recall i F1** amb criteri estricte (coincidència exacta d’entitats) i parcial (coincidència parcial).
- Generació de matrius de confusió per analitzar les principals confusions entre etiquetes.
- Gràfics comparatius per visualitzar el rendiment segons la codificació i el conjunt d’hiperparàmetres.

## Resultats Obtinguts

Els models optimitzats aconsegueixen:

- **Espanyol**: F1 exacte superior al 84% i parcial pròxim al 94%.
- **Neerlandès**: F1 exacte superior al 86% i parcial pròxim al 95%.

En el corpus CADEC (opcional), la precisió és raonable, però amb un recall més limitat degut a la complexitat de les etiquetes clíniques.

## Llibreries i Eines

- Python 3
- nltk
- pycrfsuite
- unidecode
- seaborn
- matplotlib

## Llicència

Aquest projecte s’ha desenvolupat amb finalitats acadèmiques. Per a ús productiu o comercial, es recomana una revisió exhaustiva i una adaptació del model.
