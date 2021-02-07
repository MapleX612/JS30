# 01 - Drum Kit  
**[Live Demo](https://maplex612.github.io/JS30/01%20-%20JavaScript%20Drum%20Kit/index-MAPLE.html)**  

## 1. `data-*` attribute
Global user-defined attribute in html element (HTML5).   
E.g.  
```
    <div data-key="65" class="key">
      <kbd>A</kbd>
      <span class="sound">clap</span>
    </div>
```
The `data-key` attribute above is the custom data attribute.  

**Methods to get/set the attribute value**  

Suppose we have a custom data attribute `data-test-value` in a div element.  

(1) `getAttribute`/`setAttribute` method   
```
div.getAttribute('data-test-value')
div.setAttribute('data-test-value', value);
```  

(2) `dataset` property  
```
div.dataset['testValue']
div.dataset.testValue
```  
Dash(es) in the `*` part of `data-*` will be replaced with capital letter, which converts the custom name to camelcase.   

Additionally, `in` operator can be used to check if a certain data-* attribute exists, e.g.  
```
if('testValue' in div.dataset)
```  
     
  
## 2. `currentTime` property
This property specifies the current playback time in seconds.  

```
const sound = document.querySelector(`audio[data-key='${e.keyCode}']`);
if (!sound) return; 
sound.currentTime = 0; //rewind the audio to start
sound.play();
```
Here in Drum Kit, each time when the key is pressed, we find the corresponding audio, rewind the audio to its start using `currentTime = 0` and call `play()`. In this way, everytime the key is pressed, the audio plays from the start.   

If we don't rewind the audio, then when the same key is pressed several times within a short period, the audio may only play 1 or 2 times. This is because if we call `play()` on a *playing* audio, it won't play again.

## 3. `transitionend` event  
`transitionend` event is fired when a CSS transition is completed, in both direction. In other words, reaching the target state and reverting back to the original state will all fire this event.  

In Drum Kit, since we have transition defined on the key UI blocks, thus we can listen the `transitionend` event to remove the effects.  

`keyup` event can also be used here to remove the effects. However, all the keys on keyboard will be listened while we only need to monitor certain keys. Meanwhile, if the transition duration is longer (e.g. more than 1s), the effects will be removed before it's fully displayed and we will barely recognize it.






