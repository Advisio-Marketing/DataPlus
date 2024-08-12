## Technická Specifikace pro `automatic_event`

### Parametr `automatic_event`

Objekt `index_conversion.automatic_event` obsahuje informace o událostech, které se automaticky zapisují. Tento dokument specifikuje strukturu objektu pro událost "purchase".

```javascript
window.index_conversion = window.index_conversion || {};
window.index_conversion.automatic_event = window.index_conversion.automatic_event || [];
```

#### Struktura pro událost "purchase"


```javascript
window.index_conversion.automatic_event.push({
    "name": "purchase",
    "currency": "CZK",
    "transaction_id": "12345",
    "value": "1000.00",
    "tax": "210.00",
    "shipping": "100.00",
    "items": [
        {
            "id": "sku123",
            "nm": "Product Name",
            "pr": "250.00",
            "qt": "4",
            "ca": "Category1",
            "c2": "Category2",
            "br": "BrandName"
        }
    ]
});
```

## Popis Polí

### Hlavní Pole
- `name` (string): Název události, v tomto případě "purchase".
- `currency` (string): Měna transakce. Očekávané hodnoty jsou ve formátu ISO 4217 (např. "USD", "EUR", "CZK").
- `transaction_id` (string): ID transakce.
- `value` (string): Celková hodnota transakce.
- `shipping` (string): Celková hodnota dopravy.
- `tax` (string): Celková hodnota daně.
- `items` (array): Pole objektů obsahující informace o produktech.

### Pole v items
- `id` (string): ID produktu (SKU) ID produktu musí být shodná s ID v XML feedu.
- `nm` (string): Název produktu.
- `pr` (string): Cena produktu.
- `qt` (string): Množství produktu.
- `ca`, `c2`, ... (string): Kategorie produktu (dynamicky přidávané; `ca` je první kategorie, `c2` je druhá kategorie, atd.).
- `br` (string): Značka produktu.

### Dostupné další eventy [nepovinné]
- `view_item_list` (string): Zobrazení produktů v kategorii.
- `add_to_cart` (string): Přidání produktu do nákupního košíku.
- `begin_checkout` (string): Zahájení procesu platby.
- `purchase` (string): Dokončení nákupu.
- `view_item` (string): Zobrazení jednoho produktu.

#### Struktura pro událost dalších eventů

```javascript
window.index_conversion.automatic_event.push({
    "name": "view_item",
    "currency": "CZK",
    "value": "1000.00",
    "items": [
        {
            "id": "sku123",
            "nm": "Product Name",
            "pr": "250.00",
            "qt": "4",
            "ca": "Category1",
            "c2": "Category2",
            "br": "BrandName"
        }
    ]
});
```

## Pro přidání informací o uživateli [nepovinné]

Tato část popisuje, jak přidat `user_data` do objektu `window.index_conversion`. Inicializujte objekt `user_data` s výchozím typem uživatele "b2c".

```javascript
window.index_conversion.user_data = {
    user_type: "b2c",
};
```

### Hlavní Pole
- `user_data` (array): Pole objektů klíčových vlastností uživatelů.
- `user_type` (string): Typ uživatele. Může nabývat hodnot "b2c" (business to consumer) nebo "b2b" (business to business).

## Implementace javascriptové knihovny
Načtení knihovny po nastavení dat do "automatic_event", ideálně na konec </body> na všechny stránky
```javascript
<script type="text/javascript" src="https://apps.[doména].cz/"></script>
```
