![screencapture-file-Users-ting-Library-Containers-com-apple-Safari-Data-Downloads-HTML-Email-Template-master-01-standard-template-html-2019-03-18-17_04_29](https://user-images.githubusercontent.com/2945947/54563641-1bb5b900-49a0-11e9-9b66-48292819a52c.png)
# HTML-Email-Template
Very Basic HTML Email Template
This template includes
- [x] full width image (responsible UX)
- [x] two columns layout (responsible UX)
- [x] three columns layout (responsible UX)

HTML Email Troubleshooting
- [x] don't be panic first, deeply breath and go through this bug check list after that.
- [ ] Couldn't achieve the responsible font size on different screen.<br/>Check the image added in the email template, sometimes the image increase the max-width of the template and the email client cannot do the media requirement correctly.

<span style="color:red;">Special Issues on Outlook</span>
- [x] Outlook2007-2016 on Windows 7 the bullet indent is not right.<br/>  Using the inline sytle mso-special-format:bullet can fix it.
- [x] Outlook2007-2013 on Windows(7-10) Image shown up in real size. For example if the header image is 1180x400, then this image will break the max-width of the mail 600 px. <br/>
  Using the right size of the image is important while creating the email HTML.
