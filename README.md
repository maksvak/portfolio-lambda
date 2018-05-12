# portfolio-lambda
This folder contains select code and an explanation on how my website (mavtech.io) is built.

This website is static. It is hosted out of an s3 bucket. I have a private repository on GitHub that I use to make changes to it.

This website is meant to demonstrate skill with a variety of components. Lets go through the structure of the site now.

From my person computer I upload files to GitHub. Everytime a modification is detected by GitHub it triggers an AWS Codebuild event.
Codebuild is responsible for rebuilding all of my Node.js code and getting it update to push to the web. I use NPM, webpack, Babel, and Jest,
for development and testing. Once Codebuild has completed, CodePipeline takes over, triggering an AWS Lambda function included in this repo.
The Lambda function has 2 purposes. The first is it deploys all my code to the S3 bucket I am doing the web hosting from, as well as posting
to a SNS topic to let me know when it has completed successfully.

Once the code is hosted in the right S3 bucket, CloudFront takes over. Using a domain hosted by AWS Route53, I am able to distribute my website all over
the world. The website itself takes advantage of a React framework in order to make these cool modal popups. HTML and CSS take care of the rest of it. 
