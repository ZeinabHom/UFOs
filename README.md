# UFO!

The purpose of this project is to prepare one HTML page that show article about UFO and also user can filter the data table based on below items:
 - Datetime /State / City / Country /Shape
 
This project use 4 files as follows;
 - Data.js
 - HTML
 - Java Script
 - CSS

## Data.js
this project data was saved as js format in this file. It includes different objects with dictionary format.

## HTML
HTML file displays  visual of our final project. it is  prepared based on a storyboard. It has different parts includes;
 - Navigation bar 
 - Header Page
 - Article and its paragraph  
 - Filter tables
 - Table

## app.js
This file includes functions to run filters and tables

## CSS
This CSS file helps us to make more attractive our page.

# HTML
At first part of HTML file in <head> tag, we have 2 links. One of them is  bootstrap and other is CSS (these two links are same as import in python).For designing the page the grid system is used so we have <div> tags with class=containers. Each grid system has 12 columns; i 4 columns for article header part and 8 columns for article's paragraph are chosen.
Filter table has 3 columns out of 12 columns of gride system, for each filter <li> tag is defined and <lable> and <input> tags are written in <li>tag.
9 columns as data table is created .<table> tag includes <thead> and <tbody> tags.
End part of HTML file, before closing <body>tag; java script file was imported with <script>tags. They include d3, and data.js and app.js.

# APP.JS
This java script file includes 3 functions as follows;

 - buildTable
 - updateFilters
 - filterTable

Table of data is displayed by function buildTable;
 -   	function buildTable(data) {
		 tbody.html(""); 
		 data.forEach((dataRow) => {
		let row = tbody.append("tr");	
		Object.values(dataRow).forEach((val) => {
		let cell = row.append("td");
		cell.text(val);});});}

filter tables is prepared by function function updateFilters;

 -     function updateFilters() {
		let changedElement = d3.select(this);
		let elementValue = changedElement.property("value");
		console.log(elementValue)
		let filterId = changedElement.attr("id");
		console.log(filterId)
		if (elementValue) {
		filters[filterId] = elementValue;}
		else { delete filters[filterId];}
		console.log(filters);
		filterTable();}

when user user filter table, filtered data should be show in a table. FilterTable funtion prepared that table;

	 function filterTable() {
	 var filteredData = tableData;
	 Object.entries(filters).forEach(([key, value]) => {
	 filteredData = filteredData.filter(row => row[key] === value);});
	 buildTable(filteredData);}

we add the below code after all functions to determine event for our page - event in this page is change(type in filter table).

	 d3.selectAll("input").on("change",updateFilters);
	
# CSS
The below codes make light font color and also add background image in jumbotron part of our page with center text in it.

	 - body { color: #f7f7f7;}
	 .jumbotron {
	 background-image: url("../images/nasa.jpg");
	 background-size: 100%  100%;
	 text-align: center;}
