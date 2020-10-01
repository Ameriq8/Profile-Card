# Profile Card

Hello Guys, today I will Show you how can make profile card with canvas-constructor

# First

Install `canvas-constructor` package

now make new file and set your source code. I will use this code
```
const { MessageEmbed, attachment } = require("discord.js");
const { Canvas, resolveImage } = require("canvas-constructor");
module.exports = {
  name: "profile",
  aliases: [],
  enabled: true,
  cooldown: 5,
  exec: async (client, message, args) => {
    // canvas code
  } 
}
```

# Secondly

Now I'm going to make a Canvas and the size of the image is 1000x800px 

```
let canvas = await new Canvas(1000, 800)
```

Now we need to add Items to the Canvas to print in the image

I will add Rectangle to image
```
let canvas = await new Canvas(1000, 800)
// to set the Item Color
.setColor("#333")
// to make Rectangle
.printRectangle(0, 0, 1000, 800)
// to make Circle
.printCircle(140, 300, 108)
```

# Third

Now how to print the user Avatar and print Text In the image

I will add print user avatar
```
// to Print user Avatar on the Circle
.printCircularImage(resolveImage(message.author.displayAvatarURL({ format: "jpg" })), 140, 300, 100)
```

Now how to print Text in the image

I will print user name and the discrim
```
// to Check text font and size
.setTextFont("bold 30px sans-serif")
// to set Text Align
.setTextAlign("left")
// to Check text color
.setColor("#FFFFFF")
// to print text in the image
.printText(`Name: ${message.author.username}`, 310, 350)
.printText(`#: ${message.author.discriminator}`, 310, 410)
```

# Fourthly

Now we will end the code

Now you need to add `.toBuffer()` to the Canvas code and set `;` at the end of `.toBuffer()` In order to prepare the image

Now we need to send the image, you need to make
```
const attachment = new MessageAttachment(canvas, `profile-card.png`);
message.channel.send(attachment);
```
And now you will get the form of such approaches
https://cdn.discordapp.com/attachments/751435920942694436/761199873642987520/profile.png

And We end the code.
Thank you Guys for reed the guide.
