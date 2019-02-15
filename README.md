### x-ray
---
https://github.com/matthewmueller/x-ray

```js
var Xray = require('x-ray');
var x = Xray();

x('https://blog.ycombinator.com/', '.post', [{
  title: 'h1 a',
  link: '.article-title@href'
}])
  .paginate('.nav-previous a@href')
  .limit(3)
  .write('result.json')

xray('http://google.com', 'title')(function(err, title) {
  console.log(title)
})

xray('http://reddit.com', '.content')(fn)

xray('http://techcrunch.com', 'img.logo@src')(fn)

xray('http://news.ycombinator.com', 'body@html')(fn)

var html = "<body><h2>Pear</h2></body>";
x(html, 'body', 'h2')(function(err, header) {
  header
})

var app = require('express')();
var x = require('x-ray')();

app.get('/', function(req, res) {
  var stream = x('http://google.com', 'title').stream();
  stream.pipe(res);
})

x()
  .paginate('.next_page@href')
  .limit(3)
  .then(function (res) {
    console.log(res[0])
  })
  .catch(function (err) {
    console.log(err)
  })
  
var Xray = require('x-ray');
var x = Xray();

x('http://google.com', {
  main: 'title',
  image: x('#gbar a@href', 'title'),
})(function(err, obj) {
  /*
  {
    main: 'Google',
    image: 'Google Images'
  }
  */
})

var Xray = require('x-ray');
var x = Xray();

x('http://mat.io', {
  title: 'title',
  items: x('.items', [{
    title: '.item-content h2',
    description: '.item-content secrion'
  }])
})(function(err, obj) {
  /*
  {
    title: 'mat.io',
    items: [
      {
        title: 'The 100 Best Children\'s Books of All Time',
        description: 'Relive your childhood with TIME\'s list...'
      }
    ]
  }
  */
})

var Xray = require('x-ray');
var x = Xray({
  filters: {
    trim: function (value) {
      return typeof value === 'string' ? value.trim() : value
    },
    reverse: function (value) {
      return typeof value === 'string' ? value.split('').reverse().join('') : value
    },
    slice: function (value, start, end) {
      return typeof value === 'string' ? value.slice(start, end) : value
    }
  },
});

x('http://mat.io', {
  title: 'title | trim | reverse | slice:2,3'
})(function(err, obj) {
  /*
  {
    title: 'oi'
  }
  */
})

```

```
npm install x-ray
```

```
```


