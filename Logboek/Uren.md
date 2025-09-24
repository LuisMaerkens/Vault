
| Dag            | Aantal uur    |
| -------------- | ------------- |
| **01-09-2025** | **8 uur**     |
| **02-09-2025** | **8 uur**     |
| **03-09-2025** | **8, uur**    |
| **04-09-2025** | **8 uur**     |
| **05-09-2025** | **3 uur**     |
| **08-09-2025** | **8 uur**     |
| **09-09-2025** | **8 uur**     |
| **10-09-2025** | **8 uur**     |
| **11-09-2025** | **8 uur**<br> |
| **12-09-2025** | **3 uur**     |
| **15-09-2025** | **8 uur**<br> |
| **16-09-2025** | **8 uur**<br> |
| **17-09-2025** | **8 uur**<br> |
| **18-09-2025** | **8 uur**<br> |
| **19-09-2025** | **3 uur**     |
| **22-09-2025** | **8 uur**     |
| **23-09-2025** | **8 uur**     |
| **24-09-2025** | **8 uur**     |

[[Logboek]]


```
// Zoek de eerste tabel in het huidige bestand
let table = dv.current().file.sections.find(s => s.type === 'table');
// Tel alle waarden in de eerste kolom op
let sum = table.rows.reduce((a, row) => a + Number(row.cells[0]), 0);
dv.paragraph("Totaal kolom A: **" + sum + "**");
```
