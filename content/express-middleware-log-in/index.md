---
emoji: ๐ข
title: Express ๋ฏธ๋ค์จ์ด ์ ๋๋ก ์ฌ์ฉํ๊ธฐ + ๋ก๊ทธ์ธ ๊ตฌํํ๊ธฐ
date: '2020-07-12 20:00:00'
author: ์ค์ฝ๋ฉ
tags: javascript node express ์ฐ์ํํํฌ์บ ํ ๋ฐฑ์๋๊ฐ๋ฐ ๋ธ๋ ์ต์คํ๋ ์ค ๋ฏธ๋ค์จ์ด
categories: ์น๊ณต๋ถ
---

## ๐งฉ ๋ชฉ์ 

express์ ํน์ง์ ๋ํด์๋ [Node ๊ฐ๋ฐ์๋ผ๋ฉด ์์์ผ ํ  ๊ธฐ๋ณธ ์ง์ ํฌ์คํ](https://zoomkoding.github.io/node/2020/06/04/node-developer-basic.html)์ ํตํด ์ ๋ฆฌํ์ผ๋ ์ด๋ฒ์๋ express generator๋ก ์์ฑ๋๋ ์ฌ๋ฌ ๋ฏธ๋ค์จ์ด์ ๋ก๊ทธ์ธ ํ๋ก๊ทธ๋จ ๊ตฌํ์ ์ฌ์ฉ๋ ๋ฏธ๋ค์จ์ด๋ฅผ ์ ๋ฆฌํด๋ณด๋ ค๊ณ  ํ๋ค.

<br>

## ๐ฝ๏ธ ํ๋ก์ ํธ ๊นํ ๋ ํฌ์งํ ๋ฆฌ

[[์ฐ์ํํํฌ์บ ํ] ๋ฐฐ๋ฏผ์ํ ํ์๊ฐ์/๋ก๊ทธ์ธ ๊ตฌํ ํ๋ก์ ํธ](https://github.com/woowa-techcamp-2020/market-8)

<br>

## ๐ญ Express ์ฃผ์ ๋ฏธ๋ค์จ์ด

### [pug](https://pugjs.org/api/getting-started.html)

Express๋ ๋ฐํ์์ ํํ๋ฆฟ ์์ง์ ์ด์ฉํด์ ์ฌ๋ฌ ๋ณ์๊ฐ ์๋ staticํ ํํ๋ฆฟ ํ์ผ์ ์ค์  ๊ฐ์ ๋ฃ์ด html ํ์ผ์ ์์ฑํ๋ค.

Pug๋ ๊ฐ์ฅ ๋ํ์ ์ธ ํํ๋ฆฟ์์ง์ผ๋ก ํํ๋ฆฟ์ด ์๋ ๋๋ ํ ๋ฆฌ๋ฅผ views์ ์ ํด์ฃผ๊ณ  view engine์ผ๋ก pug๋ก ์ค์ ํด์ฃผ๋ฉด ์ฌ์ฉํ  ์ ์๋ค.

<br>

app.js์ view engine ์ข๋ฅ์ template directory๋ฅผ ์ ํด์ฃผ๊ณ 

```jsx
app.set('views', './views');
app.set('view engine', 'pug');
```

๋ค์๊ณผ ๊ฐ์ด **index.pug** ๋ฅผ ๋ง๋ค์ด ์ฃผ๊ณ  title์ ๋ํ ๋ณ์๊ฐ์ ์ ๋ฌ๋ฐ๋ template์ ์ค์ ํ๊ณ 

```jsx
extends layout

block content
  h1= title
  p Welcome to #{title}
```

**router.js** ์์ res.render ํจ์๋ฅผ ํตํด ์ฌ์ฉํ  template๊ณผ ๋ณ์ ๊ฐ์ ์ ๋ฌํด์ฃผ๋ฉด

```jsx
router.get('/', function (req, res, next) {
  res.render('index', { title: 'Express' });
});
```

template์ ๋ณ์ ๊ฐ์ ๋ฃ์ด์ ํด๋นํ๋ ํ์ด์ง๋ฅผ ์ ์ ์๊ฒ ์ ๋ฌ๋๋ค.

<br>

### [morgan](https://www.npmjs.com/package/morgan)

morgan์ ์ด๋ฆ์์ ๋ฐ๋ก ์ ์ ์์ง๋ง request๋ฅผ logging์ ํด์ฃผ๋ ์์ฃผ ์ ์ฉํ ๋ฏธ๋ค์จ์ด์ด๋ค.

```jsx
var logger = require('morgan');

// ยทยทยท

app.use(logger('dev');
```

<br>

morgan์ ์ฌ์ฉํ  ๋ parameter๋ก format ๊ฐ์ ๋ณด๋ด์ค ์ ์๋ค.(์ด ๋ฏธ๋ฆฌ ์ ํด์ง format์ tiny, common, short ๋ฑ ๋ค์ํ๋ค.)

dev format๋ request๋ฅผ ๋ค์๊ณผ ๊ฐ์ ํ์์ผ๋ก console์ ๊ธฐ๋กํด์ค๋ค.

```
:method :url :status :response-time ms - :res[content-length]
```

<br>

dev format์ ์ฌ์ฉํ์ ๋์ ๋ชจ์ต์ด๋ค.

![express-middleware-0](./express-middleware-1.png)

<br>

morgan์ ์ฌ์ฉํ๋ฉด ์๋ฌ๊ฐ ์ด๋ค ์์ฒญ์์ ๋ฐ์ํ๋์ง ํ์ธํ  ์ ์์ด์ ๋งค์ฐ ์ ์ฉํ๋ค. ๊ทผ๋ฐ ๋ง์ผ ์ค์  ์๋น์ค๋ฅผ ๋ฐฐํฌํ ์ํ์์ ์๋ฒ์ ์ํ๋ฅผ ์ฝ์๋ก๋ง ํ์ธํ๋ค๋ฉด ๋ก๊ทธ๋ฅผ ๋ชจ๋ ํ์ธํ๋๋ฐ ์ด๋ ค์์ด ์๋ค.

<br>

๐ฏ**๊ฟํ** ๐ฏ

**morgan์ console ๋์  file์ logging ํ๋๋ก ์ค์ ์ด ๊ฐ๋ฅํ๋ค.**

**rotating-file-stream์ด๋ผ๋ ๋ฏธ๋ค์จ์ด๋ฅผ ์ฌ์ฉํ๋ฉด ๋งค์ผ ๋ค๋ฅธ ํ์ผ์ ๋ก๊น์ ํ  ์ ์๋๋ก ์ค์ ํ  ์ ์๊ณ  ์ฌ์ง์ด๋ console์๋ ์๋ฌ ์์ฒญ๋ง ๊ธฐ๋กํ๋๋ก ํ๊ณ  ํ์ผ์๋ ๋ชจ๋  ์์ฒญ์ ๋ค ๊ธฐ๋กํ๋๋ก ์ค์ ํ  ์๋ ์๋ค.**

๋ค์์ ๊ทธ ์์์ด๋ค!

```jsx
var express = require('express');
var morgan = require('morgan');
var path = require('path');
var rfs = require('rotating-file-stream'); // version 2.x

var app = express();

// create a rotating write stream
var accessLogStream = rfs.createStream('access.log', {
  interval: '1d', // rotate daily
  path: path.join(__dirname, 'log'),
});

// log only 4xx and 5xx responses to console
app.use(
  morgan('dev', {
    skip: function (req, res) {
      return res.statusCode < 400;
    },
  }),
);

// log all requests to access.log
app.use(
  morgan('common', {
    stream: fs.createWriteStream(path.join(__dirname, 'access.log'), { flags: 'a' }),
  }),
);
// ยทยทยท
```

<br>

### [express-session](https://www.npmjs.com/package/express-session)

express-session์ ์๋ฒ๊ฐ ์ธ์์ ์ด์ฉํ๊ฒ ํด์ฃผ๊ณ  ์ ์  ์ฟ ํค์ ์ธ์ ์ ๋ณด๋ฅผ ๋ด์ ์ ์๊ฒ ํด์ฃผ๋ ๋งค์ฐ ์ ์ฉํ ๋ฏธ๋ค ์จ์ด์ด๋ค.

์ ์  ์ฟ ํค์ ์ธ์ ์ ๋ณด๋ฅผ ๋ด์ ๋๋ ์ธ์์ ๋ชจ๋  ์ ๋ณด๋ฅผ ๋ด๋ ๊ฒ์ด ์๋๋ผ **์ธ์์ ์์ด๋ ๊ฐ์ ์ ์ฅ**ํ๊ณ  ์๋ฒ์์ ๋ฐ์ดํฐ๋ฅผ ๊ด๋ฆฌํ๊ฒ ๋๋ค.

์ด๋ ์ฌ๋ฌ ์ต์์ ์ ํด์ค์ผ ํ๋๋ฐ ์ฃผ์ ์ต์์ ํน์ง์ ๋ค์๊ณผ ๊ฐ๋ค.

**secret** : session Id๋ฅผ hashํ๊ธฐ ์ํด ์ฌ์ฉ๋๋ key ๊ฐ์ด๋ค.(ํด์ฌํ ๊ฐ์ด connect.sid์ ์ ์ฅ๋๋ค.)

**resave** : ์ธ์์ ์ ์ํ  ๋๋ง๋ค ์๋ก์ด ์ธ์์ ๋ฐ๊ธํ ์ง ๋ง์ง ์ ํ๋ ๊ณณ์ด๋ค.(true ์ค์ ์ race condition์ ๋ฐ์ ์ํฌ ์ ์๋ค๊ณ  ํ๋ค. ๋๋ถ๋ถ์ ๊ฒฝ์ฐ false๊ฐ ์ ์ ํ๋ค๊ณ  ํ๋ค.)

**saveUninitialized** : ์ธ์ ID๋ฅผ ๋ฐ๊ธํ์ง ์๋ ์ธ์๋ ๋ค ๊ธฐ๋กํ ์ง ์ ํ๋ค.(๋ก๊ทธ์ธ์ ์ฌ์ฉํ  ๋๋ ์๋ฒ ๋ฉ๋ชจ๋ฆฌ ์ฌ์ฉ์ ์ค์ฌ์ฃผ๊ธฐ ์ํด false๋ก ์ค์ ํ๋ค.)

**storage** : ์ธ์์ ์ด๋์ ์ ์ฅํ ์ง ์ ํ๋ค.(๊ธฐ๋ณธ ๊ฐ์ MemoryStore๋ฅผ ์ฌ์ฉํ๊ธฐ ๋๋ฌธ์ production์ ์ฌ์ฉํ๋ฉด memory leak์ด ๋ฐ์ํ  ์๋ ์๋ค. [์ธ์์ ์ ์ฅํ  ์ ์๋ ๋ค์ํ storage](https://www.npmjs.com/package/express-session#compatible-session-stores)๊ฐ ์กด์ฌํ๋ค.)

![express-middleware-2](./express-middleware-2.png)

๊ทธ๋ผ ๊ฐ๋จํ ์ด๋ป๊ฒ ๋์๊ฐ๋์ง ํ์ธํด๋ณด์.

๋ค์ ์ฝ๋๋ session ๋ฏธ๋ค์จ์ด๋ฅผ ์ง๋๊ฐ๋ฉด์ ์ด๋ค req์ ์ด๋ค ๋ด์ฉ์ด ์๊ธฐ๋์ง ๋ณด๋ ์ฝ๋์ด๋ค.

```jsx
var express = require('express');
var session = require('express-session');

var app = express();

function logSessionInfo(req) {
  console.log(`req.session : ${req.session}`);
  console.log(`req.sessionID : ${req.sessionID}`);
}

app.use(function (req, res, next) {
  console.log(`express-session ํต๊ณผ ์ `);
  console.log(`req.headers.cookie : ${req.session}`);
  logSessionInfo(req);
  next();
});

app.use(
  session({
    secret: 'keyboard cat',
    resave: false,
    saveUninitialized: true,
  }),
);

app.use(function (req, res, next) {
  console.log(`express-session ํต๊ณผ ํ`);
  logSessionInfo(req);
  next();
});

// ยทยทยท
```

<br>

์ถ๋ ฅ ๊ฒฐ๊ณผ๋ ๋ค์๊ณผ ๊ฐ๋ค.

![express-middleware-3](./express-middleware-3.png)

<br>

๐๏ธ**์ ๋ฆฌ** ๐๏ธ

express-sesssion์ req.headers.cookie์ ์ฃผ์ด์ง sid๋ฅผ sessionID๋ก ๋ฒ์ญํ๊ณ  ๊ทธ sessionID์ ํด๋นํ๋ session ๊ฐ์ req.session์ ์ ์ฅํ๊ฒ ๋๋ค!

**์ฆ, ์ธ์์ ์ ๋ณด ๊ฐ์ ์ฟ ํค์ ์ ๋ฌ๋์ง ์๊ณ  ํด์ฌํ๋ sid๋ง ์ ์ ์ ์ฟ ํค์ ์ ์ฅ๋๊ณ  ์์ฒญ์ด ๋ค์ด์ค๋ฉด sid๋ฅผ ๋ฒ์ญํ๊ณ  ์ป์ session ID์ ํด๋นํ๋ session ๊ฐ์ req.session์ ๋ฃ์ด์ฃผ์ด nextํจ์์์ ์ฌ์ฉํ  ์ ์๊ฒ ํด์ค๋ค!!(์ด์  ์ข ์๊ฒ ๋ค...ใใใ)**

<br>

## ๐ค ๋ณธ๊ฒฉ express๋ก ๋ก๊ทธ์ธ ๊ตฌํํ๊ธฐ

๊ทธ๋ผ ์ด์  ๋ก๊ทธ์ธ ๊ตฌํ์ express์ middleware์ ์์๋ณด๊ณ  ๋ก๊ทธ์ธ ํ์ด์ง๋ฅผ ๊ตฌํํด๋ณด์.

### [passport](http://www.passportjs.org/docs/)

passport๋ node์์ ๊ฐ์ฅ ๋ง์ด ์ฐ์ด๋ authentication ๋ฏธ๋ค์จ์ด์ด๋ค. ๊ฐ๋จํ๊ฒ username๊ณผ password๋ฅผ ์ ๊ณตํ๋ ๋ก๊ทธ์ธ ๋ฐฉ๋ฒ๋ถํฐ OpenID์ OAuth ์ ๋ต๋ ์ ๊ณตํ๊ธฐ ๋๋ฌธ์ ๋งค์ฐ ์ ์ฉํ๊ฒ ์ฌ์ฉํ  ์ ์๋ค.

passport์์ ์ ๊ณตํ๋ ์ฌ๋ฌ strategy๋ฅผ ์ค์นํด์ ์ฌ์ฉํ  ์ ์๋ค.

![express-middleware-4](./express-middleware-4.png)

๋ค์๊ณผ ๊ฐ์ด passport์ ํ๋์ Strategy๋ฅผ ๊ฐ์ ธ์์

```jsx
const passport = require('passport');
const localStrategy = require('passport-local').Strategy;
```

์ด๋ค ์์ผ๋ก strategy์ ๊ตฌ์ฒด์ ์ธ ๋ด์ฉ์ ์ ์ํ๊ณ  passport์ ๋ฃ์ด์ค๋ค.

```jsx
passport.use(new LocalStrategy(
	//verify callback ํจ์
  function(username, password, done) {
    User.findOne({ username: username }, function (err, user) {
      if (err) { return done(err); }
			// ์์ด๋ ์์
      if (!user) {
        return donnull, false, { message: 'Incorrect username.' });
      }
			// ๋น๋ฐ๋ฒํธ ํ๋ฆผ
      if (!user.validPassword(password)) {
        return done(null, false, { message: 'Incorrect password.' });
      }
			// ์ฑ๊ณต
      return done(null, user);
    });
  }
));
```

๊ทธ๋ฆฌ๊ณ  passport.authenticate๋ฅผ ๋ค์๊ณผ ๊ฐ์ด login request์ ์ฌ์ฉํ  ์ ์๋ค.

```jsx
app.post('/login', passport.authenticate('local'), function (req, res) {
  // If this function gets called, authentication was successful.
  // `req.user` contains the authenticated user.
  res.redirect('/users/' + req.user.username);
});
```

passport.authentication ํจ์๊ฐ ์ฑ๊ณตํ๋ฉด req.user์ ์ ์  ์ ๋ณด๋ฅผ ๋ฃ์ด์ ์ฝ๋ฐฑ ํจ์๋ฅผ ์คํํ์ง๋ง ๋ก๊ทธ์ธ ์คํจ์ ๋ฐ๋ก 401 authentication error ๋ฉ์์ง๋ฅผ ์ ๋ฌํ๋ค.

<br>

**โ๊ทธ๋ผ ๋ก๊ทธ์ธ ์ฌ๋ถ๋ ์ด๋์ ๊ฒฐ์  ๋ ๊น?**

์์ ์ฝ๋์์ username, password, done์ ํ๋ผ๋ฏธํฐ๋ก ๋ฐ๋ ํจ์๋ verify callback๋ผ๊ณ  ํ๋๋ฐ ์ฌ๊ธฐ์ authentication ์ฑ๊ณต๊ณผ ์คํจ ์ฌ๋ถ๋ฅผ **doneํจ์**๋ก ์ ๋ฌํ๋ค. (์ด๋ ์ ๋ฌ๋ ๊ฐ์ด req.user์ ๋ฃ์ด์ง๋ค.)

์ฑ๊ณต์์๋ done์ ๋๋ฒ์งธ ์ธ์๋ก ์ ์  ์ ๋ณด๋ก ์คํจ์์๋ false๋ฅผ ๋ฐํํ๋ค.

์๋ฌ ๋ฐ์์์๋ ์ฒซ๋ฒ์งธ ์ธ์์ ์๋ฌ๋ฅผ ๋ฃ์ด์ ๋ฐํํ๋ค. // done(err);

<br>

**โ๋ก๊ทธ์ธ ์ธ์์ ์ฌ์ฉํ๊ณ  ์ถ๋ค๋ฉด?**

passport ๋ํ session์ ์ฌ์ฉํ  ์ ์๋ค.

๋ฌด์กฐ๊ฑด session ๋ฏธ๋ค์จ์ด๋ฅผ ์ด์ฉํ ํ์ passport์ session์ ์ฌ์ฉํ๋ค.

```jsx
app.use(express.session({ secret: 'keyboard cat' }));
app.use(passport.initialize());
app.use(passport.session());
```

์ธ์์ ์ด์ฉํ๊ธฐ ์ํด์๋ serializeUser์ deserializeUser ํจ์๋ฅผ ์ ์ํด์ค์ผ ํ๋ค.

```jsx
passport.serializeUser(function (user, done) {
  done(null, user.id);
});

passport.deserializeUser(function (id, done) {
  User.findById(id, function (err, user) {
    done(err, user);
  });
});
```

<br>

๐ฉ **serializeUser**

verify callback๊ฐ ์ ์  ์ ๋ณด๋ฅผ ์ ๋ฌํ๋ฉด ์คํ๋๋ ํจ์๋ก, ์ฑ๊ณตํ ์ ์ ์ ์ ๋ณด๋ฅผ session์ ์ถ๊ฐํ๋ค.

<br>

๐ค **deserializeUser**

deserializeUser์ Cookie์ ์ ์ฅ๋ passport session ์ ๋ณด๋ฅผ ์ด์ฉํด์ User์ ๋ณด๋ฅผ ๊ฐ์ ธ์ค๋ ํจ์์ด๋ค.  
์์์ session๊ณผ ๊ฐ์ด cookie์๋ ๊ตฌ์ฒด์ ์ธ ์ ์ ์ ๋ณด๊ฐ ๋ด๊ธฐ์ง ์๊ณ  passport session id๊ฐ ์ ์ฅ๋์ด ์๋ค.

๐session ์ฌ์ฉ๋์ ์ค์ด๊ธฐ ์ํด์ user์ id๋ง ์ ์ฅํ๊ณ  ์์ฒญ์ด ์ค๋ฉด id์ ํด๋นํ๋ ์ ์ ์ ๋ณด๋ฅผ ๊ฐ์ ธ์์ ์ฐ๋ฉด ์ข๋ค.

<br>

**โ๊ทธ๋ผ passport session์ ์ ์ ์๊ฒ ์ด๋ป๊ฒ ์ ์ฅ๋ ๊น?**

passport์ฉ ์ธ์์ด ์๋ก ์๊ธฐ๋ ๊ฒ ์๋๋ผ express session์ ํ๋์ property๋ก ๋ค์ด๊ฐ๊ฒ ๋๋ค.  
cookie์ ๋ค์ด์๋ express session์ด ์์ฑํ connect.sid์ ํ๋ฉด ๊ทธ ์์ passport session ์ ๋ณด๊ฐ ๋ค์ด์๋ ๊ฑธ ๋ณผ ์ ์๋ค.

![express-middleware-5](./express-middleware-5.png)

<br>

**โ๋ก๊ทธ์ธ ์ํ์ ๋ฐ๋ผ ํ์ด์ง ์ ๊ทผ ์ ์ดํ๊ธฐ!**

๋ง์ดํ์ด์ง์ ๊ฐ์ ํ์ด์ง์ ์ ๊ทผํ  ๋๋ ์ ์ ์ ๋ก๊ทธ์ธ ์ํ์ ๋ฐ๋ผ์ ํ์ด์ง๋ฅผ ๋ฌ๋ฆฌ ํด์ค์ผ ํ๋ค.

์ด๋ฐ ์ํฉ์๋ passport์ ์ํด req์ ์์ฑ๋ isAuthenticated๋ฅผ ์ด์ฉํ  ์ ์๋ค. ํจ์์ ํํ๋ ๋ค์๊ณผ ๊ฐ๋ค.

```jsx
req.isAuthenticated = function () {
  var property = 'user';
  if (this._passport && this._passport.instance) {
    property = this._passport.instance._userProperty || 'user';
  }

  return this[property] ? true : false;
};
```

์์ ํจ์๋ฅผ ์ด์ฉํ๋ฉด ๋ค์๊ณผ ๊ฐ์ ํจ์๋ฅผ ๋ง๋ค์ด์ ํ์ด์ง๋ฅผ ๋ณด์ฌ์ฃผ๊ธฐ ์ ์ ๋ก๊ทธ์ธ ์ํ๋ฅผ ํ์ธํ์ฌ ๋ก๊ทธ์ธ ๋์ง ์์ req๋ฅผ login page๋ก redirect ํด์ค ์ ์๋ค.

```jsx
function isAuthenticated(req, res, next) {
  if (req.isAuthenticated()) return next();
  return res.redirect('/login');
}

// ยทยทยท

router.get('/mypage', isAuthenticated, (req, res) => res.render('mypage', { user: req.user }));
```

<br>

### [bcrypt](https://www.npmjs.com/package/bcrypt)

bcrpyt๋ ๋น๋ฐ๋ฒํธ๋ฅผ ์ฝ๊ฒ ์ํธํํด์ฃผ๋ ๋ฏธ๋ค์จ์ด์ด๋ค.

hash๋ฅผ ์์ฑํ ๋๋ bcrypt์ hash ํจ์๋ฅผ ์ด์ฉํ๊ณ  ๋น๋ฐ๋ฒํธ๋ฅผ ํ์ธํ  ๋๋ compare ํจ์๋ฅผ ์ด์ฉํ๋ค.

```jsx
const saltRounds = 10;
user.passwordHash = await bcrypt.hash(password, saltRounds);
const match = await bcrypt.compare(password, user.passwordHash);
```

<br>

**โbcrpyt๊ฐ ๊ทผ๋ฐ ๋ญ์ง์? [๋น๋ฐ๋ฒํธ ์ํธํ ๊ด๋ จ ์ฌ์ง ์ถ์ฒ ๋ฐ ์ฐธ๊ณ ์๋ฃ](https://d2.naver.com/helloworld/318732)**

๋น๋ฐ๋ฒํธ๋ฅผ ๋จ๋ฐฉํฅ์ผ๋ก hashing ๋ง์ผ๋ก ์๊ธธ ์ ์๋ ์ ์ถ ๊ฐ๋ฅ์ฑ์ด๋ ๋น ๋ฅธ ์๋๋ก ์ธํด ํด์ปค๋ค์๊ฒ ํธ์์ฑ์ ์ ๊ณตํ  ์ ์๋ค.

์ด๋ฅผ ํด๊ฒฐํ๊ธฐ ์ํด salt๋ฅผ ๋น๋ฐ๋ฒํธ์ ๋ํ ํ์ hashing์ ์งํํ์ฌ ๋ค์ด์ ์คํธ๋ฅผ ์์ฑํ๋ค.  
bcrypt๋ ์ด์ ๋ํด ๋ค์ด์ ์คํธ๋ฅผ ์์ฑํ๋ ๊ณผ์ ์ ๋ช๋ฒ ์งํํ ์ง ๊ฒฐ์ ํ๋ 'work factor'(์ฌ๊ธฐ์๋ **saltRounds**์ด๋ค)๋ฅผ ์กฐ์ ํ๋ ๊ฒ ๋ง์ผ๋ก **์์คํ ๋ณด์์ฑ์ ์ฆ๊ฐ**์ํจ๋ค๊ณ  ํ๋ค.

![express-middleware-6](./express-middleware-6.png)

<br>

### [flash](https://www.npmjs.com/package/connect-flash)

flash๋ ์ธ์์์ ๋ฉ์์ง๋ฅผ ์ ์ฅํ  ๋ ์ฌ์ฉํ๋ ํน๋ณํ ๊ณต๊ฐ์ด๋ค.

flash์ ์์ฑ๋ ๋ฉ์์ง๋ ํ๋ฒ ์ ์ ํํ display๋๋ฉด ๋ฐ๋ก ์ญ์ ๋๋ค.

<br>

**โ์ด๋์ ์ธ๊น? ๋ก๊ทธ์ธ ์คํจ ๋ฉ์์ง ์ ๋ฌ์!**

์ฃผ๋ก redirect์ ๋ง์ด ์ฌ์ฉ๋๋๋ฐ ํนํ ๋ก๊ทธ์ธ ์คํจ ์ด์  ๋ฉ์์ง๋ฅผ ๋์ธ ๋ ์ฌ์ฉํ๋ฉด ๋งค์ฐ ์ ์ฉํ๋ค ใใ

passport๋ flash๋ฅผ ์ด์ฉํด์ message๋ฅผ ๋์ฐ๋ ๊ฑธ ์ง์ํ๋ค.

verify callback ํจ์๋ฅผ ๋ณด๋ฉด ๋ค์๊ณผ ๊ฐ์ด message๋ฅผ ๊ฐ์ด ๋ณด๋ด์ฃผ๊ฒ ๋๋ค. ์ด ๋ถ๋ถ์ flash์ ์ ์ฅ๋๊ฒ ๋๋ค.

```jsx
// ยทยทยท
if (!user) {
  return done(null, false, { message: 'Incorrect username.' });
}
if (!user.validPassword(password)) {
  return done(null, false, { message: 'Incorrect password.' });
}
// ยทยทยท
```

๊ทธ๋ฆฌ๊ณ  req.flash()๋ฅผ ์ด์ฉํด์ ํด๋น ๊ฐ์ ์ ์ ์๊ฒ ์ ๋ฌํ  ์ ์๋ค!**(ํ๋ฒ ๋ณด์ฌ์ฃผ๋ฉด ์ฌ๋ผ์ง๋ค.)**

```jsx
router.get('/login', (req, res) =>
  req.isAuthenticated()
    ? res.redirect('/mypage')
    : res.render('login', { failureMsg: req.flash().error }),
);
```

![express-middleware-7](./express-middleware-7.png)

<br>

## ๐ ๋ก๊ทธ์ธ ์ ๋ณด ์ ์ฅ์ฉ ํ์ผ ๊ธฐ๋ฐ ๋๋น ๊ตฌํํ๊ธฐ

์ด์ ์ ์ฌ์ฉํ๋ sequelize์ ๊ฐ์ ORM๊ณผ ์ ์ฌํ๊ฒ ํ์ด๋ธ ํํ๋ฅผ ์ ์ํ๊ณ  create, update, getById ํจ์๋ฅผ ๋ด์ฅํ ๋ชจ๋ธ ํด๋์ค๋ฅผ ๋ง๋ค์ด๋ณด์๋ค.

validate ํจ์๋ฅผ ํตํด ์ ์ ๊ฐ ์๋ ฅํ ๊ฐ์ด ํ์ด๋ธ์ attributes์ ํ์๊ณผ ์ผ์นํ๋์ง ํ์ธํ๋ ํจ์๋ ๊ตฌํํด๋ดค๋ค ใใ

```jsx
const fs = require('fs');
const path = require('path');

class Model {
  static sync = function () {
    if (fs.existsSync(this.fileName)) {
      const data = fs.readFileSync(this.fileName, 'utf8');
      this.items = JSON.parse(data);
    }
  };

  static init = (attributesTypes, { tableName, sync }) => {
    this.tableName = tableName;
    this.dirname = path.join(__dirname, `../database`);
    this.fileName = `${this.dirname}/${tableName}.json`;
    this.attributesTypes = attributesTypes;
    this.items = [];
    if (sync) this.sync();
  };

  static write = function () {
    const data = JSON.stringify(this.items);
    if (!fs.existsSync(this.dirname)) fs.mkdirSync(this.dirname);
    fs.writeFileSync(this.fileName, data, 'utf8');
  };

  static validate = function (item) {
    const data = {};
    for (const [key, value] of Object.entries(item)) {
      if (!this.attributesTypes[key] || !value) continue;

      switch (this.attributesTypes[key]) {
        case 'date':
          data[key] = Date(value);
          break;
        case 'boolean':
          data[key] = value == 'on' || value == 1;
          break;
        case typeof value:
          data[key] = value;
          break;
        default:
          throw new Error('User Input Error');
      }
    }
    data.createdAt = Date.now();
    data.updatedAt = Date.now();
    return data;
  };

  static getById = (id) => this.items.find((item) => item.id === id);

  static create = function (item) {
    const validatedItem = this.validate(item);
    this.items.push(validatedItem);
    this.write();
    return validatedItem;
  };

  static update = function (item) {
    const id = this.items.findIndex(item.id);
    item.updatedAt = Date.now();
    this.items[id] = item;
    this.write();
  };

  static delete = function (item) {
    const id = this.items.findIndex(item.id);
    item.updatedAt = Date.now();
    if (id) this.items[id] = null;
    this.write();
  };
}

module.exports = Model;
```

๊ทธ๋ฆฌ๊ณ  User table์ ์์ ๋ชจ๋ธ๋ฅผ ๊ธฐ๋ฐ์ผ๋ก ๋ง๋ค์๋ค:)

```jsx
const Model = require('./model');

class Users extends Model {
  static init() {
    return super.init(
      {
        id: 'string',
        pw: 'string',
        email: 'string',
        name: 'string',
        phoneNo: 'string',
        address1: 'string',
        address2: 'string',
        zipCode: 'string',
        isAdAgreed: 'boolean',
      },
      {
        tableName: 'Users',
        sync: true,
      },
    );
  }
}

module.exports = Users;
```

<br>

## ๐ฝ๏ธ ํ๋ก์ ํธ ๊นํ ๋ ํฌ์งํ ๋ฆฌ

[[์ฐ์ํํํฌ์บ ํ] ๋ฐฐ๋ฏผ์ํ ํ์๊ฐ์/๋ก๊ทธ์ธ ๊ตฌํ ํ๋ก์ ํธ](https://github.com/woowa-techcamp-2020/market-8)

<br>

## ๐ญ ํ๊ณ 

- ์ด๋ฒ ๊ธฐํ๋ฅผ ํตํด์ ์ธ์์ด ์ด๋ป๊ฒ ๋์ํ๊ณ  ํนํ passport์์ ์ธ์์ด ์ด๋ป๊ฒ ์ด์ฉ๋๋์ง ์ข๋ ์ ์ดํดํ  ์ ์์๋ ๊ฒ ๊ฐ๋ค.
- ๋ค์์๋ morgan์ ํ์ผ๋ก ๋ก๊นํ๋๋ฐ ๊น์ง ์ฌ์ฉํด๋ด์ผ๊ฒ ๋ค.
- ๋ชจ๋ฅด๊ณ  ์ฌ์ฉํด์ ์ฌ์ค ๋ถ์ํ ๋ถ๋ถ๋ค์ด ๋ง์๋๋ฐ ์ด๋ฒ ๊ธฐํ์ ๊ทธ๋ฐ ๋ถ์ํจ์ด ๋ง์ด ํด์๋ ๊ฒ ๊ฐ์ ๋ณด๋์ฐจ๋ค.
- **โ๋ฌด์๋ณด๋ค ํ๋ก ํธ์๋๋ ๋๋ฌด ๋ถ์กฑํ๋ ๋ค์ ๊ธฐํ์๋ ํ๋ก ํธ์๋ ๊ณต๋ถ์๋ ๋ ๋ง์ด ์ ๊ฒฝ์จ๋ด์ผ๊ฒ ๋ค!**

> ์๋ชป ์ ๋ฆฌ๋ ์ ์ด๋ ํผ๋๋ฐฑ ์์ผ๋ฉด ๋ง์ํด์ฃผ์ธ์!

```toc

```
