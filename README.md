# Personal Website
* I'll use Jekyll, since I like its decoupling of things and its easy way of including extra pages. Also, I like how [Tanuki](https://tanuki.ai) turned out.
## Installation
* [Install Jekyll](https://jekyllrb.com/docs/installation/)
* Install ruby-dev: `sudo apt-get install ruby-dev`
* Install [rbenv](https://github.com/rbenv/rbenv#installation) and use [Ruby v2](https://talk.jekyllrb.com/t/error-no-implicit-conversion-of-hash-into-integer/5890)
    * `rbenv install --list`
* Initialize the Ruby virtual environment: `rbenv init`. A new bundler will need to be installed for this version of Ruby: `gem install bundler`.
* [Install the Gems](https://jekyllrb.com/docs/step-by-step/01-setup/)
* Install [jEnv](http://www.jenv.be/) for a local, old version of Java.
* Add a compatible version of Java:
```bash
sudo apt install openjdk-8-jdk
echo "Looking for a version of Java 8 − where is it?"
update-java-alternatives --list
echo "Pick a destination for the next command…"
jenv add /usr/lib/jvm/java-1.8.0-openjdk-amd64
```
* Install Bower: `npm install -g bower`
* Install the JavaScript dependencies specified in [bower.json](./bower.json): `bower install`.

## Running
```bash
rbenv init
eval "$(jenv init -)"
bundle exec jekyll build
bundle exec jekyll serve
```
## Pushing Changes
* Check the settings in [s3_website.yml](/s3_website.yml)
* Initialize the Ruby virtual environment: `rbenv init`
* Enable a locally isolated version of Java: `eval "$(jenv init -)"`
* Set a compatible version of Java: `jenv shell 1.8`
* Push: `s3_website push`
* Visit the bucket's page in the S3 console. Visit the properties and enable bucket hosting for the website.
* Set the bucket policy to public.
* Check the S3 website before publishing it to your own domain. There might still be some internal references to `localhost`, which will result in [404s](https://en.wikipedia.org/wiki/HTTP_404).
* Change the DNS records with your actual DNS provider. Note that [Route 53](https://console.aws.amazon.com/route53/home) is happy to hold DNS records even if it isn't your actual provider.
* For CloudFront's origins, enter the URL of the S3 website; don't select their S3 choice from the suggested list. Also, don't restrict bucket access, else people will strictly be required to visit eg `/about/index.html` rather than eg `/about`.
* The changes will first be visible at <http://owen.engineer.s3-website-us-east-1.amazonaws.com/>, before propagating through CloudFront to https://owen.engineer, once you invalidate its cache.
* Maybe [ask Google to re-analyse the sitemap](https://search.google.com/search-console/sitemaps?resource_id=sc-domain%3Aowen.engineer).

## Future
* Animating face upon hover
* Gif for face
