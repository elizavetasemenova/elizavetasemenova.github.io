---
layout: post
title: "Obfuscate email with CSS."
date: 2016-12-02
comments: true
---
While creating this site, I wanted to add my e-mail explicitly to the list of contacts but not become a spam bot victim. Search results 
offered such solutions as HTML-encoding or JavaScript obfuscation. I opted for the CSS workaround since found it the most elegant: 
it changes text direction right to left. The trick works with the following code:


```CSS
span.reverse {
  unicode-bidi: bidi-override;
  direction: rtl;
}
```

<pre class="prettyprint">
span.reverse {
  unicode-bidi: bidi-override;
  direction: rtl;
}
</pre>


Now apply it to any text on your page to make it written right to

```javascript
 <span class="reverse">tfel.</span>
```

This will not work unfortunately work for right to left scrips such as hebrew. Otherwise happy obfuscating!
