---
title: Cards
description: Describes all the cards available to bots in Teams
keywords: bots cards reference
ms.date: 03/22/18
---
# Cards Reference

The cards listed in this section are supported in bots for Teams. These cards are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own. Differences are called out in the references below.

## Card examples

You can find information on how to use cards in the documentation for the Bot Builder SDK. Code samples are in the Microsoft/BotBuilder-Samples repository on GitHub.

* .NET
  * [Add cards as attachments to messages](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [Cards sample code](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/cards-RichCards)
* Node.js
  * [Add cards as attachments to messages](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [Cards sample code](https://github.com/Microsoft/BotBuilder-Samples/tree/master/Node/cards-RichCards)

## Common properties for all cards

### Inline card images

Your card can contain a inline image by including a link to the image content hosted on a public content-delivery network (CDN).

Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.

Images must be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF is not officially supported.

| Property | Type  | Description |
| --- | --- | --- |
| url | URL | HTTPS URL to the image |
| alt | String | Accessible description of the image |

### Buttons

Buttons are shown stacked at the bottom of the card. Button text is always on a single line and will be truncated if the text exceeds the button width. Any additional buttons beyond the maximum number supported by the card will not be shown.

See the topic [Card Actions](`/concepts/cards/cards-actions) for more information.

### Card formatting

* Cards support formatting in the text property only, not in the title or subtitle properties
* Cards do not support Markdown or table formatting

[!include[Formatting text content in cards](~/includes/bots/message-format-cards.html)]a

## Hero card

A card that typically contains a single large image, one or more buttons, and text.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

### Example

![Example of a hero card](~/assets/images/cards/hero.png)

### Properties

| Property | Type  | Description |
| --- | --- | --- |
| title | Rich text | Title of the card. Maximum 2 lines; formatting not currently supported |
| subtitle | Rich text | Subtitle of the card. Maximum 2 lines; formatting not currently supported |
| text | Rich text | Text appears just below the subtitle; see [Message format](~/concepts/bots/bots-conversations#message-format) for formatting options |
| images | Array of images | Image displayed at top of card. Aspect ratio 16:9 |
| buttons | Array of action objects | Set of actions applicable to the current card. Maximum 6 |
| tap | Action object | This action will be activated when the user taps on the card itself |
|

### Example

```JSON
{
  "contentType": "application/vnd.microsoft.card.hero",
  "content": {
    "title": "Bender Bending RodrÃ­guez",
    "subtitle": "Main character in the animated television series Futurama",
    "text": "Bender Bending RodrÃ­guez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio",
    "images": [
      {
        "url": "http://cdn.overclock.net/7/72/72f33e5f_greybender.png",
        "alt": "Bender_Rodriguez"
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Thumbs Up",
        "image": "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg",
        "value": "I like it"
      },
      {
        "type": "imBack",
        "title": "Thumbs Down",
        "image": "http://yourfaceisstupid.com/wp-content/uploads/2014/08/thumbs-down.png",
        "value": "I don't like it"
      },
      {
        "type": "openUrl",
        "title": "I feel lucky",
        "image": "http://thumb9.shutterstock.com/photos/thumb_large/683806/148441982.jpg",
        "value": "https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE"
      }
    ],
    "tap": {
      "type": "imBack",
      "value": "Tapped it!"
    }
  }
}
```

### For more information

Bot Framework reference:

* [Hero card Node](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.herocard.html)
* [Hero card C#](https://docs.botframework.com/en-us/csharp/builder/sdkreference/attachments.html#herocard) 

## Thumbnail card

A card that typically contains a single thumbnail image, one or more buttons, and text.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

### Example

![Example of a thumbnail card](~/assets/images/cards/thumbnail.png)

### Properties

| Property | Type  | Description |
| --- | --- | --- |
| title | Rich text | Title of the card. Maximum 2 lines; formatting not currently supported |
| subtitle | Rich text | Subtitle of the card. Maximum 2 lines; formatting not currently supported |
| text | Rich text | Text appears just below the subtitle; see [Message format](~/concepts/bots/bots-conversations#message-format) for formatting options |
| images | Array of images | Image displayed at top of card. Aspect ratio 1:1 (square) |
| buttons | Array of action objects | Set of actions applicable to the current card. Maximum 6 |
|

### Schema

| tap | Action object | This action will be activated when the user taps on the card itself |

### Example

```JSON
{
  "contentType": "application/vnd.microsoft.card.thumbnail",
  "content": {
    "title": "Bender",
    "subtitle": "tale of a robot who dared to love",
    "text": "Bender Bending RodrÃ­guez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio",
    "images": [
      {
        "url": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
        "alt": "Bender_Rodriguez"
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Thumbs Up",
        "image": "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg",
        "value": "I like it"
      },
      {
        "type": "imBack",
        "title": "Thumbs Down",
        "image": "http://yourfaceisstupid.com/wp-content/uploads/2014/08/thumbs-down.png",
        "value": "I don't like it"
      },
      {
        "type": "openUrl",
        "title": "I feel lucky",
        "image": "http://thumb9.shutterstock.com/photos/thumb_large/683806/148441982.jpg",
        "value": "https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE"
      }
    ],
    "tap": {
      "type": "imBack",
      "value": "Tapped it!"
    }
  }
}
```

### For more information

Bot Framework reference:

* [Thumbnail card Node](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.thumbnailcard.html)
* [Thumbnail card C#](https://docs.botframework.com/en-us/csharp/builder/sdkreference/attachments.html#thumbnailcard)

## Office 365 connector card

Supported in teams, not in Bot Framework.

The Office 365 Connector card provides a flexible layout with multiple sections, fields, images, and actions. This card encapsulates a connector card so that it can be used by bots. See the notes section for differences between connector cards and the O365 card.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✖ |
|

### Notes

Office 365 Connector cards function properly on Microsoft Teams including [ActionCard actions](https://docs.microsoft.com/en-us/outlook/actionable-messages/card-reference#actioncard-action).

One important difference between using Connector cards from a Connector and using Connector cards in your bot is the handling of card actions.

* For a Connector, the endpoint receives the card payload via HTTP POST.
* For a bot, the `HttpPOST` action triggers an `invoke` action that sends only the action ID and body to the bot.

To use Connector cards in your bot, we recommend using the `O365ConnectorCard` class in the [Teams extensions for the Bot Builder SDK](~/get-started/code#microsoft-teams-extensions-for-the-bot-builder-sdk) for .NET or Node.js. You can simplify handling of the `HttpPOST` action by using the `onO365ConnectorCardAction` method.

Each Connector card can display a maximum of 10 sections; each section can contain a maximum of 5 images and 5 actions.

> [!NOTE]
> Any additional sections, images, or actions in a message do not appear.

All text fields support Markdown and HTML formatting. You can control which sections use Markdown or HTML by setting the `markdown` property in a message. By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.

If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.

To specify the rendering style for `activityImage`, you can set `activityImage` as follows.

| Value | Description |
| --- | --- |
| `avatar` | Default; `activityImage` will be cropped as a circle |
| `article` | `activityImage` will be displayed as a rectangle and retain its aspect ratio |

For all other details about Connector card properties, see the **[Actionable message card reference](https://docs.microsoft.com/en-us/outlook/actionable-messages/card-reference)**. The only Connector card properties that Microsoft Teams does not currently support are as follows:

* `heroImage`
* `hideOriginalBody`
* `startGroup`

### Properties

| Property | Type  | Description |
| --- | --- | --- |
| title | Rich text | Title of the card. Maximum 2 lines; formatting not currently supported |
| subtitle | Rich text | Subtitle of the card. Maximum 2 lines; formatting not currently supported |
| text | Rich text | Text appears just below the subtitle; see [Message format](~/concepts/bots/bots-conversations#message-format) for formatting options |
| images | Array of images | Image displayed at top of card. Aspect ratio 16:9 |
| buttons | Array of action objects | Set of actions applicable to the current card. Maximum 6 |
| tap | Action object | This action will be activated when the user taps on the card itself |

### Example

```JSON
{
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "John Doe commented on Trello",
    "title": "Project Tango",
    "sections": [
        {
            "activityTitle": "John Doe commented",
            "activitySubtitle": "On Project Tango",
            "activityText": "\"Here are the designs\"",
            "activityImage": "http://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg"
        },
        {
            "title": "Details",
            "facts": [
                {
                    "name": "Labels",
                    "value": "Designs, redlines"
                },
                {
                    "name": "Due date",
                    "value": "Dec 7, 2016"
                },
                {
                    "name": "Attachments",
                    "value": "[final.jpg](http://connectorsdemo.azurewebsites.net/images/WIN14_Jan_04.jpg)"
                }
            ]
        },
        {
            "title": "Images",
            "images": [
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/MicrosoftSurface_024_Cafe_OH-06315_VS_R1c.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Scene_01.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Anthony_02.jpg"
                }
            ]
        }
    ],
    "potentialAction": [
        {
            "@context": "http://schema.org",
            "@type": "ViewAction",
            "name": "View in Trello",
            "target": [
                "https://trello.com/c/1101/"
            ]
        }
    ]
}
```

### Using the O365 Connector card

If you are using .NET and C# or Node.js, you can use the `O365ConnectorCard` class in the [Microsoft Teams extensions for the Bot Builder SDK](~/get-started/code#microsoft-teams-extensions-for-the-bot-builder-sdk) to send Connector cards from your bot.

## List card

The list card has been added by Teams to provide functions beyond what the list collection can provide. The list card provides a scrolling list of items.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✖ |
|

### Properties

| Property | Type  | Description |
| --- | --- | --- |
| title | Rich text | Title of the card. Maximum 2 lines; formatting not currently supported |
| items | Array of list items  ||
| buttons | Array of action objects | Set of actions applicable to the current card. Maximum 6 |
|

### Example

```JSON
{
  "contentType": "application/vnd.microsoft.teams.card.list",
  "content": {
    "title": "Card title",
    "items": [
      {
        "type": "file",
        "id": "https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xslx",
        "title": "Report",
        "subtitle": "teams > new > design",
        "tap": {
          "type": "imback",
          "value": "editOnline https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx"
        }
      },
      {
        "type": "resultItem",
        "icon": "https://cdn2.iconfinder.com/data/icons/social-icons-33/128/Trello-128.png",
        "title": "Trello title",
        "subtitle": "A Trello subtitle",
        "tap": {
          "type": "openurl",
          "value": "http://trello.com"
        }
      },
      {
        "type": "section",
        "title": "Manager"
      },
      {
        "type": "person",
        "id": "JohnDoe@contoso.com",
        "title": "John Doe",
        "subtitle": "Manager",
        "tap": {
          "type": "imback",
          "value": "whois JohnDoe@contoso.com"
        }
      }
    ],
    "buttons": [
      {
        "type": "imback",
        "title": "Select",
        "value": "whois"
      }
    ]
  }
}
```

## Profile card

The profile card has been added by Teams.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✖ |
|

### Properties

| Property | Type  | Description |
| --- | --- | --- |
| title | Rich text | Title of the card. Maximum 2 lines; formatting not currently supported |
| description | Rich text | Subtitle of the card. Maximum 2 lines; formatting not currently supported |
| type |||
| required |||
| additionalProperties |||
| properties |||
| definitions |||
|

## Adaptive card

Not supported in Microsoft Teams.

A customizable card that can contain any combination of text, speech, images, buttons, and input fields.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✖ | ✖ | ✖ | ✔ |
|

### For more information

[Adaptive Cards Overview](https://docs.microsoft.com/en-us/adaptive-cards/)

## Animation card

Not supported in Teams.

A card that can play animated GIFs or short videos.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✖ | ✖ | ✖ | ✔ |
|

### For more information

Bot Framework reference:

* [Animation card Node](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.animationcard.html)

## Audio card

Not supported in Teams.

A card that can play an audio file.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✖ | ✖ | ✖ | ✔ |
|

### For more information

Bot Framework reference:

* [Audio card Node](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.audiocard.html)

## Receipt card

Not supported in Teams. TBD: billbl: I think it was implemented. Check with Robyn Liao.

A card that enables a bot to provide a receipt to the user. It typically contains the list of items to include on the receipt, tax and total information, and other text.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✖ | ✖ | ✖ | ✔ |
|

### For more information

Bot Framework reference:

* [Recipt card Node](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.receiptcard.html)

## Signin card

Supported in teams

A card that enables a bot to request that a user sign-in. It typically contains text and one button that the user can click to initiate the sign-in process.

Teams users can also use the *signin action* from any card. See the topic [Microsoft Teams authentication flow for bots](`/concepts/bots/auth-flow-bot) for more details.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✖ | ✖ | ✖ | ✔ |
|

### For more information

Bot Framework reference:

*[Bot Framework SignIn card Node](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.signincard.html)

## Video card

Not supported in Teams.
A card that can play videos.

### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✖ | ✖ | ✖ | ✔ |
|

### For more information

Bot Framework reference:
[Video card](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.videocard.html)

## Card collections

Card collections are provided by the Bot Framework: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.  These collections can only contain Hero or Thumbnail cards.

### Carousel collection

The [carousel layout](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments) shows a carousel of cards, optionally with associated action buttons.

#### Support

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

> [!NOTE]
> A carousel can display a maximum of 10 cards per message.

#### Example

![Example of a carousel of cards](~/assets/images/cards/carousel.png)

Properties are the same as for the hero or thumbnail card.

#### Syntax

`builder.AttachmentLayout.carousel`

### List collection

#### Support

The list layout shows a vertically stacked list of cards, optionally with associated action buttons.

| Bots in Teams | Messaging Extensions  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

#### Example

![Example of a list of cards](~/assets/images/cards/list.png)

Properties are the same as for the hero or thumbnail card.

A list can display a maximum of 10 cards per message.

> [!NOTE]
> Some combinations of list cards are not yet supported on iOS and Android.

#### Syntax

`builder.AttachmentLayout.list`