# Individueel Project ID
The data I am going to use is about victims of hacking. I have data about the amount of hacking in years and ages. I want to show you how many people are victim of cybercrime. Sort by age, kind of crime and declare.

## Barchart
First I am going to show a barchart about how many people are victims of hacking. The data is sort by ages.

## Linechart
What I will show in this graph is the kind of crimes that were committed. I will show the data from 2012 till 2014. You can see the data is reduced.
The data I am going to use is about every crime in percent. 
- Broke in computer
- Broke in e-mail account
- Broke in on website/social media
- Hacking total
- Others

## Grouped barchart
I will show the amount of notifications and the declarations of each province in the Netherlands and the big difference between the numbers.


## Using charts
Barchart: https://bl.ocks.org/mbostock/3885304 [AFB BAR CHART]
At the x-axis I will put the ages, the y-axis will show the percentage. 

Linechart: http://bl.ocks.org/wdickerson/64535aff478e8a9fd9d9facccfef8929

Grouped barchart: https://bl.ocks.org/mbostock/3887051

## My changes of the barchart
At first I separated the HTML, CSS, Javascript and TSV. 
I linked everything in my HTML document. 
I gave my bar chart a title in a h1. 
Then I put my own data in the tsv file. 
I changed the margin, the font style and color of the bar chart. 
I have added: path, text and tick, to change their color to white. 	
	
I added a tooltip from: https://bl.ocks.org/alandunning/274bf248fd0f362d64674920e85c1eb7
I put the tooltip at the bottom of the js file

CSS
Deleted: .axis—x path {
  	display: none;
}

Added the toolTip property from CSS in the example.


JS
Added var toolTip in js, html and CS

Added at the bottom of the JS file from tooltip example:

g.selectAll(".bar")
      	.data(data)
      .enter().append("rect")
        .attr("x", function(d) { return x(d.area); })
        .attr("y", function(d) { return y(d.value); })
        .attr("width", x.bandwidth())
        .attr("height", function(d) { return height - y(d.value); })
        .attr("fill", function(d) { return colours(d.area); })
        .on("mousemove", function(d){
            tooltip
              .style("left", d3.event.pageX - 50 + "px")
              .style("top", d3.event.pageY - 70 + "px")
              .style("display", "inline-block")
              .html((frequency));
        })
    		.on("mouseout", function(d){ tooltip.style("display", "none");});


Changed all area to letter and all value to frecuency.

Deleted .bar in css and added rect and a fill plus hover.

I have added transition code from: https://bl.ocks.org/jamesleesaunders/f32a8817f7724b17b7f1

And put them next to each other. I looked in what order the lines had to stay. At first I added .attr("width", x.bandwidth())
        .attr("y", height)
        .attr("height", 0)
        .transition()
        .duration(1000)
        .delay(100)

Then, I put .attr("y", function(d) { return y(d.frequency); }) 

After this I had an error: Uncaught Error: unknown type: mousemove.
I googled the problem that my mouseover doesn’t work anymore and found this site https://stackoverflow.com/questions/22645162/d3-when-i-add-a-transition-my-mouseover-stops-working-why

Then I separated the parts transition and mouseover. The error was gone.

At last I added var colours = d3.scaleOrdinal()
   .range([“#4ebc1b"]); from: https://bl.ocks.org/alandunning/274bf248fd0f362d64674920e85c1eb7

I deleted the .bar and rect in css from before, they are unnecessary now.
 
I renamed frequency and letter.

## My changes of the line chart
Changed all const to var. I changed the data in the json file to my own. Then I changed the years on the x-axis on line 7 to 2012-2014. And the y-axis on line 8 to. 

I had a lot of errors: could not read population. And my tooltip was gone. I changed the data back to original and changed only the years to my data. It worked. 

I found out that the chart stops at 2010 somewhere in de code. It’s about this piece of code:

function drawTooltip() {
  const year = Math.floor((x.invert(d3.mouse(tipBox.node())[0]) + 5) / 10) * 10;
  
  states.sort((a, b) => {
    return b.history.find(h => h.year == year).population - a.history.find(h => h.year == year).population;
  })

Especially:  const year = Math.floor((x.invert(d3.mouse(tipBox.node())[0]) + 5) / 10) * 10;

With a lot of trying and change the numbers, I found out that the years can only be in steps of 10. It will show the years between but the tooltip will only show the years in steps of 10.

Then I styled the chart: font, color, position and changed the margin in the js file.

## My changes of the grouped barchart
I separated everything and made files. 
I put my own data in the csv file. 
Deleted the bars I didn’t need

I changed the CSS to my own style. Changed the colors of the bars in the js file. 
Changed the margin and the size of the svg in the html file

I deleted .attr("font-family", "sans-serif")
      .attr("font-size", 10)

## Sources of my data
[PDF file in map]
http://statline.cbs.nl/Statweb/publication/?DM=SLNL&PA=82465ned&D1=124-134&D2=0&D3=6-17&D4=l&VW=T

## License 
Released under the GNU General Public License, version 3. 
Released under the The MIT License. 

![Debug grafiek](preview.png)
