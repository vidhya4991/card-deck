# HTML5 Deck of Cards
[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/pakastin/deck-of-cards?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

Pure vanilla JS (+ CSS3) – no dependencies, by [Juha Lindstedt](https://github.com/pakastin) & [contributors](https://github.com/pakastin/deck-of-cards/graphs/contributors).

https://deck-of-cards.js.org

[Install from Google Chrome Web Store](https://chrome.google.com/webstore/detail/html5-deck-of-cards/ljafdfknpepklmkhomgaocmehgfdcpno)

Frontside card graphics are slightly modified from Chris Aguilar's awesome [Vector Playing Card Graphics Set](http://sourceforge.net/projects/vector-cards/).

Also check out my [RE:DOM](https://redom.js.org) and [HTML5 Node Garden](https://nodegarden.js.org) projects!

## Note
I'm currently rewriting the Deck of Cards. Lots of cool stuff coming soon! 😉

## License

LGPL if you use Chris Aguilar's [vector playing cards](http://sourceforge.net/projects/vector-cards/). Otherwise MIT.

## Download

- [Production version (~5 KB uncompressed)](https://deck-of-cards.js.org/dist/deck.min.js)
- [Development version (~15 KB uncompressed)](https://deck-of-cards.js.org/dist/deck.js)



## Usage

### Full example

``` html
<html>
    <head>
        <title>Cards</title>

        <link rel="stylesheet" href="node_modules/deck-of-cards/example/example.css">
    </head>
    <body>
        <script src="node_modules/deck-of-cards/dist/deck.min.js"></script>

        <div id="container"></div>

        <script>
            var $container = document.getElementById('container');

            // create Deck
            var deck = Deck();

            // add to DOM
            deck.mount($container);

            deck.cards.forEach(function (card, i) {
                card.setSide(Math.random() < 0.5 ? 'front' : 'back');

                // explode
                card.animateTo({
                    delay: 1000 + i * 2, // wait 1 second + i * 2 ms
                    duration: 500,
                    ease: 'quartOut',

                    x: Math.random() * window.innerWidth - window.innerWidth / 2,
                    y: Math.random() * window.innerHeight - window.innerHeight / 2
                });
            });
        </script>
    </body>
</html>
```

Available on JsFiddle: http://jsfiddle.net/x0gjood1/


### Javascript API

#### Deck

``` js
// Instanciate a deck
var deck = Deck();

// display it in a html container
var $container = document.getElementById('container');
deck.mount($container);
```

Deck example: http://jsfiddle.net/ec4kcx1k/

``` js
// Flip all cards in deck
deck.flip();

// Sort cards
deck.sort();

// Shuffle
deck.shuffle();

// Display fan
deck.fan();

// Remove deck from html container, hide it
deck.unmount();
```

Shuffle cards and fan: http://jsfiddle.net/favbdkta/

Deck with jokers:

``` js
// Instanciate a deck with jokers
var deck = Deck(true);
``


#### Card in deck

Remove a card from a deck

``` js
var deck = Deck();

// Remove 10 cards starting from the 6th
var removedCards = deck.cards.splice(5, 10);

removedCards.forEach(function (removedCard) {
    removedCard.unmount();
});
```

Deck without Clubs: http://jsfiddle.net/L25facxj/

#### Card

``` js
// Select the first card
var card = deck.cards[0];

// Add it to an html container
card.mount($container);

// Allow to move/drag it
card.enableDragging();
card.disableDragging();

// Allow to flip it
card.enableFlipping();
card.disableFlipping();

// Flip card
card.flip();

// Display card front or back
card.setSide('front');
card.setSide('back');
```

Draggable and flippable card: http://jsfiddle.net/cgz9mjts/