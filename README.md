# lovebot-nodejs

## Introduction

LoveBot is a chatbot connected to my Facebook Page Glovers : https://www.facebook.com/gloverskor/

It handles customers general inquiries (Delivery info, Size chart, etc..).
It's using Dialogflow Natural language processing and it's hosted on Heroku platform.

Working now on the ownership thread protocol & payment system.

## Messenger profile API cURL commands

To set up the bot profile using the messenger profile API, here are the commands line:


> GREETING BUTTON

```
curl -X POST -H "Content-Type: application/json" -d '{
    "greeting":[
      {
        "locale":"default",
        "text":"Hello {{user_first_name}}! LoveBot at your service."
      }, {
        "locale":"en_US",
        "text":"Hello {{user_first_name}}! LoveBot at your service."
      }, {
        "locale":"ko_KR",
        "text":"안녕하세요 {{user_first_name}}! 러브봇입니다."
      }
    ]
}' "https://graph.facebook.com/v2.6/me/messenger_profile?access_token=YOUR_API_TOKEN"
```

> GET STARTED BUTTON 

```
curl -X POST -H "Content-Type: application/json" -d '{
  "get_started":{
    "payload":"Get started !"
  }
}' "https://graph.facebook.com/v2.6/me/messenger_profile?access_token=YOUR_API_TOKEN"
```

> PERSISTENT MENU 

```
curl -X POST -H "Content-Type: application/json" -d '{
    "persistent_menu":[
    {
      "locale":"default",
      "composer_input_disabled": false,
      "call_to_actions":[
        {
          "type":"web_url",
          "title":"Buy now !",
          "url":"http://storefarm.naver.com/glovers/products/2371275262",
          "webview_height_ratio":"tall"
        },
        {
          "title":"Questions",
          "type":"nested",
          "call_to_actions":[
            {
              "title":"Delivery Information",
              "type":"postback",
              "payload":"Delivery information"
            },
            {
              "title":"What is Glovers?",
              "type":"postback",
              "payload":"What is Glovers?"
            },
            {
              "title":"Size Chart",
              "type":"postback",
              "payload":"Size chart"
            },
            {
              "title":"Refund Policy",
              "type":"postback",
              "payload":"Refund policy"
            }
          ]
        },
        {
          "title":"Contact",
          "type":"nested",
          "call_to_actions":[
            {
              "title":"Talk to LoveBot",
              "type":"postback",
              "payload":"I want to talk to LoveBot"
            },
            {
              "title":"Talk to human staff",
              "type":"postback",
              "payload":"I want to talk to human staff"
            }
          ]
        }
      ]
    }
  ]
}' "https://graph.facebook.com/v2.6/me/messenger_profile?access_token=YOUR_API_TOKEN"
```







