# js-regex
Javascript regex

## Svenska datum
Matchar datum i den svenska kalendern i formatet `YYYY-MM-DD`, från år 0000-01-01 till år 9999-12-31.

Möstret matchar borttagandet av dagarna 18-28 februari år 1753 samt tar höjd för skottdagar:
* både i Julianska och Greorianska kalendern
* det första försöket till kalenderbyte (stöket med skottdagar) år 1700-1708
* tillökningsdagen (för att komma till rätta med stöket) år 1712

```javascript
((?!1753\-02\-(1[89]|2[0-8]))[0-9]{4}\-(02\-(0[1-9]|1[0-9]|2[0-8])|(0[13578]|1[02])\-(0[1-9]|[12][0-9]|3[01])|(0[469]|11)\-(0[1-9]|[12][0-9]|30)))|(1712\-02\-30|((([2468][048]|[3579][26])00|[0-9]{2}(0[48]|[13579][26]|[2468][048])|(0[1-9]|1[0-6])00)\-02\-29))
```
