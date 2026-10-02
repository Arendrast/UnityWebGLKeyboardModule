# Unity WebGL Mobile Keyboard

The project is a **module that brings the native mobile keyboard to `TMP_InputField` in Unity WebGL builds**. Out of the box, Unity WebGL does not open the phone keyboard properly, so I made my own solution: the `MobileWebGLKeyboardTools` class, which works together with the `web-gl-mobile-keyboard.jslib` plugin

It supports *emoji* (text can be replaced with `<sprite=Index>` images), closing the keyboard after submit and full styling of the input field through CSS values

---

### Installation
1. Add the module to your project (the `Runtime` folder with the `WebGLMobileKeyboardModule` assembly)
2. Put `web-gl-mobile-keyboard.jslib` from the `WebGL` folder of this repository into `Assets/Plugins/WebGL`

---

### Quick start
If the default look suits you and you don't want to initialize the input field from code, just add the `InputFieldMobileWebGLKeyboardInitializer` component to the GameObject with the input field

---

### Initializing from code
Call the method below on start for every input field that should open the mobile keyboard (each one is initialized separately):

```csharp
#if UNITY_WEBGL && !UNITY_EDITOR
_inputField.InitializeInputFieldForMobileKeyboard(
    shouldReplaceEmojiTextToImage: true,
    shouldCloseKeyboardAfterSubmit: true,
    fontSize: "18px");
#endif
```

Wrap the call in `#if UNITY_WEBGL && !UNITY_EDITOR`: calling an `extern` method in the Editor throws an error

---

### Parameters
1. `inputField` - the input field the keyboard is opened for
2. `shouldReplaceEmojiTextToImage` - whether to replace text with images (emoji). If not, `<sprite=Index>` stays plain text
3. `shouldCloseKeyboardAfterSubmit` - whether to close the keyboard after pressing submit
4. `color` - text color of the input field

**Input field settings** take CSS values. If you're not sure what to pass, look up CSS examples online:

1. `backgroundColor` - background color
2. `top` - offset from the top edge of the screen
3. `bottom` - offset from the bottom edge of the screen
4. `left` - offset from the left edge of the screen
5. `width` - width
6. `height` - height
7. `transform` - offset of the element relative to itself
8. `position` - position mode
9. `border` - border
10. `fontSize` - font size (at least `16px` is recommended)

<img width="607" height="415" alt="Mobile keyboard input field in a WebGL build" src="https://github.com/user-attachments/assets/d67973cd-ade9-49fe-bb1c-94059c5db849" />

---

### Default values
Any parameter you leave out falls back to its default:

<img width="471" height="163" alt="Default input field values" src="https://github.com/user-attachments/assets/b59fcc5b-0347-4044-b4ea-d049deb2cab2" />

---

*Happy to hear any feedback or questions! :)*
