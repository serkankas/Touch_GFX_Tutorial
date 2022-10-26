## Buttons

In this session, I will create a simple example that will work with simulation. As I mentioned before, it meens I am not going to add any additional/board future yet. Whenever you try to add new feature from your board (~~let's say you add hardware button, led, spi, etc.~~) you will not able to work with simulation no more. I am not sure if that's going to be fixed or not. But for now, keep in mind that.<br>
So, with that being sad. I am creating new project with following steps,
1. Open TouchGFX Designer
1. Press the Create button that placed in left corner.
1. Select the corresponded board. (~~for my case, STM32F769I Discovery Kit~~)
1. And press Create. For this purposes, I will give my application name to "Demo_4_Git"

If you followed correctly, you will ended up with empty project like I have in here.

![Picture](/Pics/6.PNG "Empty Project Screen")

I will add various buttons and going to explain what could do with what.<br>
First, let's see what types buttons are given to us.

![Picture](/Pics/7.PNG "Buttons Icon from Bar")

When you press the picture that shown at above, you will have the list of buttons that avaliable to use. The list I curently have is this.

![Picture](/Pics/8.PNG "Buttons in List")

1. Button
1. Button with Label
1. Button with Icon
1. Toggle Button
1. Radio Button
1. Repeat Button
1. Flex Button

Let me add every one of them in screen, except the radio button. Radio button will be added two times or more. Going to explain in a minute

![Picture](/Pics/9.PNG "Buttons on Screen ")

That's the simple design I came up with. Didn't add any background image since, it will be covered in upcoming sections. The buttons are as follow.

1. Button
1. Button with Label
1. Button with Icon
1. Flex Button
1. Toggle Button
1. Repeat Button
1. Radio Button
1. Radio Button
1. Radio Button

After this design, I press the generate code. Then press Run Simulation.<br>
Let's dive into what button do what. I also going to put official reference link to every button. So that if you need any further information, you could check official website.

* [Button](https://support.touchgfx.com/4.18/docs/development/ui-development/ui-components/buttons/button): This button is working as that. You pressed (nothing will happened) until you release the button. Whenever you release it, one action will be taken. The action will be setted in  Interaction part. That's why I am going to skip the what action you could do with that. Overall if you want to press button from gui and take an action, this button is way to go.<br>
When we checked the properties of button, we could see following options.

![Picture](/Pics/10.PNG "Properties of Buttons")

1. Name for button
1. Location. With non changable width and height. If you press the "Lock" section, you will not able to change the location.
1. Style Section. There is a pre-defined styles for buttons
1. Images. Let's say you decide the style but with different colors, etc. You could select from here.
1. Apperance. You could make less visible to non-visible as you wished.
1. Mixins. It gives some sort of dynamical effects in buttons. I couldn't make it work any of them but "Draggable". That's obviously unlock the position of the button and allow you to move if you wish.

* [Button with Label](https://support.touchgfx.com/4.14/docs/development/ui-development/ui-components/buttons/button-with-label): This is exact same functionallaty with "Button". It has just additional feature. That additional feature is can text be written on top button. Related options can be found in "Properties" section.

* [Button with Icon](https://support.touchgfx.com/4.14/docs/development/ui-development/ui-components/buttons/button-with-icon): This also has same exact functionallaty with "Button". The only difference now is, you can add symbol on top of button.

* [Flex Button](https://support.touchgfx.com/4.14/docs/development/ui-development/ui-components/buttons/flex-button): As the name suggest, this button can be resized as wished. Also, this button can select the behavioral trigger. That section is also shown in "Properties section". You can add additional icon/text/image from the "Visual Elements" section in "Properties" bar. There is a small "+" box that makes that option accessable.

* [Toggle Button](https://support.touchgfx.com/4.14/docs/development/ui-development/ui-components/buttons/toggle-button): Toggle button is a button if you are going to use in case like on/off switch modes. Instead of calling every iteration in every press or so, you calling iteration whenever it changes status. With creative algorithm, it can be very useful.

* [Repeat Button](https://support.touchgfx.com/4.14/docs/development/ui-development/ui-components/buttons/repeat-button): This button is a bit different that the normal button. It look same, but functional wise, it is different. I already explain that the normal button get triggered just after you release the button. However, the repeatable button works when you pressed on. The trigger happens between the tame you press and release. Longer you press, longer the triggered function will worked.

* [Radio Button](https://support.touchgfx.com/4.14/docs/development/ui-development/ui-components/buttons/radio-button): Radio button is automatically grouped. You can only select one radio button at a time in that group. Let's say you have 3 option choise for RGB (Red Green Blue), you can only select one at a time. If you need two group of radio button, you should open "Properties" bar and find the section called "Group". You can change the name of the group so that create another group and link other buttons as need it.

![Picture](/Pics/11.PNG "3 Different Radio Switch Group")

That's one example design that contains 3 different radioButtonGroup with two of them 2 buttoned, one of them 3 buttoned. It can be adjusted as needed.

<hr>
This section is over in here. Actual function connection via Interaction will be covered in Interaction section. 