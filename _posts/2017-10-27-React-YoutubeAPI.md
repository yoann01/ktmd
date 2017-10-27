---
layout: post
title: Making Requests to the YouTube API with React
tags: [React, Youtube]
categories:
- blog
---


Making Requests to the YouTube API with React
-------------

There is a neat little package that you can install into your React project that will make the whole searching process
a little easier. This fun little package is called **YTSearch** and it can be installed by running the following.

```sh
npm install YTSearch
```
Once installed, you will need to import this into your React project in the file where you’ll be making the calls.

```js
import YTSearch from 'youtube-api-search'
```

Now that the YTSearch package is installed, it’s easy to make a call to the YouTube API! All you have to do is 
call ```js YTSearch() ```, the search takes an argument in the form of an object including your API key and the search term. 
The callback function will be used to return the results and in the case below, it can be used to set the state.

```js
YTSearch({key: API_KEY, term: term}, (videos) => {
      this.setState({
        videos: videos,
        selectedVideo: videos[0]
       });
    });
```
