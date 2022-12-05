## Containers

In this session, I will explain containers. The containers, as the name suggest, are group of widget collected together. If you need to apply most of the thing together, you can create containers and used them. Here's the list of avaliable container for my version of TouchGFX.
1. Container
1. Scrollable Container
1. Swipe Container
1. List Layout
1. Modal Window
1. Scroll List
1. Scroll Wheel
1. Slide Menu

* [Container](https://support.touchgfx.com/4.18/docs/development/ui-development/ui-components/containers/container): Simple container used for just containing information. It doesn't have additional futures. You can drag the whole container, waiting for clicking that place or optionally moveanimator. I have no idea what moveanimator or clicklistener option do.

![Picture](/Pics/31.PNG "Empty Container")

![Picture](/Pics/32.PNG "Container with Circle")

* [Scrollable Container](https://support.touchgfx.com/4.18/docs/development/ui-development/ui-components/containers/scrollable-container): This container can scroll for two dimensional (both x and y or either one you preffer.). 

![Picture](/Pics/33.PNG "Scrollable Container")

I want to point it out three things. First, The things that we want to scroll should be placed under __scrollableContainer__ group. Second, we should enable scroll directions. Lastly, the field of scrollable container should be specified smaller than your whole picture. The shown bounds will be scrollable. However, the objects should be placed outside of bound in order to accessable.

* [Swipe Container](https://support.touchgfx.com/4.20/docs/development/ui-development/ui-components/containers/swipe-container): This container has multiple pages. You can switch the pages through swiping right/left. Threshold value can be set inside the properties.

![Picture](/Pics/34.PNG "Swipe Container")

* [List Layout](https://support.touchgfx.com/4.20/docs/development/ui-development/ui-components/containers/list-layout): This is container that just listing the items either horizontally or vertically. Not that good nor important.

* [Modal Window](https://support.touchgfx.com/4.20/docs/development/ui-development/ui-components/containers/modal-window): This is container which can pop up and closed as modal window. We set this open and close function two different button. One inside the modal and the other one is in screen directly. Here's the configuration that we set. The order in screen is important as well.

![Picture](/Pics/35.PNG "Modal window in Screen Configuration")

![Picture](/Pics/36.png "Modal Interaction configuration")

![Picture](/Pics/37.png "Modal Interaction configuration")

<video width="320" height="240" autoplay muted>
    <source src="Vids/2.wmv" type="video/wmv">
</video>

