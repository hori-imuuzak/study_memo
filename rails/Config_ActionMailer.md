# ActionMailer でメールを送信できるようにする

## とりあえず開発環境で

- config/environments/development.rb を編集

```
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

config.action_mailer.delivery_method = :smtp
config.action_mailer.smtp_settings = {
    address: 'smtp.gmail.com',
    port: 587,
    authentication: :plain,
    user_name: Rails.application.secrets.SMTP_EMAIL,
    password: Rails.application.secrets.SMTP_PASSWORD,
}
```

- SMTP_EMAIL / SMTP_PASSWORD を secretsに設定

```
EDITOR=nano rails secrets:edit
```

- メール送信処理は非同期で遅れるようにjob化する
