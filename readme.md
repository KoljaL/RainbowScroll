Simple and fun idea:

**The color of the headings (or whatever) changes depending on how far the page was scrolled down.**

This function gives us the percentage value:
```js
function getScrollPercent() {
    var h = document.documentElement,
        b = document.body,
        st = 'scrollTop',
        sh = 'scrollHeight';
    return (h[st] || b[st]) / ((h[sh] || b[sh]) - h.clientHeight) * 100;
}
```

> We have to multiply that by 3.6 so that we have the HSL circle complete.

Then just an event listener:
```JS
var r = document.querySelector(':root'); 

document.addEventListener('scroll', (e) => {
    let percent = getScrollPercent();
    let hsl = Math.round(percent * 3.6); 
    r.style.setProperty('--rainbowColor', 'hsl(' + hsl + ', 70%, 50%)');
})
```

And the corresponding CSS:
```CSS
:root {
    --rainbowColor: hsl(0, 100%, 50%);
}

h1,h2,strong {
    color: var(--rainbowColor);
}
```

[Try it out](https://koljal.github.io/RainbowScroll/)   
[Repo](https://github.com/KoljaL/RainbowScroll/)