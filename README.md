# Kitty! by 3reetop
This is the front-end to an API that serves random pictures of my cat!

## How does it work?
You really wanna know? Well, okay, you asked for it. Here we go:

1. The entire API backend consists of a single Cloudflare Workers script that requests a JSON file from a private GitHub repository owned by me. This JSON file contains links to each image in a JSON array.
2. The API selects a random index from the array and gets that link.
3. The API makes an HTTP request to fetch the image hosted at that link.
4. The API returns the raw image data for that image. Like, the actual image binary data.
5. All of the above only happens when you make a properly-authenticated GET request to the API.
6. This front-end makes that GET request, and takes the raw image data that the API returns and encodes it into Base64 in the browser.
7. The Base64 string is rendered onto the page via an HTML `<img>` element.

## That sounds like terrible design.
It most likely is, but I just wanted to have a nice little thing to honor my pet kitty. I love him so much.

## What's your cat's name?
We never named him, we've been calling him "Kitty" ever since he came to us and he got used to it fairly quickly actually.

## Who's the person holding him in some of the pictures.
That's my brother. Yes, I did get consent from him before making his likeness public on the Internet.

## How long did this take to make?
Around 3 hours.
