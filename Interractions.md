## Interractions

In this section, I will explain some functionallaty that you can add to your design. For that, I want to create a two Screen application with single button each. Whenever I press the button, I want them to change accordingly.<br>
Let's dive into the example design.

Screen 1

![Picture](/Pics/12.PNG "Screen 1 Design")

Screen 2

![Picture](/Pics/13.PNG "Screen 2 Design")

The background images comes from "Images" section. It will be covered in other markdown file. It's straight-forward that I just put two simple background the distinguish the screens from each other.<br>
I just add "Button" without any additional function.<br>
Now, when we press the button, we will see Properties/Interaction tab at the right corner screen. I do not want to change anything from properties. So, I select the Interaction tab. It is completely empty at first. We need to add some interaction. In order to add some functionality to our design. There is a small "Add interaction" button that we can add variety interaction with it.<br>
Let's have a look at the what interaction we can add. ~~The Interaction section related to screen 1. The screen 2 will be configured later~~

![Picture](/Pics/14.PNG "Add Interaction button")

![Picture](/Pics/15.png "Empty Interaction Section")

After press that button, we have empty interaction section. I will add interaction and put the last version that in here as picture.

![Picture](/Pics/16.png "Designed Interaction Section for Screen 1")

Along with your selections, there will add some new tabs. That's why it's confusing to tell everything one by one.<br>
We can follow from designed section. Here is the key idea that we should follow:

1. Trigger: When the interaction will be triggered. We want our function triggered when the button is triggered. So, we select that.
1. Choose clicked source: Which button clicked source will trigger the function. That might be multiple button action that you want to have different trigger on. It will be handled one by one as interaction.
1. Action: There are couple action type that you can select. I am going to use two different way to make this example happen. First is, using pre-built screen change design. Second is, using virtual function. __Note that, using virtual function may crush the simulation. In that case, focus on build itself, not simulation!__
1. Choose screen: The screen that will come after the trigger. Not the one that you are currently in. The one will be happen after.
1. Transition: You have some option, I didn't look all of it. Just using slide is satisfying for me.
1. Transition direction: There are four option for slide option. It may vary for different transitions.
1. Interaction Name: You can leave it default or change as you wish.

We will configure almost same pattern in Screen 2 interaction.

![Picture](/Pics/17.png "Deisgned Interaction Section for Screen 2")

Now, I may need to clearify two things.
1. Button1 is used for first example too, but since we change to the screen 2. It binds this function to Screen2::Button1. The previous one binded to Screen1::Button1. So they are not the same button!
1. Interaction 1 name is also used for in both situation. But still, it is binded the each screen with different functions. In order to make this work, you need to call from related screen when we coded our design.

With that being sad, you can build your code and run simulation.

<video width="320" height="240" autoplay muted>
    <source src="Vids/1.mov" type="video/mov">
</video>

This was the first way to do with. Now we can do with virtual functions. Using virtual functions are also important since the button action may not only have screen transition, but additional implementation like changing the button status, or sending some message through the UART. You need to handle those action from virtual functions.<br>
Before we re-arrange the interaction functions, I want to look to the projects in STM32CubeIDE. Because, I might have trouble to make transition with sliding effect on board.<br>
When you press the file location from TouchGFX, you will ended up in a file called<br>
>\<ProjectPath>/\<ProjectName>/TouchGFX

From here, you want to return to your \<ProjectName> path, so that you could see your IDE environment. I prefer to use STM32CubeIDe, so I select that one. Ended up with this path
>\<ProjectPath>/\<ProjectName>/STM32CubeIDE

You will select the __.project__ file to open from your IDE.

![Picture](/Pics/18.png "Files from non-converted project")

1. Screen1View&Screen2View is the part where we will add our virtual functions. ~~Also inside the related header file~~
1. Screen1ViewBase is the place where most of the things are configured.
1. Also main can be converted as you wished. But simple functions can be handled inside the __view.cpp__ files

When we checked the transition and how it happens, we can see that it contains these inside of the FrontEndApplicationBase.cpp file

```c++
/*********************************************************************************/
/********** THIS FILE IS GENERATED BY TOUCHGFX DESIGNER, DO NOT MODIFY ***********/
/*********************************************************************************/
#include <new>
#include <gui_generated/common/FrontendApplicationBase.hpp>
#include <gui/common/FrontendHeap.hpp>
#include <touchgfx/transitions/NoTransition.hpp>
#include <texts/TextKeysAndLanguages.hpp>
#include <touchgfx/Texts.hpp>
#include <touchgfx/hal/HAL.hpp>
#include <platform/driver/lcd/LCD16bpp.hpp>
#include <gui/screen1_screen/Screen1View.hpp>
#include <gui/screen1_screen/Screen1Presenter.hpp>
#include <gui/screen2_screen/Screen2View.hpp>
#include <gui/screen2_screen/Screen2Presenter.hpp>

using namespace touchgfx;

FrontendApplicationBase::FrontendApplicationBase(Model& m, FrontendHeap& heap)
    : touchgfx::MVPApplication(),
      transitionCallback(),
      frontendHeap(heap),
      model(m)
{
    touchgfx::HAL::getInstance()->setDisplayOrientation(touchgfx::ORIENTATION_LANDSCAPE);
    reinterpret_cast<touchgfx::LCD16bpp&>(touchgfx::HAL::lcd()).enableTextureMapperAll();
}
/*
 * Screen Transition Declarations
 */

// Screen1

void FrontendApplicationBase::gotoScreen1ScreenNoTransition()
{
    transitionCallback = touchgfx::Callback<FrontendApplicationBase>(this, &FrontendApplication::gotoScreen1ScreenNoTransitionImpl);
    pendingScreenTransitionCallback = &transitionCallback;
}

void FrontendApplicationBase::gotoScreen1ScreenNoTransitionImpl()
{
    touchgfx::makeTransition<Screen1View, Screen1Presenter, touchgfx::NoTransition, Model >(&currentScreen, &currentPresenter, frontendHeap, &currentTransition, &model);
}

void FrontendApplicationBase::gotoScreen1ScreenSlideTransitionEast()
{
    transitionCallback = touchgfx::Callback<FrontendApplicationBase>(this, &FrontendApplication::gotoScreen1ScreenSlideTransitionEastImpl);
    pendingScreenTransitionCallback = &transitionCallback;
}

void FrontendApplicationBase::gotoScreen1ScreenSlideTransitionEastImpl()
{
    touchgfx::makeTransition<Screen1View, Screen1Presenter, touchgfx::SlideTransition<EAST>, Model >(&currentScreen, &currentPresenter, frontendHeap, &currentTransition, &model);
}

// Screen2

void FrontendApplicationBase::gotoScreen2ScreenSlideTransitionWest()
{
    transitionCallback = touchgfx::Callback<FrontendApplicationBase>(this, &FrontendApplication::gotoScreen2ScreenSlideTransitionWestImpl);
    pendingScreenTransitionCallback = &transitionCallback;
}

void FrontendApplicationBase::gotoScreen2ScreenSlideTransitionWestImpl()
{
    touchgfx::makeTransition<Screen2View, Screen2Presenter, touchgfx::SlideTransition<WEST>, Model >(&currentScreen, &currentPresenter, frontendHeap, &currentTransition, &model);
}
```

Although it says do not change the file, we may need to change couple things to make work on

Now we could change the iterations and make our example with virutal functions way.<br>
In Screen1

![Picture](/Pics/19.png "Screen1 Virtual Function")

In Screen2

![Picture](/Pics/20.png "Screen2 Virtual Function")

After set our interactions, generate the code. Then open from CubeIDE ~~or preffered IDE~~.<br>
Now we need to configure some files. In order to make these functions work, we need to find related function as need.<br>
First we will set up the Screen 1 to Screen 2 transition, then vice versa.<br>
Open the __Screen1ViewBase.cpp__ file. And find the related code part.

![Picture](/Pics/21.png "gotoScreen2 definiton")

After we see where our function called, we clearify that name is defined as it is. From here, we need to declear a virtual function in both __Screen1View.hpp__ and __Screen1View.cpp__. I am going to share how it also happen.

![Picture](/Pics/22.png "gotoScreen2 declerataion")

Now, __FrontendApplicationBase.cpp__ looks like this

```c++
/*********************************************************************************/
/********** THIS FILE IS GENERATED BY TOUCHGFX DESIGNER, DO NOT MODIFY ***********/
/*********************************************************************************/
#include <new>
#include <gui_generated/common/FrontendApplicationBase.hpp>
#include <gui/common/FrontendHeap.hpp>
#include <touchgfx/transitions/NoTransition.hpp>
#include <texts/TextKeysAndLanguages.hpp>
#include <touchgfx/Texts.hpp>
#include <touchgfx/hal/HAL.hpp>
#include <platform/driver/lcd/LCD16bpp.hpp>
#include <gui/screen1_screen/Screen1View.hpp>
#include <gui/screen1_screen/Screen1Presenter.hpp>
#include <gui/screen2_screen/Screen2View.hpp>
#include <gui/screen2_screen/Screen2Presenter.hpp>

using namespace touchgfx;

FrontendApplicationBase::FrontendApplicationBase(Model& m, FrontendHeap& heap)
    : touchgfx::MVPApplication(),
      transitionCallback(),
      frontendHeap(heap),
      model(m)
{
    touchgfx::HAL::getInstance()->setDisplayOrientation(touchgfx::ORIENTATION_LANDSCAPE);
    reinterpret_cast<touchgfx::LCD16bpp&>(touchgfx::HAL::lcd()).enableTextureMapperAll();
}

/*
 * Screen Transition Declarations
 */

// Screen1

void FrontendApplicationBase::gotoScreen1ScreenNoTransition()
{
    transitionCallback = touchgfx::Callback<FrontendApplicationBase>(this, &FrontendApplication::gotoScreen1ScreenNoTransitionImpl);
    pendingScreenTransitionCallback = &transitionCallback;
}

void FrontendApplicationBase::gotoScreen1ScreenNoTransitionImpl()
{
    touchgfx::makeTransition<Screen1View, Screen1Presenter, touchgfx::NoTransition, Model >(&currentScreen, &currentPresenter, frontendHeap, &currentTransition, &model);
}
```
So there is couple functions are missing as you can see:
* void FrontendApplicationBase::gotoScreen1ScreenSlideTransitionEast()
* void FrontendApplicationBase::gotoScreen1ScreenSlideTransitionEastImpl()
* void FrontendApplicationBase::gotoScreen2ScreenSlideTransitionWest()
* void FrontendApplicationBase::gotoScreen2ScreenSlideTransitionWestImpl()

We are going to create second interaction to have those transition. Screen 1 Interaction.

![Picture](/Pics/23.png "Screen 2 Transition")

Does the same for Screen 2 Interaction

![Picture](/Pics/24.png "Screen 1 Transition")

There is total 4 file that has been changed.

* Screen1View.cpp
* Screen1View.hpp
* Screen2View.cpp
* Screen2View.hpp

We add virtual functions in both header and source files.<br>
Inside the functions, we implement the transition functions like this.

```c++
void Screen1View::gotoScreen2()
{
	application().gotoScreen2ScreenSlideTransitionEast();
}
```
When you press simulate, it works like before.<br>
If you want to have a GPIO status change or any other function that you want to add, you can configure your Screen1View.cpp file accordingly.<br>

After these steps, you can easily see that simulation has transition effect as before. However, that's not the case in MCU. ~~I will look at the configuration and explain what is wrong and why there is no transition in MCU later on.~~

<hr>
This section is over in here. Feel free to check other markdown files.