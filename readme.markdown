# awesomeCloud - jQuery Plugin

The awesomeCloud plugin creates a word cloud using the HTML5 `canvas` element, using a wordlist that exists on your page.

## Requirements

* jQuery 1.7+
* browser that supports the `canvas` element

## Usage

	$( "#wordCloudContainer" ).awesomeCloud( settings );

awesomeCloud assumes that each child of the container is an HTML element with a `data-weight` attribute containing an integer or decimal value that reflects it's "weight", and the content of the element is the word. For example, `<span data-weight="12">first</span>` is a valid child.

## Settings

	"size" : {
		"grid" : 8, // word spacing, smaller is more tightly packed
		"factor" : 0, // font resize factor, 0 means automatic
		"normalize" : true // reduces outliers for more attractive output
	},
	"color" : {
		"background" : "rgba(255,255,255,0)", // background color, transparent by default
		"start" : "#20f", // color of the smallest font, if options.color = "gradient""
		"end" : "rgb(200,0,0)" // color of the largest font, if options.color = "gradient"
	},
	"options" : {
		"color" : "gradient", // if "random-light" or "random-dark", color.start and color.end are ignored
		"rotationRatio" : 0.3, // 0 is all horizontal, 1 is all vertical
		"printMultiplier" : 1, // set to 3 for nice printer output; higher numbers take longer
		"sort" : "highest" // "highest" to show big words first, "lowest" to do small words first, "random" to not care
	},
	"font" : "Helvetica, Arial, sans-serif", // the CSS font-family string
	"shape" : "circle" // the selected shape keyword, or a theta function describing a shape

## Example

	<div id="wordcloud" style="border:1px solid #f00;height:150px;width:150px;">
		<span data-weight="14">word</span>
		<span data-weight="5">another</span>
		<span data-weight="7">things</span>
		<span data-weight="23">super</span>
		<span data-weight="10">cloud</span>
	</div>
	<script>
		var settings = {
			"size" : {
				"grid" : 16
			},
			"options" : {
				"color" : "random-dark",
				"printMultiplier" : 3
			},
			"font" : "Futura, Helvetica, sans-serif",
			"shape" : "square"
		}
		$( "#wordcloud" ).awesomeCloud( settings );
	</script>

## Notes

AwesomeCloud uses the HTML5 canvas element to create word clouds similar to [http://wordle.net/](http://wordle.net/). It may or may not work for you.

If your words are all fairly evenly weighted and are large compared to the containing element, you may need to adjust the size.grid setting to make the output more attractive. Conversely, you can adjust the size.factor setting instead.

It should be noted that the more words you have, the smaller the size.grid, and the larger the options.printMultiplier, the longer it will take to generate and display the word cloud.

## Extra Thanks

Without Timothy Chien's work ([https://github.com/timdream/wordcloud](https://github.com/timdream/wordcloud)), this plugin would have taken much longer and been much uglier. Fate smiled and I found his version while I was searching out the equations I needed to make a circle-shaped cloud. I've simplified and, in places, dumbified his code for this plugin, and even outright copied chunks of it since those parts just worked far better than what I had originally written. Many thanks, Timothy, for saving some of my wits, sanity and hair over the past week.

Thanks to http://www.websanova.com/tutorials/jquery/jquery-plugin-development-boilerplate for providing a great boilerplate I could use for my first jQuery plugin. My original layout worked, but this one was much better.
