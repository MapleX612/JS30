# 10 - Hold Shift and Check Checkboxes

**[Live Demo](https://maplex612.github.io/JS30/10%20-%20Hold%20Shift%20and%20Check%20Checkboxes/index-MAPLE.html)**  

## 1. Detect whether the <kbd>shift</kbd> key is pressed - `shiftKey` property  

The `shiftKey` property exists in `MouseEvent`, `KeyboardEvent` and `TouchEvent`. This property is a boolean value and always read-only.

In `MouseEvent` and `KeyboardEvent`, `shiftKey` is `true` if the <kbd>shift</kbd> key was pressed when the event occurs.

In this challenge, with this property, there is no need to listen to `keydown` and `keyup` events to detect when the shift key is pressed.
  
## 2. Pass parameters into event listeners - encapsulate the actual listener with a anonymous function  

As known, the event listener (callback function) accepts **one single parameter** - the `Event` object describing current event. If we want to pass more parameters into the callback, we can use a anonymous function encapsulating the actual listener, like this:  
```
//other info we want to pass to the listener
let param = 'someInfo'; 

element.addEventListener('click', () => { actualListener(param); });
```

In this challenge, I want to track the index of the clicked checkbox, so that when <kbd>shift</kbd> is pressed, I can know where to start and end.  

To do this, of course, I focused on the `click` event listener. At first, I tried to find if the click event object `e` passed to the listener contains the index info. However, I didn't find such property (there are some indirect information showing which checkbox is clicked, like `nextSiblingElement`, though it's of no help to get the index). Thus, I tried to pass the index info into the listener, using the above approach.

Here is my code:
```
checkboxes.forEach((checkbox, index) => {
    checkbox.addEventListener('click', (e) => selectGroup(e, index));
});
```  
In `Array.forEach()`, I can get the index of the checkbox. Then I pass this info into the actual listener `selectGroup()`. I also need the event object `e` here to check the `shiftKey` property, so I pass `e` into `selectGroup()` as well. 

## 3. My Implementation and Wes's Implementation  
In this challenge, we all need to find the range of the chosen checkboxes - the start and end point.  

As for me, I use indices to identify the start/end checked box. To get the index of the clicked checkbox, I use the optional argument, `index`, of the callback function in `Array.forEach()`.     

Wes (see index-FINISHED.html) identifies the start/end checkboxes by looping through the list and comparing the elements directly.  

My implementation may be 'fragile' since I use the relative position of the checkboxes to locate them. This approach relies on the structure of the list. If the structure changes, indices may change and more work is needed.
