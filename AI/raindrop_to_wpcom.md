# Raindrop.io to WordPress.com

A simple Serverless function to post my weekly bookmarks from Raindrop.io to my Wordpress.com blog.

## Installation

- Clone this repository to your local machine
- Install dependencies
    - `npm install serverless -g``
- Copy `config.example.json` to `config.json`
- Change `raindropToken` to your Raindrop.io token
- Change `raindropCollection` to the ID of the collection you want to post from (you can get this from the URL)
- Change `wpToken` to your WordPress.com token and `wpSite` to your WordPress.com site name
- Deploy using `sls deploy`

The moment the function is run can be changed in `serverless.yml`. 

