---
layout: post
---
Now selenium 3 is the default I've had some issues running tests on Centos 6
which use Firefox ESR.  Selenium 3 will try and use geckodriver/marionette by
default so you have to turn this off. Sample ruby code:

    desired_capabilities = Selenium::WebDriver::Remote::Capabilities.firefox
    desired_capabilities[:marionette] = false unless system('sh -c "command -v geckodriver > /dev/null"')
    Capybara.register_driver(:selenium) { |app| Capybara::Selenium::Driver.new(app, profile: profile, desired_capabilities: desired_capabilities) }
