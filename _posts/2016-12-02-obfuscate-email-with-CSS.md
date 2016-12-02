---
layout: post
title: "Obfuscate email with CSS."
date: 2016-12-02
comments: true
---
While creating this site, I wanted to add my e-mail explicitly to the list of contacts but not become a spam bot victim. Search results 
offered such solutions as HTML-encoding or JavaScript obfuscation. I opted for the CSS workaround since found it the most elegant: 
it changes text direction right to left. The trick works with the following code in the CSS file

```javascript
/* E-Mail */
span.reverse {
  unicode-bidi: bidi-override;
  direction: rtl;
}
```

and apply to any text text on your page
```HTML
 <span class="reverse">thgir ot tfel</span>
```
