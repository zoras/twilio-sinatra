* Clone the repo
`git@github.com:zoras/twilio-sinatra.git`

* `bundle install`

* Create new TwiML app
```[ruby]
@client = Twilio::REST::Client.new ENV["TWILIO_ACCOUNT_SID"] \
                                  ,ENV["TWILIO_AUTH_TOKEN"]
@app = @client.account.applications.create(
                      :voice_url => voice_url, :sms_url => sms_url,
                      :friendly_name => opts[:friendly])
```

* Purchase new phone number
```[ruby]
@number = @client.account.incoming_phone_numbers.create(
                    :area_code => "305", :voice_application_sid => @app.sid,
                    :sms_application_sid => @app.sid,
                    :friendly_name => opts[:friendly])
```

* Please copy paste these into your shell to test locally:
```[bash]
export TWILIO_ACCOUNT_SID=ENV['TWILIO_ACCOUNT_SID']
export TWILIO_AUTH_TOKEN=ENV['TWILIO_AUTH_TOKEN']
export TWILIO_APP_SID=ENV['TWILIO_APP_SID']
export TWILIO_CALLER_ID=ENV['TWILIO_CALLER_ID']
```

* Start server
```[bash]
foreman start
```

Congratulations! Your Twilio app should be set up properly now.

Try calling by heading to localhost:5000

Most importantly, though, hack away on app.rb!
