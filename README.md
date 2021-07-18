<h1 align="center" style="border: none !important">Knot<br></h1>
<p align="center">✨ The Open Source URL Shortner ✨</p>

<div align="center">
 
![Build Status](https://badgen.net/apm/license/linter)
![JS version](https://badgen.net/dub/stars/silly)
[![Twitter](https://img.shields.io/twitter/url.svg?url=https%3A%2F%2Ftwitter.com%2Fct_tricks&style=social&label=Follow%20%40ct_tricks)](https://twitter.com/ct_tricks)

</div>
A very simple URL shortener made by using Google Form & Spreadsheet as a backend to store and get URL and data. Knot never logs the number of times a URL gets a request or anything. It simply shorts the long URL and stores data in a spreadsheet using google form. It is made just for experimental and educational purposes.

### How it works?
In the main landing pagae, there are two inputs. 1st Alias and 2nd Long URL. Here i am using `google form` to store the recored in `google spreadsheet` when a new request is made on `index.html` page. As this is a custom HTML form ( if you don't know how to setup custom html form <a href="https://youtu.be/WevO_PDB7E0" target="_blank">watch this tutorial video</a> ). In this form when a user enter/change alice it get stored in localstorage of browser using.  Now once the form is submitted successfully it redirects users to `shorted.html` page. Here when a user arrives it display the shorted url ( simply by adding alias value at the end of the url). 

```javascript
var sourceUrl = "https://cttricks.github.com/knot/load.html?sl=" + localStorage.getItem("alias");

//Example : https://cttricks.github.com/knot/load.html?sl=tanish
```

Now when a user visit the shorted url i.e `load.html` page, with the `sl` value. It make a `GET` request on google spreadsheet with `SQL query` in the request url.
`Query : SELECT B WHERE C ='" + page.searchParams.get("sl") + "'"`
```javascript

const baseID = "Spreadsheet_ID";
const baseName = "Sheet1";
const page = new URL(window.location.href);

var url = "https://docs.google.com/spreadsheets/d/"+baseID+"/gviz/tq?tqx=out:json&sheet="+baseName+"&tq=" + encodeURIComponent("SELECT B WHERE C ='" + page.searchParams.get("sl") + "'");

```
On response it parse the response text, and loads the long url in the same tab. 

### Create your own
Download the files of this repo and upload it to the hosting server. And follow these simple steps.
- Create a new <a href="http://forms.google.com/" target="_blank">google form</a>
- Create two fileds, 1st Alias and 2nd Long URL
- Now get the `entry.codes` of these two fileds. ( you can easily get it by creating a prefilled link )
- On response section you'll get an option to add response sheet. Click on that, it'll open a spreadhseet for you. Here on the top right corner click on share and set permission to anyone with link can view.
- Open `index.html` and upadted the `form action url` and `entry.code` with yours
- Open `shorted.html` and upadted the default shortened link `https://cttricks.github.io/knot/load.html?sl=` with your domain and path to this file.
- Open `load.html` and update the `baseID` and `baseName` (baseName = sheetname)

All done, Now test your own `Knot` version of URL shortner.

### 🎯 Why i'm building this ?
Long ago i made a tutorial on <a href="https://youtu.be/WevO_PDB7E0" target="_blank">how to store custom from data to google spreadsheet using google form</a>. And as we all know, Google Spreadsheet is a very powerful tool and there is an option to query and get data using export method with SQL querys. So i mixed this two thing togather and made this url shortner ( Just as an experiment ) using Google Forms and Spreadsheet. It is not a complete solution. But yeah! Anyone can use this in their small/big projects at their own risk. 😄

⚠️ Use my version of knot only for testing.


### 📌 Important Links
- <a href="https://cttricks.github.io/knot/shorted.html" target="_blank">Knot Demo</a>
- Demo + Tutorial Video (NA)

Enjoy...!!


