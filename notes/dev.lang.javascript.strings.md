---
id: tjp3kswzndv23sven8z0elg
title: 문자열 다루기
desc: ''
updated: 1696550575941
created: 1696549810430
---

##
```javascript
function convertToFillInTheBlank(sentence) {
    const regex = /{{([^}]+)}}/g;
    const matches = sentence.match(regex);

    if (!matches) {
        return sentence;
    }

    const components = sentence.split(regex).map((item, index) => {
        if (matches.includes(`{{${item}}}`)) {
            return `<span>key={${index}} solution={${item}}</span>`;
        }
        return item;
    });

    return components.toString();
}

const data = '(Genesis 1:1) In the beginning God created the {{heavens}} and the {{earth}}.'


const lineComponents = line.split(regex).map((item, index) => {
    if (matches.includes(`{{${item}}}`)) {
    return <Blank key={index} solution={item} />;
    }
    return item;
});
```