

### Examples

```js
R.map(([k, v]) => global[k] = v, R.toPairs(R));
```


### ramda_intro.js
```js
  const R = require('ramda')
  const fs = require('fs')
  
  const readFileSync = path => fs.readFileSync(path, { encoding: 'utf-8' })
  
  const readData = R.pipe(
    R.converge(R.concat, [
      R.pipe(  
        R.replace(/.*\//, ''),
        R.replace(/\..*/, ''),
        R.concat('date\t'),
        R.concat(R.__, '\n')
      ),
      readFileSync
    ])
  )
  
  R.pipe(
    R.map(R.pipe(
      readData,
      R.split('\n'),
      R.map(R.pipe(
        R.split('\t'),
        R.view(R.lensIndex(1))
      )),
      R.converge(R.map, [
        R.pipe(R.head, R.objOf),
        R.tail
      ])
    )),
    R.transpose,
    R.map(R.mergeAll),
    console.log
  )(['./btc.csv', './eth.csv'])
  
  
  R.pipe(
    R.map(R.pipe(
      readData,
      R.split('\n'),
      R.map(R.pipe(
        R.split('\t'),
        R.take(2),
      )),
    )),
    R.transpose,
    R.map(R.pipe(
      R.flatten,
      R.uniq,
      R.map(R.ifElse(isNumeric, toNumber, R.identity)),
      R.map(R.ifElse(R.head, R.toUpper, R.identity))
    )),
    console.log
  )(['./btc.csv', './eth.csv'])
```

### ramda_lesson01.js
```js
  const R = require('ramda');
  R.map(([k, v]) => global[k] = v, R.toPairs(R));
  
  const permissions = {
    'group1-perm1': true,
    'group1-perm2': false,
    'group2-perm1': false,
    'group2-perm2': true,
    'perm3': true,
    'perm4': false
  };
  
  // {
  //   group1: [
  //     { value: 'group1-perm1', checked: true, 'label': 'perm1' }]
  //   ]
  // }
  
  const GROUP_LEN = 6;
  const KEYS = ['value', 'checked', 'label'];
  const inGroup = str => str.indexOf('-') === GROUP_LEN;
  const getLabel = compose(last, splitAt(GROUP_LEN + 1));
  const addLabel = chain(append, compose(ifElse(inGroup, getLabel, identity), head));
  const convert = compose(zipObj(KEYS), addLabel);
  
  const groupName = ifElse(compose(inGroup, prop('value')),
    compose(head, splitAt(GROUP_LEN), prop('value')),
    () => 'general'
  );
  
  const fn = compose(groupBy(groupName), map(convert), toPairs);
  
  console.log(fn(permissions));
```

### ramda_lesson04.js
```js
  const R = require('ramda');
  
  const perms = { 
    "group1": [ 
      { "value": "group1-perm1", "checked": true, "label": "perm1" },
      { "value": "group1-perm2", "checked": false, "label": "perm2" }
    ],
    "group2": [ 
      { "value": "group2-perm1", "checked": false, "label": "perm1" },
      { "value": "group2-perm2", "checked": true, "label": "perm2" } 
    ],
    "general": [ 
      { "value": "perm3", "checked": true, "label": "perm3" },
      { "value": "perm4", "checked": false, "label": "perm4" },
      { "value": "perm5", "checked": true, "label": "perm5" } 
    ] 
  };
  
  const fn = R.compose(
    R.mergeAll,
    R.map(p => ({ [p.value]: p.checked })),
    R.flatten, 
    R.map(R.nth(1)), 
    R.toPairs);
  
  console.log(JSON.stringify(fn(perms)));
```

```
- BTCETH
  "[ [ 'DATE', 'BTC', 'ETH' ],
    [ 'JUL 26, 2018', 8176.85, 472.33 ],
    [ 'JUL 25, 2018', 8379.66, 479.91 ],
    [ 'JUL 24, 2018', 7716.51, 451.14 ],
    [ 'JUL 23, 2018', 7414.71, 459.44 ],
    [ 'JUL 22, 2018', 7417.8, 462.44 ],
    [ 'JUL 21, 2018', 7352.72, 450.68 ],
    [ 'JUL 20, 2018', 7467.4, 469.31 ],
    [ 'JUL 19, 2018', 7378.2, 480.63 ],
    [ 'JUL 18, 2018', 7315.32, 500.84 ],
    [ 'JUL 17, 2018', 6739.65, 480.08 ],
    [ 'JUL 16, 2018', 6357.01, 450.43 ],
    [ 'JUL 15, 2018', 6272.7, 435.88 ],
    [ 'JUL 14, 2018', 6247.5, 434.51 ],
    [ 'JUL 13, 2018', 6235.03, 430.74 ],
    [ 'JUL 12, 2018', 6396.78, 446.5 ],
    [ 'JUL 11, 2018', 6330.77, 434.52 ],
    [ 'JUL 10, 2018', 6739.21, 476.16 ],
    [ 'JUL 09, 2018', 6775.08, 488.88 ],
    [ 'JUL 08, 2018', 6857.8, 492.07 ],
    [ 'JUL 07, 2018', 6668.71, 474.06 ],
    [ 'JUL 06, 2018', 6638.69, 474.36 ],
    [ 'JUL 05, 2018', 6599.71, 467.29 ],
    [ 'JUL 04, 2018', 6550.87, 464.15 ],
    [ 'JUL 03, 2018', 6596.66, 475.39 ],
    [ 'JUL 02, 2018', 6380.38, 453.82 ],
    [ 'JUL 01, 2018', 6411.68, 455.24 ],
    [ 'JUN 30, 2018', 6214.22, 436.21 ],
    [ 'JUN 29, 2018', 5898.13, 422.59 ],
    [ 'JUN 28, 2018', 6153.16, 442.29 ],
    [ 'JUN 27, 2018', 6084.4, 432.24 ] ]"
```

### countBy
```js
  const fn = R.compose(
    R.map(R.compose(R.flatten, R.over(R.lensIndex(0), R.split(',')))),
    R.toPairs,
    R.countBy(R.identity)
  )
  console.log(fn(data))
  
  const data = [
    ["0722", "ID_1"],
    ["0722", "ID_3"],
    ["0722", "ID_1"],
    ["0723", "ID_3"],
    ["0723", "ID_2"],
    ["0724", "ID_1"],
    ["0724", "ID_3"],
    ["0724", "ID_2"],
    ["0724", "ID_1"],
    ["0724", "ID_3"]
  ]
```

### Ramda Tutorial
  - "https://github.com/knowthen/ramdatutorial"
