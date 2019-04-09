---
title: "Django SMTP Settings for Gmail"
date: 2017-12-18T18:21:50-05:00
draft: false
---

Django SMTP Settings for Gmail

```
EMAIL_USE_TLS = True
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_HOST_USER = '<<username>>@gmail.com' # your Gmail username
EMAIL_HOST_PASSWORD = 'xxxx' # your Gmail password
EMAIL_PORT = 587
DEFAULT_FROM_EMAIL = EMAIL_HOST_USER

```

And enable low security apps <a href="https://accounts.google.com/DisplayUnlockCaptcha">here</a>.
