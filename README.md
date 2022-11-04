# League of Troll

```javascript
// code to create a json from dragon data
(async () => {
	const championsResponse = await fetch(
		"http://ddragon.leagueoflegends.com/cdn/12.21.1/data/en_US/champion.json"
	);
	const championsData = (await championsResponse.json()).data;
	const champions = [];
	const printjson = [];

	for (const champion in championsData) {
		champions.push(champion);
		const championResponse = await fetch(
			`http://ddragon.leagueoflegends.com/cdn/12.21.1/data/en_US/champion/${champion}.json`
		);
		const championData = await championResponse.json();
		printjson.push({
			name: championData.data[champion].name,
			title: championData.data[champion].title,
			tags: championData.data[champion].stats,
			splash: `http://ddragon.leagueoflegends.com/cdn/img/champion/splash/${champion}_0.jpg`
		});
	}

	console.log(JSON.stringify(printjson));
})();
```
