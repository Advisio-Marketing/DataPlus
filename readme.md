## Technická Specifikace pro `automatic_event`

### Parametr `automatic_event`

Objekt `index_conversion.automatic_event` obsahuje informace o událostech, které se automaticky zapisují. Tento dokument specifikuje strukturu objektu pro událost "purchase".

#### Struktura pro událost "purchase"

```json
{
    "name": "purchase",
    "currency": "CZK",
    "transaction_id": "12345",
    "version": "shoptet",
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
}
