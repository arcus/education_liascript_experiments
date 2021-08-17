<!--

author:   Joy Payton

email:    paytonk@chop.edu

version:  0.0.1

language: en

narrator: US English Female

comment:  Short description here

script:   https://code.jquery.com/jquery-3.6.0.slim.min.js

@onload
(function($) {

  // Get the .gif images from the "data-alt".
	var getGif = function() {
		var gif = [];
		$('img').each(function() {
			var data = $(this).data('alt');
			gif.push(data);
		});
		return gif;
	}

	var gif = getGif();

	// Preload all the gif images.
	var image = [];

	$.each(gif, function(index) {
		image[index]     = new Image();
		image[index].src = gif[index];
	});

	// Change the image to .gif when clicked and vice versa.
	$('figure').on('click', function() {

		var $this   = $(this),
				$index  = $this.index(),

				$img    = $this.children('img'),
				$imgSrc = $img.attr('src'),
				$imgAlt = $img.attr('data-alt'),
				$imgExt = $imgAlt.split('.');

		if($imgExt[1] === 'gif') {
			$img.attr('src', $img.data('alt')).attr('data-alt', $imgSrc);
		} else {
			$img.attr('src', $imgAlt).attr('data-alt', $img.data('alt'));
		}

		// Add play class to help with the styling.
		$this.toggleClass('play');

	});

})(jQuery);
@end
-->

# Let's check out an animated gif

<figure>
  <img src="https://raw.githubusercontent.com/arcus/education_liascript_experiments/main/img/r_console.png" height="500" width="800" alt="Static Image" data-alt="https://raw.githubusercontent.com/arcus/education_liascript_experiments/main/img/r_console.gif">
</figure>

**Click to start / restart playback of video**

# This was a bit of a pain to figure out

But now I think I can show folks how to do it?  

* A few weird javascript things...
* Some troubleshooting experiences from my webdev days...
* AWS got in there...
