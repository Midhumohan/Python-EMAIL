# Python-EMAIL: 

```bash

import smtplib
import email.message


USERNAME = 'Sender.example.com@gmail.com'
PASSWORD = 'password'


report = email.message.EmailMessage()

report['From'] = USERNAME
report['Subject'] = 'Track of every registered user on the server'
report['To'] = [ 'recipient1.example.com@gmail.com' , 'recipient2.example.com@gmail.com', 'recipient3.example.com@gmail.com' ]

with open('/etc/passwd','r') as fh:
  data = fh.read()
  
report.add_attachment(data,subtype='text',filename='attach.txt')

with smtplib.SMTP_SSL('smtp.gmail.com',465) as smtp:
  smtp.login(USERNAME,PASSWORD)
  smtp.send_message(report)


```

## smtplib

Python provides smtplib module, which defines an SMTP client session object that can be used to send mail to any Internet machine with an SMTP or ESMTP listener daemon.


## email.message.EmailMessage()

The central class in the email package is the EmailMessage class, imported from the email.message module. It is the base class for the email object model. EmailMessage provides the core functionality for setting and querying header fields, for accessing message bodies, and for creating or modifying structured messages.

## To attach the file /etc/passwd with the mail

```bash

with open('/etc/passwd','r') as fh:
  data = fh.read()
  
report.add_attachment(data,subtype='text',filename='atach.txt')

```


