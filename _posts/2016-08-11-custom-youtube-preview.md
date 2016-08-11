---
datePublished: '2016-08-11T17:30:31.365Z'
sourcePath: _posts/2016-08-11-custom-youtube-preview.md
author: []
via: {}
dateModified: '2016-08-11T17:30:31.017Z'
title: Custom YouTube Preview
publisher: {}
description: >-
  This post shows how to use a custom image (or any element) for your YouTube
  video preview. This method also potentially speeds up the initial page load.
starred: false
inFeed: true
hasPage: false
inNav: false
_type: MediaObject

---
# Custom YouTube Preview

This post shows how to use a custom image (or any element) for your YouTube video preview. This method also potentially speeds up the initial page load.

This example uses a custom image in place of the regular YouTube embedded iFrame. When you click the image, some Javascript swaps out the image for the actual video and it starts playing. You could do this with any element, not just an image. I also recommend using [FitVids][0] for perfectly responsive video.

Since nothing from YouTube is loaded until the user actually clicks the image, you might even see an increase in the initial page load speed. And if the user never clicks the image, you've saved them the trouble of loading data they didn't need.

\`\`\`javascript  
/\*\*  
\* Load a YouTube video after clicking a thumbnail. Use like so:  
\* <img id="youtubeid" onclick="playYouTubeVideo(this)" src="thumbnail.jpg"\>  
\*/  
function playYouTubeVideo(element) {  
// Create an iFrame with autoplay set to true so it starts as soon as we insert it.  
var iframe = document.createElement('iframe');  
iframe.setAttribute('src', 'https://www.youtube.com/embed/' + element.id + '?autoplay=1&autohide=1&showinfo=0&modestbranding=1');  
// Replace the thumbnail with YouTube player.  
var parent = element.parentNode;  
parent.replaceChild(iframe, element);  
// I recommended using FitVids after inserting the iFrame if responsive video is needed.  
jQuery(parent).fitVids();  
}  
\`\`\`

[0]: http://fitvidsjs.com/