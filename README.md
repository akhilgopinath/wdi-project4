# CSM Bot

[Heroku Deployment](https://postalcsbot.herokuapp.com/)

## Short
***CSM Bot*** is a proof-of-concept customer service chatbot that seamlessly integrates a clean and light-weight React User interface with real-time interaction analysis powered by the IBM Watson Tone Analyzer and trained Wit.Ai decision-aggregation models

## Introduction / Problem Statement
The proliferation of offshore customer service operations has distanced users from seeking answers to time-sensitive problems, or even questions they might be facing. Navigating complex websites is daunting and places unnecessary road blocks in the way of the user. Energized by a less-than-satisfactory experience locating a mis-delivered package by one of our members, our team set out to explore ways to facilitate meaningful front-facing customer interaction - with deep learning capabilities focused on listening to the user.

### Objective
* Make a chatbot that can make API calls -- and can be deployed on a website

## Framework
We chose the [React on Rails](https://github.com/shakacode/react_on_rails) by Shakacode. Like the react-rails gem, React on Rails is capable of server-side rendering with fragment caching and is compatible with turbolinks. Unlike react-rails, which depends heavily on sprockets and jquery-ujs, React on Rails uses webpack and does not depend on jQuery. While the initial setup is slightly more involved, it allows for advanced functionality such as:

1. Redux (for action cables)
2. Webpack optimization functionality
3. React Router
4. Ability to use **both** ruby gems and npm packages
5. Can optimize for SEO (through use of pre-renders)

Cons
1. Native modules tend to break down on some module installations - cost us a lot of time
2. Debugging was difficult because of webpack

## Built with
------
* React
* Rails
* Node.js
* CSS
* [ReactSimpleChatBot](https://github.com/LucasBassetti/react-simple-chatbot)
* [Type.js.JQuery](type.js)
* [Bootstrap Dashboard](https://startbootstrap.com/template-overviews/sb-admin/)

## APIs
* [IBM Watson Tone Analyzer](https://www.ibm.com/watson/developercloud/tone-analyzer.html)
* [Wit.ai](https://wit.ai/)
* [D3](https://d3js.org/)]

## IBM Watson Tone Analyzer

The IBM Watson™ Tone Analyzer service uses linguistic analysis to detect emotional, social, and language tones in written text. API has two endpoints: general purpose and customer engagement. Due to the time constraint, we only managed to implement the general tone analyzer.

API is available for several clients such node, python, java. This is how we implemented the API call from react component/javascript.

```javascript
// message = encodeURIComponent(message);
//  fetch(`https://watson-api-explorer.mybluemix.net/tone-analyzer/api/v3/tone?version=2016-05-19&text=${message}`)
// .then((response) => {
//   return response.json();
// })
// .then((json) => {
  // do something with response from api
}
```

Part of the api output:

```javascript
"tones": [
    {
      "score": 0.134622,
      "tone_id": "anger",
      "tone_name": "Anger"
    },
```

## D3 for Data Visualization

D3.js is a JavaScript library for manipulating documents based on data. D3 helps you bring data to life using HTML, SVG, and CSS. D3 has a very good documentation and lots of examples on what can be achieved with this library.

However, it can be overwhelming while trying to explore this library and has to admit that there is a high learning curve in the beginning. With the limited time that we have, we only managed to implement a simple bar chart and that has taken us huge amount of time.

------
## Development
* Week 1 - We explored **a lot** of APIs -- Google Vision API (Object recognition, Geocoding, Face recognition, Natural Language Processing, Sentiment Analysis), Twitter real-time streaming API (using Python), Wit.Ai and narrowed our focus to a chatbot that can make API calls -- and can be deployed on a website. Raymond explored app integrations using both the React-Rails and React-on-Rails.

* Week 2 - We found a recent-release react-simple-chatbot by (LucasBassetti)[https://github.com/LucasBassetti] and found it to be a really light-weight UI with styling options and somewhat flexible integration. But we had to **hack a lot**. For instance, dynamic chat routing was not supported:

![Dynamic Trigger Issue](https://github.com/lackdaz/wdi-project4/blob/master/public/img/issues1.png)

But we found a solution buried deep in documentation:

![Breakout](https://github.com/lackdaz/wdi-project4/blob/master/public/img/solution1.png)

which opened up to the possibility -- and *complexities* of doing (req,res) callbacks within the chat engine. We spent a lot of time debating, experimenting and integrating this feature, and understanding the chat engine and design.

We opened a number of issues, and gave some recommendations for modest improvement on the engine -- and changes were implemented very quickly!:

![Feedback](https://github.com/lackdaz/wdi-project4/blob/master/public/img/feedback.png)


* Week 3 - Ultimately, in the final product sprint, we downloaded the source codes and made several modifications to allow for bi-directional flow of information between our components -- and this allowed us a lot of creative and programming freedom for passing states and props between the parent component and child components.

## Components

| Parent | Child                | Child  |
|:------:|:------:              |:------:|
| MainApp| Chatbot (NPM)        | Many   |
| --     | SentimentBot         | --     |
| --     | CustomerServiceChat  | --     |


### Obstacles
* Implementing user stories for chatbots is difficult!
* The React Component lifecycle was very challenging -- especially to API calls that have the same message/response
* Webpacks crash your Atom if you're not careful! It basically disabled search-all functions
* The webpack precompiling of .css and .js files doesn't seem to work very well with .scss files. I had to modify custom bootstrap css to do CSS styling

### Points of Interest
* Chatbots are very, very useful --- especially when used with the ReactDOM router. It can help to direct you to relevant pages.
* Introducing dynamic chat routing increases your code complexity exponentially

### Performance
* There are definitely performance issues -- particular with new initializing new sessions and large chat sessions. We've noticed that all the previous chat messages are re-rendered each update, and finding shouldComponentUpdate conditions that limit needless re-rendering and not break the code is **very challenging**

### Future
* More emotional chatbot profiles!
* For practical/innovative use cases [here](https://keyreply.com/botspeak/). I particularly liked IKEA Bot
------

## Credit
This is a proof-of-concept project and naturally all contributions are welcome.

### Contributors
* Raymond Aung Pyae Sone, GA Full-stack Developer
* Seth Loh Wei Chen, GA Full-stack Developer

### Acknowledgements
* We are incredibly thankful to the developer [LucasBassetti](https://github.com/LucasBassetti) for giving us helpful pointers along the way since this was our first React project and graciously allowed us to use his base codes.
* [Yi Sheng](https://github.com/yisheng90) for the useful guidance
* [Sharona](https://github.com/sharona1610) for the ERD advice
* [Prima](https://github.com/primaulia) for the massive amount of patience and debugging help!
* All of GA coursemates for being supportive and the good humour

### Image credits:
* [Images](https://unsplash.com/@halgatewood
