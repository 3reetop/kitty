# Kitty! by 3reetop
This is the front-end to an API that serves random pictures of my cat!

## How does it work?
You really wanna know? Well, okay, you asked for it. Here we go:

1. The entire API backend consists of a single Cloudflare Workers script that requests a JSON file from a private GitHub repository owned by me. This JSON file contains links to each image in a JSON array.
2. The API selects a random index from the array and gets that link.
3. The API makes an HTTP request to fetch the image hosted at that link.
4. The API returns the raw image data for that image. Like, the actual image binary data.
5. All of the above only happens when you make a properly-authenticated GET request to the API.
6. The API also has an endpoint that lets me make sure it's alive.
7. This front-end makes 2 GET requests, one to get the raw image data and the other to the ping endpoint using 2 XMLHttpRequest instances
8. It takes the raw image data once the API returns it, and it encodes it into a Base64 string in your browser. (I know!)
9. It takes the response from the ping endpoint and based on the HTTP status code changes the content of the text on screen.
10. The Base64 string gets inserted into a data URI and that data URI gets set as the source of an HTML `<img>` element.

Oh and the front-end is styled using Bootstrap, for anyone who was curious.

This whole process gets repeated whenever you refresh the page. The button at the bottom simply refreshes the page using JavaScript by calling `window.location.reload()`.

## That sounds like terrible design.
It most likely is, but I just wanted to have a nice little thing to honor my pet kitty. I love him so much.

## What's your cat's name?
We never named him, we've been calling him "Kitty" ever since he came to us and he got used to it fairly quickly actually.

## Who's the person holding him in some of the pictures.
That's my brother. Yes, I did get consent from him before making his likeness public on the Internet.

## How long did this take to make?
Around 3 hours.

## Why does the API require authentication, and why did you make the authentication token public?
I host the entire API backend on 1 Cloudflare Workers script. I use the Workers Free plan, meaning I don't have to pay to run Workers. However, the Free plan comes with the limit that your Worker only encounters 100,000 requests per month. Once you reach this limit, your Workers script goes offline and cannot process any more requests for that month.

In order to prevent spammers from spamming my API, I decided to implement authentication. Sure, you can find the authentication token very easily. It was never meant to be private. However, it's my futile attempt at stopping spammers from using up my 100,000 request quota from the month. Eh, it's still better than not having any authentication at all.
