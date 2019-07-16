# Applied Accessibility

"Accessibility" generally means having web content and a user interface that can be understood, navigated, and interacted with by a broad audience. This includes people with visual, auditory, mobility, or cognitive disabilities. Websites should be open and accessible to everyone, regardless of a user's abilities or resources. Some users rely on assistive technology such as a screen reader or voice recognition software. Other users may be able to navigate through a site only using a keyboard. Keeping the needs of various users in mind when developing your project can go a long way towards creating an open web. Here are three general concepts this section will explore throughout the following challenges:



1. have well-organized code that uses appropriate markup
2. ensure text alternatives exist for non-text and visual content
3. create an easily-navigated page that's keyboard-friendly

<br>

### Add a Text Alternative to Images for Visually Impaired Accessibility

It's likely you've seen an `alt`attribute on an `img`tag in other challenges. `Alt`text describes the content of the image and provides a text-alternative. This helps in case the image fails to load or can't be seen by a user. It's also used by search engines to understand what an image contains to include it in search results. Here's an example:

```html
<img src="importantLogo.jpeg" alt="Company logo">
```

People with visual impairments rely on screen readers to convert web content to an audio interface. They won't get information if it's only presented visually. For images, screen readers can access the `alt`attribute and read its contents to deliver key information.

Good `alt`text is short but descriptive, and meant to briefly convey the meaning of the image. You should always include an `alt`attribute on your image. Per HTML5 specification, this is now considered mandatory.

<br>

### Know When Alt Text Should be Left Blank

In the last challenge, you learned that including an `alt`attribute on img tags is mandatory. However, sometimes images are grouped with a caption already describing them, or are used for decoration only. In these cases `alt`text may seem redundant or unnecessary.

In situations when an image is already explained with text content, or does not add meaning to a page, the `img`still needs an `alt`attribute, but it can be set to an empty string. Here's an example:

```html
<img src="visualDecoration.jpeg" alt="">
```

Background images usually fall under the 'decorative' label as well. However, they are typically applied with CSS rules, and therefore not part of the markup screen readers process.

**Tip**: For images with a caption, you may still want to include `alt`text, since it helps search engines catalog the content of the image.

```html
<h1>Deep Thoughts with Master Camper Cat</h1>
<article>
    <h2>Defeating your Foe: the Red Dot is Ours!</h2>
    <p>To Come...</p>
</article>

<img src="samuraiSwords.jpeg" alt="">

<article>
    <h2>Is Chuck Norris a Cat Person?</h2>
    <p>To Come...</p>
</article>
```

<br>

### Use Headings to Show Hierarchical Relationships of Content

Headings (`h1`through `h6`elements) are workhorse tags that help provide structure and labeling to your content. Screen readers can be set to read only the headings on a page so the user gets a summary. This means it is important for the heading tags in your markup to have semantic meaning and relate to each other, not be picked merely for their size values.

*Semantic meaning* means that the tag you use around content indicates the type of information it contains.

If you were writing a paper with an introduction, a body, and a conclusion, it wouldn't make much sense to put the conclusion as a subsection of the body in your outline. It should be its own section. Similarly, the heading tags in a webpage need to go in order and indicate the hierarchical relationships of your content.

Headings with equal (or higher) rank start new implied sections, headings with lower rank start subsections of the previous one.

As an example, a page with an `h2`element followed by several subsections labeled with `h4`tags would confuse a screen reader user. With six choices, it's tempting to use a tag because it looks better in a browser, but you can use CSS to edit the relative sizing.

One final point, each page should always have one (and only one) `h1`element, which is the main subject of your content. This and the other headings are used in part by search engines to understand the topic of the page.

<br>

### Jump Straight to the Content Using the main Element

HTML5 introduced a number of new elements that give developers more options while also incorporating accessibility features. These tags include `main`, `header`, `footer`, `nav`, `article`, and `section`, among others.

By default, a browser renders these elements similarly to the humble `div`. However, using them where appropriate gives additional meaning in your markup. The tag name alone can indicate the type of information it contains, which adds semantic meaning to that content. Assistive technologies can access this information to provide better page summary or navigation options to their users.

The `main`element is used to wrap (you guessed it) the main content, and there should be only one per page. It's meant to surround the information that's related to the central topic of your page. It's not meant to include items that repeat across pages, like navigation links or banners.

The `main`tag also has an embedded landmark feature that assistive technology can use to quickly navigate to the main content. If you've ever seen a "Jump to Main Content" link at the top of a page, using a main tag automatically gives assistive devices that functionality.

```html
<header>
    <h1>Weapons of the Ninja</h1>
</header>
<main></main>

<footer></footer>
```

<br>

### Wrap Content in the article Element

`article`is another one of the new HTML5 elements that adds semantic meaning to your markup. `Article`is a sectioning element, and is used to wrap independent, self-contained content. The tag works well with blog entries, forum posts, or news articles.

Determining whether content can stand alone is usually a judgement call, but there are a couple simple tests you can use. Ask yourself if you removed all surrounding context, would that content still make sense? Similarly for text, would the content hold up if it were in an RSS feed?

Remember that folks using assistive technologies rely on organized, semantically meaningful markup to better understand your work.

**Note about sectionand div**
The `section`element is also new with HTML5, and has a slightly different semantic meaning than `article`. An `article`is for standalone content, and a `section`is for grouping thematically related content. They can be used within each other, as needed. For example, if a book is the `article`, then each chapter is a `section`. When there's no relationship between groups of content, then use a `div`.

```pseudocode
<div> - groups content
<section> - groups related content
<article> - groups independent, self-contained content
```

```html
<h1>Deep Thoughts with Master Camper Cat</h1>
<main>
    <article>
        <h2>The Garfield Files: Lasagna as Training Fuel?</h2>
        <p>The internet is littered with varying opinions on nutritional paradigms, from catnip paleo to hairball cleanses. But let's turn our attention to an often overlooked fitness fuel, and examine the protein-carb-NOM trifecta that is lasagna...</p>
    </article>

    <img src="samuraiSwords.jpeg" alt="">

    <article>
        <h2>Defeating your Foe: the Red Dot is Ours!</h2>
        <p>Felines the world over have been waging war on the most persistent of foes. This red nemesis combines both cunning stealth and lightening speed. But chin up, fellow fighters, our time for victory may soon be near...</p>
    </article>

    <img src="samuraiSwords.jpeg" alt="">

    <article>
        <h2>Is Chuck Norris a Cat Person?</h2>
        <p>Chuck Norris is widely regarded as the premier martial artist on the planet, and it's a complete coincidence anyone who disagrees with this fact mysteriously disappears soon after. But the real question is, is he a cat person?...</p>
    </article>
</main>
```

<br>

### Make Screen Reader Navigation Easier with the header Landmark

The next HTML5 element that adds semantic meaning and improves accessibility is the `header`tag. It's used to wrap introductory information or navigation links for its parent tag, and works well around content that's repeated at the top on multiple pages.

`header`shares the embedded landmark feature you saw with `main`, allowing assistive technologies to quickly navigate to that content.

**Tip**: `header`is meant for use in the `body`tag of your HTML document. This is different than the `head`element, which contains the page's title, meta information, etc.

```html
<body>
    <header>
        <h1>Training with Camper Cat</h1>
    </header>


    <main>
        <section id="stealth">
            <h2>Stealth &amp; Agility Training</h2>
            <article><h3>Climb foliage quickly using a minimum spanning tree approach</h3></article>
            <article><h3>No training is NP-complete without parkour</h3></article>
        </section>
        <section id="combat">
            <h2>Combat Training</h2>
            <article><h3>Dispatch multiple enemies with multithreaded tactics</h3></article>
            <article><h3>Goodbye world: 5 proven ways to knock out an opponent</h3></article>
        </section>
        <section id="weapons">
            <h2>Weapons Training</h2>
            <article><h3>Swords: the best tool to literally divide and conquer</h3></article>
            <article><h3>Breadth-first or depth-first in multi-weapon training?</h3></article>
        </section>
    </main>
</body>
```

<br>

###  Make Screen Reader Navigation Easier with the nav Landmark

The `nav`element is another HTML5 item with the embedded landmark feature for easy screen reader navigation. This tag is meant to wrap around the main navigation links in your page.

If there are repeated site links at the bottom of the page, it isn't necessary to markup those with a `nav`tag as well. Using a `footer`(covered in the next challenge) is sufficient.

```html
<body>
    <header>
        <h1>Training with Camper Cat</h1>

        <nav>
            <ul>
                <li><a href="#stealth">Stealth &amp; Agility</a></li>
                <li><a href="#combat">Combat</a></li>
                <li><a href="#weapons">Weapons</a></li>
            </ul>
        </nav>

    </header>
    <main>
        <section id="stealth">
            <h2>Stealth &amp; Agility Training</h2>
            <article><h3>Climb foliage quickly using a minimum spanning tree approach</h3></article>
            <article><h3>No training is NP-complete without parkour</h3></article>
        </section>
        <section id="combat">
            <h2>Combat Training</h2>
            <article><h3>Dispatch multiple enemies with multithreaded tactics</h3></article>
            <article><h3>Goodbye world: 5 proven ways to knock out an opponent</h3></article>
        </section>
        <section id="weapons">
            <h2>Weapons Training</h2>
            <article><h3>Swords: the best tool to literally divide and conquer</h3></article>
            <article><h3>Breadth-first or depth-first in multi-weapon training?</h3></article>
        </section>
    </main>
</body>
```

<br>

### Make Screen Reader Navigation Easier with the footer Landmark

Similar to `header`and `nav`, the `footer`element has a built-in landmark feature that allows assistive devices to quickly navigate to it. It's primarily used to contain copyright information or links to related documents that usually sit at the bottom of a page.

```html
<body>
    <header>
        <h1>Training</h1>
        <nav>
            <ul>
                <li><a href="#stealth">Stealth &amp; Agility</a></li>
                <li><a href="#combat">Combat</a></li>
                <li><a href="#weapons">Weapons</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section id="stealth">
            <h2>Stealth &amp; Agility Training</h2>
            <article><h3>Climb foliage quickly using a minimum spanning tree approach</h3></article>
            <article><h3>No training is NP-complete without parkour</h3></article>
        </section>
        <section id="combat">
            <h2>Combat Training</h2>
            <article><h3>Dispatch multiple enemies with multithreaded tactics</h3></article>
            <article><h3>Goodbye world: 5 proven ways to knock out an opponent</h3></article>
        </section>
        <section id="weapons">
            <h2>Weapons Training</h2>
            <article><h3>Swords: the best tool to literally divide and conquer</h3></article>
            <article><h3>Breadth-first or depth-first in multi-weapon training?</h3></article>
        </section>
    </main>


    <footer>&copy; 2018 Camper Cat</footer>


</body>
```

<br>

### Improve Accessibility of Audio Content with the audio Element

HTML5's `audio`element gives semantic meaning when it wraps sound or audio stream content in your markup. Audio content also needs a text alternative to be accessible to people who are deaf or hard of hearing. This can be done with nearby text on the page or a link to a transcript.

The `audio`tag supports the `controls`attribute. This shows the browser default play, pause, and other controls, and supports keyboard functionality. This is a boolean attribute, meaning it doesn't need a value, its presence on the tag turns the setting on.

Here's an example:

```html
<audio id="meowClip" controls>
    <source src="audio/meow.mp3" type="audio/mpeg" />
    <source src="audio/meow.ogg" type="audio/ogg" />
</audio>
```

**Tip**: Multimedia content usually has both visual and auditory components. It needs synchronized captions and a transcript so users with visual and/or auditory impairments can access it. Generally, a web developer is not responsible for creating the captions or transcript, but needs to know to include them.

```html
<body>
  <header>
    <h1>Real Coding Ninjas</h1>
  </header>
  <main>
    <p>A sound clip of Zersiax's screen reader in action.</p>
    <audio controls>
      <source src="https://s3.amazonaws.com/freecodecamp/screen-reader.mp3" type="audio/mpeg"/>
    </audio>
  </main>
</body>
```