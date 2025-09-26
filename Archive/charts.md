```dataviewjs
(async () => {
    const pages = dv.pages();
    const data = [];

    for (const p of pages) {
        const content = await dv.io.load(p.file.path);
        const wordCount = (content.match(/\b\w+\b/g) || []).length;
        data.push({ name: p.file.name, words: wordCount });
    }

    const top = data.sort((a, b) => b.words - a.words).slice(0, 30);

    // maak een canvas element
    const canvas = this.container.createEl("canvas");

    // teken de chart met Chart.js
    new Chart(canvas.getContext("2d"), {
        type: "bar",
        data: {
            labels: top.map(d => d.name),
            datasets: [{
                label: "Word count",
                data: top.map(d => d.words),
                backgroundColor: "rgba(239, 136, 98, 0.7)" // mooi kleurtje
            }]
        },
        options: {
            indexAxis: "y", // horizontale bars (handiger met lange namen)
            plugins: {
                legend: { display: false }
            }
        }
    });
})();
```


```mermaid
flowchart TB
    Gemeentesecretaris["Gemeentesecretaris (Algemeen Directeur)"]
    Gemeenteraad["Gemeenteraad"]
    B&W["College van B&W"]
    Directieteam["Directieteam"]

    %% Domeinen
    SociaalDomein["Sociaal Domein"]
    FysiekDomein["Fysiek Domein"]
    Veiligheidsdomein["Veiligheidsdomein"]
    SSC["Shared Service Centrum (SSC)"]
    PubliekeDienstverlening["Publieke Dienstverlening"]
    SDF["Sociaal Domein Fryslân (SDF)"]
    Concern["Concern"]

    %% Structuur
    Gemeentesecretaris -->|Leiding| Directieteam
    Directieteam -->|Bestuurlijke afstemming| B&W
    B&W -->|Beleid en uitvoering| Gemeentesecretaris
    Gemeentesecretaris --> SociaalDomein
    Gemeentesecretaris --> FysiekDomein
    Gemeentesecretaris --> Veiligheidsdomein
    Gemeentesecretaris --> SSC
    Gemeentesecretaris --> PubliekeDienstverlening
    Gemeentesecretaris --> SDF
    Gemeentesecretaris --> Concern

    %% Domeinstructuur
    SociaalDomein -->|Beleid en uitvoering| SociaalDomein
    FysiekDomein -->|Beleid en uitvoering| FysiekDomein
    Veiligheidsdomein -->|Beleid en uitvoering| Veiligheidsdomein
    SSC -->|Ondersteuning| SSC
    PubliekeDienstverlening -->|Dienstverlening| PubliekeDienstverlening
    SDF -->|Regionale samenwerking| SDF
    Concern -->|Ondersteuning| Concern

```



