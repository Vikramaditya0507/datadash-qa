const { chromium } = require('playwright');

(async () => {
  const browser = await chromium.launch();
  const page = await browser.newPage();
  let total = 0;

  for (let seed = 72; seed <= 81; seed++) {
    const url = `https://sanand0.github.io/tdsdata/js_table/?seed=${seed}`;
    await page.goto(url, { waitUntil: 'networkidle' });
    const numbers = await page.$$eval('td', cells =>
      cells.map(c => parseFloat(c.innerText)).filter(n => !isNaN(n))
    );
    const seedSum = numbers.reduce((a, b) => a + b, 0);
    console.log(`Seed ${seed}: sum = ${seedSum}`);
    total += seedSum;
  }

  console.log(`TOTAL SUM: ${Math.round(total)}`);
  await browser.close();
})();
