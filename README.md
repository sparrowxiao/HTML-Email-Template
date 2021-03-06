# [![Build Status](https://img.shields.io/travis/fatih/color.svg?style=flat-square)](https://travis-ci.org/fatih/color)

## This template includes
- [x] Full width image (responsible UX)
- [x] Two columns layout (responsible UX)
- [x] Three columns layout (hybrid UX)
- [x] Bulletproof buttons style
- [x] Send email automatically 
- [x] Test email with Jenkins

## Screenshot of this HTML email template
![screencapture-file-Users-ting-Downloads-HTML-Email-Template-master-2-01-standard-template-html-2019-05-17-14_48_24](https://user-images.githubusercontent.com/2945947/57949920-bbfe6000-78b3-11e9-8aeb-2e471404f9de.png)

## HTML Email Troubleshooting
1. - [x] don't be panic first, deeply breath and go through this bug check list and check some useful notes here. 

   - [ ] Couldn't achieve the responsible font size on different screen.<br/>Check the image added in the email template, sometimes the image increase the max-width of the template and the email client cannot do the media requirement correctly.

2. #### Special Issues on Outlook
  - [x] Outlook2007-2016 on Windows 7 the bullet indent is not right.<br/>  Using the inline sytle mso-special-format:bullet can fix it.
  - [x] Outlook2007-2013 on Windows(7-10) Image shown up in real size. For example if the header image is 1180x400, then this image will break the max-width of the mail 600 px. <br/>
  Using the right size of the image is important while creating the email HTML.
  - [ ] Outlook2007-2013 on Windows(7-10) some copy has been cut off.

3. #### Special Issues on Pardot
  - [x] Pardot render all the http or https link into the track link for analysis in its platform. So in order to avoid the webfont links treated as track link just put it in <style> tag.

## SendEmail service on MacOS
- [x] I personally don't like the test email feature from Pardot, since it is too too slow, local server might be pretty fast. Use command line here can make life much easier. Here is my try, installed SendEmail service on MacOS.

```
brew SendEmail
```

> /usr/local/Cellar/sendemail/1.56/bin/sendEmail -f yoursender@gmail.com -t yourRecipient@gmail.com < youttestemail.html -s smtp.gmail.com:587 -xu youraccount@gmail.com -xp password

- [x] Jenkins pipeline service is perfect to test the created template on your own email client, and the speed is extreamly fast. 
If you never use it before, you can follow [this post](https://medium.com/@gustavo.guss/jenkins-sending-email-on-post-build-938b236545d2) to configure the Jenkins Email plugins, then create the pipeline and configure it as the screenshot, then add the script to the pipeline part and build it.

## Email Test with Jenkins pipeline settings
![screencapture-file-Jenkins-pipeline-settings](https://user-images.githubusercontent.com/2945947/58354564-de5a2580-7e3f-11e9-818a-a38afcef1464.png)

```
pipeline {
   agent any
    stages {
        stage('clone repo and clean it'){
            steps{
                sh "rm -rf HTML-Email-Template"
                sh "git clone https://github.com/sparrowxiao/HTML-Email-Template.git"
            }
        }
        stage('Ok') {
            steps {
                echo "Ok"
            }
        }
    }
    post {
        always {
            emailext mimeType: 'text/html', 
            body: '${FILE,path="/Users/Shared/Jenkins/Home/workspace/send-test-email/HTML-Email-Template/01-standard-template.html"}', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'
        }
    }
  
}
```

## **Good Marketing Email Service**

   - [Litmus](https://litmus.com): I like their email render feature
  
   - [Campaign Monitor](https://www.campaignmonitor.com): I like their resource section


