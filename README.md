
#  Statistical Modelling with Python Project
Project for program at Lighthouse Labs. Worked on in October 2024. <br>
Click [here](https://prezi.com/view/g5epficHVM2q1VTXrAiq/) to see the prestation that goes with!
  

##  Project/Goals
Listed in no particular order

 - To test my new skills in python!
 - Find if there is a relationship between how many bike slots  there are at a bike station in Glasgow, Scotland and the ratings of locations (bars, pubs, restaurants, and even dog parks!) within 1000m of them.
 - Compare how different APIs that store similar data function  

##  Process

  

${\color{red} Note!}$  <br>Every time data is pulled from an API, it gets saved first as a JSON, then after parsing and some data cleaning, as a CSV.  Take a look in the data folder to see them!

 - APIs
	 - Review API documentation for each API I planned to use
	 - Tested calls on smaller subsections of the data I was planning on using
	 - Called the full amount of data once preparations had been complete for cleaning and sorting data
 - Data Cleaning
	 - Parsed subsections of data to weed out bugs with parser code
	 - Created cleaning functions
	 - Ran full datasets through parser and cleaning functions
 - Data Exploration
	 - Explored each data set separately and then together in both dataframes form and via charts
 - Regression Model Building
	 - Created a single linear regression visual model
	 - Ran a single linear regression model 
  

##  Results

### API Comparison
In this project I explored two APIs that gave business data such as location, ratings, contact information, etc. Once I had the results, and cleaned them, from both APIs I took a moment to compare them. In the tables below you can see some example data from each API.
#### *Yelp*
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>name</th>
      <th>bar</th>
      <th>dog_park</th>
      <th>restaurant</th>
      <th>distance</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>rating</th>
      <th>station_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>c2fwMshDF0wtCKGLe3IGtw</td>
      <td>Dukes</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>838.518390</td>
      <td>55.866966</td>
      <td>-4.292194</td>
      <td>4.4</td>
      <td>066c99293af108ece27d9b0436c30cc4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>qjjmYSR3CVsJlr75vyIEBg</td>
      <td>BrewDog Glasgow</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>871.079804</td>
      <td>55.867702</td>
      <td>-4.291878</td>
      <td>4.3</td>
      <td>066c99293af108ece27d9b0436c30cc4</td>
    </tr>
  </tbody>
</table>
</div>

### *Foursquare*
<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>name</th>
      <th>bar</th>
      <th>dog_park</th>
      <th>restaurant</th>
      <th>distance</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>rating</th>
      <th>station_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4e1c4c481fc714dc5c3143ed</td>
      <td>BrewDog Glasgow</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>884</td>
      <td>55.868325</td>
      <td>-4.292289</td>
      <td>None</td>
      <td>066c99293af108ece27d9b0436c30cc4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4b7b007cf964a5205b4b2fe3</td>
      <td>Mother India's Cafe</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>931</td>
      <td>55.867287</td>
      <td>-4.291100</td>
      <td>None</td>
      <td>066c99293af108ece27d9b0436c30cc4</td>
    </tr>
  </tbody>
</table>
</div>

I noticed that while I was expecting both to have extremely similar results, *Yelp* had more accurate distances  as well as ratings.  *Foursquare* missing ratings meant any locations *Yelp* didn't have in there database would show up in my data, but not have a rating. In the example about you can see "*BrewDog Glasgow*" appears in both tables, *Yelp* with a rating and a more details distance and *Foursquare* without a rating and a rounded up distance.

### Bike Stations Slots and Locations around them and their ratings
When I first saw *CityBikes*'s API returned how many bike slots were at each station, I immediately assumed the stations with more locations and/or locations with higher ratings would have more slots. More people would need bikes, right? I caught myself as I was dismissing that question. This was the perfect chance to test my assumption!
I started with looking at the density of locations around each bike station, but quickly noticed there was a high number of stations in the downtown area, meaning there was a lot more people using those stations that just the locations I looked for. This is when I knew I either needed to dig into the population density and building types in the downtown area or pull back and reassess the direction I was going in. As this is a project for school, and has a tight turn around, I chose to reassess.

<a href="https://ibb.co/BrjBCV2"><img src="https://i.ibb.co/wwC4zNh/Glasgow-heatmap.png" alt="Glasgow-heatmap" border="0"></a>

> Heatmap showing location density and bike station locations. Look in
> the joining data notebook for an interactive map!

Now that I took a step and took a new look at the assumption I had made, I pivoted my question. Does having more bike slots in nearby bike stations mean the rating of locations would be higher? There's more access to the locations form the bikes so that became my new question. I decided to do a single linear regression as I knew there were many variables at play, but was mainly curious about this one in particular. 

<a href="https://imgbb.com/"><img src="https://i.ibb.co/WKXTx8F/Linear-Regression-Graph.png" alt="Linear-Regression-Graph" border="0"></a>

> Single Linear Regression Graph

  I won't bore you with every detailed step I went through, if you want to know more please take a look at my notebooks! The surprising (to me!) result is that the **more** bike slots a station has, the **lower** the ratings tend to be. There is clearly more at play here, but this was an interesting discovering.

##  Challenges

- Reading API documentation... if there was any
	- I found both *Yelp*'s and *Foursquare*'s list of categories tricky to find as well as *Yelp*'s API key needed "Bearer" before it
- API call limits
	- I lost almost a full day or work time due to *Yelp*'s 300 a day limit.
- Making a heatmap of Glasgow
	- I had to quickly learn a new python library,  *folium*,  to create it. 

  

##  Future Goals

 1. Explore the effect some of the other *CityBikes*'s data has on the ratings of nearby locations. Changing my Single Linear Regression to a Multiple Linear Regression
 2. Explore other location categories in relation to the number of bike slots at stations. Schools? Rec centres?
 3. Better code comments and optimizing code

  

##  Resources Used

CityBikes API - https://citybik.es <br>
Yelp Fusion  <br>
Foursquare <br>
