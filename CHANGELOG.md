# Changelog

Tutte le modifiche rilevanti a questo modulo sono documentate in questo file.

Il formato è basato su [Keep a Changelog](https://keepachangelog.com/it/1.1.0/)
e questo progetto aderisce al [Semantic Versioning](https://semver.org/lang/it/).

## [1.0.0] - 2026-11-05

### Added
- Feed XML (RSS 2.0 con namespace `g:`) per **Google Merchant Center** e per il **catalogo Meta** (Facebook e Instagram),
  un file per profilo, negozio e lingua, in `modules/tcproductfeed/feeds/`.
- URL con token non indovinabile, derivato dalla chiave dei cookie del negozio (stabile nel tempo).
- Generazione da cron (URL con token, da chiamare ogni ora: rigenera i file più vecchi di N ore), da riga di comando
  (`php modules/tcproductfeed/cli.php [--shop=] [--profile=google|meta] [--force]`) e dal pulsante *Genera ora*;
  il file viene scritto su un temporaneo e rinominato a fine lavoro.
- Prezzi IVA inclusa come in negozio, per il gruppo dei visitatori (sconti specifici, date e regole catalogo già applicati):
  `price` + `sale_price` quando c'è uno sconto. Con combinazioni vale quella col prezzo più basso (un solo articolo).
- Filtri: tipi di prodotto (standard, virtuali, pack), categorie, esclusione per campo o caratteristica
  (es. `available_for_order = 0` per i prodotti "prossimamente"), prodotti esauriti.
- Dati: marca (produttore), GTIN (EAN-13, ISBN o UPC), MPN (o riferimento), categoria Google, immagini aggiuntive,
  `product_type` dal percorso categoria, `identifier_exists = no` per Google quando mancano GTIN e MPN.
- Esclusi: prezzo 0 e prodotti senza immagine.
- Configurazione in *Moduli → Product feed per Google e Meta*, con gli URL dei feed, lo stato e il pulsante *Genera ora*.
- Traduzione italiana.
