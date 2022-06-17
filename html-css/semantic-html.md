### Semantic HTML

- Semantic HTML helps express the **meaning** or purpose of the content in a webpage:

	<img src="https://i.imgur.com/2jxmD28.png">

- Benefits for the developer:
	- Semantic HTML makes the developer's intentions more clear as to what the developer is trying to accomplish.
- Benefits for the user:
	- More accurate web searches via better SEO (search engine optimization).
	- Improves accessibility for the vision impaired because screen readers can do their job better.

#### Pair up and research these semantic tags:

   1. `<section>`
   2. `<article>`
   3. `<aside>`
   4. `<figure>`
   5. `<footer>`
   6. `<header>`
   7. `<main>`
   8. `<nav>`

We'll discuss your findings in 5 minutes.

##### Discuss
- What meaning does each semantic provide?

### Essential Questions

1. Explain what semantic HTML is and the benefits it provides.
2. What are attributes and what are they used for?
3. It is important to properly __________ nested elements to make the markup more readable and less prone to errors.

## Practice Exercise / Lab

#### Create a new `index.html` file and copy the HTML below into it. Refactor the HTML code so it uses semantic HTML tags instead of non-semantic tags. Use [Codecademy's tutorial](https://www.codecademy.com/learn/learn-html/modules/learn-semantic-html) as a reference.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <!-- Font Awesome -->
  <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.2.0/css/all.css" integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" crossorigin="anonymous">
  <title>HTML & CSS</title>
</head>
<body>
  <div class="header">
    <div class="container">
      <div class="row">
        <span class="col col-8 first logo">HTML</span>
        <div class="col col-4">
          <ul class="nav">
            <li class="nav-item"><a class="nav-link" href="#">Home</a></li>
            <li class="nav-item"><a class="nav-link" href="#">About</a></li>
            <li class="nav-item"><a class="nav-link" href="#">Contact</a></li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <div class="container">
    <div class="row">
      <div class="col col-2 first">
        <img src="http://picsum.photos/200" alt="Some Image" width="200" />
      </div>
      <div class="col col-10">
        <h2>Lorem ipsum dolor sit amet.</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. In tempore est quam officiis maiores tempora dolores exercitationem, aliquid voluptas enim, eius earum explicabo, quibusdam vitae!</p>
        <span>More... >></span>
      </div>
    </div>
  </div>

  <div class="container">
    <div class="row">
      <div class="col col-2 first">
        <img src="http://picsum.photos/20" alt="Some Image" width="200" />
      </div>
      <div class="col col-10">
        <h2>Lorem ipsum dolor sit amet.</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. In tempore est quam officiis maiores tempora dolores exercitationem, aliquid voluptas enim, eius earum explicabo, quibusdam vitae!</p>
        <span>More... >></span>
      </div>
    </div>
  </div>

  <div class="container">
    <div class="row">
      <div class="col col-2 first">
        <img src="http://picsum.photos/30" alt="Some Image" width="200" />
      </div>
      <div class="col col-10">
        <h2>Lorem ipsum dolor sit amet.</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. In tempore est quam officiis maiores tempora dolores exercitationem, aliquid voluptas enim, eius earum explicabo, quibusdam vitae!</p>
        <span>More... >></span>
      </div>
    </div>
  </div>

  <div class="footer">
    <div class="social">
      <i class="fab fa-facebook-square"></i>
      <i class="fab fa-twitter-square"></i>
      <i class="fab fa-google-plus-square"></i>
    </div>
    <p>&copy; <span id="year"></span> Acme Inc.</p>
  </div>

</body>
</html>
```
