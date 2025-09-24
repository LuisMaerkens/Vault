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


