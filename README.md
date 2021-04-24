
#### Struct

É uma tabela separada e pré-mesclada na sua tabela principal.

Um STRUCT pode ter:

- um ou mais campos;
- tipos de dados iguais ou diferentes para cada campo;
- um alias próprio

##### Example

```sql
# Array
SELECT ["current", "previous", "birth"] AS address_history;

SELECT STRUCT("Rudisha" as name, [23.4, 26.3, 26.4, 26.1] as splits) AS runner;

SELECT 
[
    STRUCT("current" AS status,"London" AS address, "ABC123D" AS postcode),
    STRUCT("previous" AS status,"New Delhi" AS address, "738497" AS postcode),
    STRUCT("birth" AS status,"New York" AS address, "SHI747H" AS postcode)
] AS address_history;

SELECT 
    "Chaco Bar" AS name, 
    "Potts Point" AS location,
    STRUCT(
        ["Japanese", "Yakitori", "Casual"] AS cuisine_array, 
        "$$" AS price_range, 
        False AS has_delivery
    ) AS basic_info;

```

#### Partition

```sql
CREATE OR REPLACE TABLE project.user
PARTITION BY date_formatted
OPTIONS (
 descritpion="a table partitioned by date"
) AS
SELECT DISTINCT
 full_name,
 last_name,
 date_formatted,
 FROM `project.dataset.user`
```