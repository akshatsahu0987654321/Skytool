# Local Panel OTP Patch

This patch keeps your signup flow using `mail_provider="worker"` but lets the worker provider call the fast local iCloud-HME panel endpoint directly.

Use this config in your signup request/config:

```json
{
  "mail_provider": "worker",
  "email_logs_url": "http://127.0.0.1:5050/api/accounts/acc_288b5620/mail",
  "email_api_key": ""
}
```

The provider will call:

```text
http://127.0.0.1:5050/api/accounts/acc_288b5620/mail/<alias@icloud.com>?limit=20&days=1
```

It also still supports the old route:

```text
http://127.0.0.1:5050/logs?mail=<alias@icloud.com>
```

Install:

```bat
copy /Y mail_providers.py "PATH_TO_YOUR_SIGNUP_PROJECT\mail_providers.py"
python -m py_compile mail_providers.py
```
