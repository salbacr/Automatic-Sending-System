# Automatic-Sending-System

import smtplib
from email.mime.text import MIMEText
from email.header import Header

def send_email_alert(subject, content):
    sender = 'Sendding@gmail.com'       # Replace with your Gmail address
    receiver = 'Receving@example.com'   # Replace with the receiving email address
    password = 'YourAppPassword'        # Replace with the 'App Password' for Gmail

    msg = MIMEText(content, 'plain', 'utf-8')
    msg['From'] = sender
    msg['To'] = receiver
    msg['Subject'] = Header(subject, 'utf-8')

    try:
        smtp = smtplib.SMTP('smtp.gmail.com', 587)
        smtp.starttls()
        smtp.login(sender, password)
        smtp.sendmail(sender, [receiver], msg.as_string())
        smtp.quit()
        print("✅ Email has been sent")
    except Exception as e:
        print("❌ Email sending failed:", e)
