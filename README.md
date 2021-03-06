# estimated-read-time

[![NPM](https://img.shields.io/npm/v/estimated-read-time.svg?logo=npm&style=flat-square)](https://www.npmjs.com/package/estimated-read-time)    [![Github](https://img.shields.io/github/release/karthik512/estimated-read-time.svg?colorB=orange&logo=github&style=flat-square)](https://github.com/karthik512/estimated-read-time) [![Downloads](https://img.shields.io/npm/dt/estimated-read-time.svg?logo=npm&style=flat-square)](https://www.npmjs.com/package/estimated-read-time) [![License](https://img.shields.io/github/license/karthik512/estimated-read-time.svg?style=flat-square&logo=github)](https://github.com/karthik512/estimated-read-time/blob/master/LICENSE)


`estimated-read-time` helps to estimate the time taken to read a content.

## Features

  1. Estimates the time taken to read any plain text content.
  2. Reduces the avg. reading WPM for a technical document based on its difficulty level.
  3. Calculate avg. WPM from previous total words and seconds. ([Tip #1](https://github.com/karthik512/estimated-read-time#tips))

## Installation

```sh
npm install estimated-read-time --save
```

## Usage

```javascript
var readtime = require('estimated-read-time');

var result = readtime.text(content);
//Returns
//{
//  word_count: 265
//  seconds: 60
//}
```

## API

`text(content, options)`

  - `content`: the text to analyze
  - `options.MIN_WORD_LEN`: Avg Length of one word which will be used to count the no. of words in the content. <b>(Default: 4)</b>
  - `options.WPM`: Words Per Minute a person can read. <b>(Default: 265)</b>
  - `options.IS_TECHNICAL_DOC`: true or false indicating whether the content is a technical document. <b>(Default: false)</b>
  - `options.TECH_DIFFICULTY`: The Technical Difficulty of the content. Allowed values are <b>0 to 5</b>. <b>(Default: 3)</b>
  - `options.TOTAL_WORDS`: Total Words read <b>(Default: 0)</b>
  - `options.TOTAL_SECONDS`: Total Seconds taken to read `options.TOTAL_WORDS`. <b>(Default: 0)</b>
  
  <b>Note</b>:
    The WPM calculated using `options.TOTAL_WORDS` and `options.TOTAL_SECONDS` takes higher precedence than `options.WPM`.
    
 ## Tips
 
  1. If you want to show the estimated reading time differently for each user based on their previous reading, then you can store the total words read by the user and the total seconds taken to read and pass them in `options.TOTAL_WORDS` and `options.TOTAL_SECONDS`.