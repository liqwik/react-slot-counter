# react-slot-counter

`react-slot-counter` is a feature-rich React component that displays numbers and strings with an engaging slot machine animation effect.

[![NPM](https://img.shields.io/npm/v/react-slot-counter.svg)](https://www.npmjs.com/package/react-slot-counter)
![License](https://img.shields.io/npm/l/react-confetti-boom)
![Size](https://img.shields.io/bundlephobia/min/react-confetti-boom)

<p align="center">
    <a target="_blank" href="https://almond-bongbong.github.io/react-slot-counter/">
        <img src="https://github.com/almond-bongbong/react-slot-counter/raw/main/docs/preview.gif" />
    </a>
</p>

## Features

- **Flexible Inputs**: Support for displaying numbers, strings, and JSX elements. You can even use a combination of these in a single slot counter instance!
- **Animated Changes**: Only the characters that change get animated, bringing life and motion to your app's interface.
- **Customize Animation Settings**: Control the duration of the animation, or decide whether to start the animation automatically upon mounting.
- **Sequential Animation Mode**: A unique feature that provides the option to animate the numbers incrementally or decrementally from the start value to the target value, rather than a random animation.
- **Monospace Font Support**: The useMonospaceWidth prop ensures that all numeric characters occupy the same horizontal space as they would in a monospace font.
- **Infinite List Appearance**: Option to make the list appear as continuous, seamlessly connecting the end of the target character to the beginning.
- **Style Customization**: Easily add custom styles to the characters, separators, and overall container. You can even customize the class name for the slot value.
- **Ref Support**: Control the animation start with a ref for increased flexibility.

Immerse your users in an interactive, engaging, and enjoyable experience with `react-slot-counter`. Whether you're displaying user scores, loading status, or real-time data, `react-slot-counter` adds that extra 'spin' to your numbers and strings.

## Installation

To install the package, run the following command:

```bash
npm install react-slot-counter
```

## Usage

Import `SlotCounter` and use it in your component. Here's a simple example:

```jsx
import React from 'react';
import SlotCounter from 'react-slot-counter';

function App() {
  return (
    <>
      <SlotCounter value={123456} />
      <SlotCounter value={36.5} />
      <SlotCounter value="1,234,567" />
      <SlotCounter value={['1', '2', '3', '4', '5', '6']} />
      <SlotCounter value="??????" />
    </>
  );
}

export default App;
```

## Demo

For more examples of usage and available options, check out the [demo page](https://almond-bongbong.github.io/react-slot-counter/).

## Props

| Prop                    | Type                                                  | Default                                | Description                                                                                                                                     | Version            |
| ----------------------- | ----------------------------------------------------- | -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| value _(required)_      | `number` \| `string` \| `string[]` \| `JSX.Element[]` |                                        | The value to be displayed. It can be a number or a string with numbers and commas.                                                              | JSX.Element: 1.8.0 |
| startValue              | `number` \| `string` \| `string[]` \| `JSX.Element[]` |                                        | The initial value to be displayed before the animation starts. It sets the beginning of the slot machine animation.                             | 1.7.0              |
| startValueOnce          | `boolean`                                             | `false`                                | If set to true, the animation starts from the `startValue` only for the first render. For subsequent animations, it starts from the last value. | 1.10.0             |
| duration                | `number`                                              | `0.7`                                  | The duration of the animation in seconds.                                                                                                       |                    |
| dummyCharacters         | `string[]` \| `JSX.Element[]`                         | Defaults to random numbers from 0 to 9 | An array of dummy characters to be used in the animation.                                                                                       |                    |
| dummyCharacterCount     | `number`                                              | `6`                                    | The number of dummy characters to be displayed in the animation before reaching the target character.                                           |                    |
| autoAnimationStart      | `boolean`                                             | `true`                                 | Determines whether the animation should start automatically when the component is first mounted.                                                |                    |
| animateUnchanged        | `boolean`                                             | `false`                                | Determines whether to animate only the characters that have changed.                                                                            |                    |
| hasInfiniteList         | `boolean`                                             | `false`                                | Determines whether the list should appear as continuous, with the end of the target character seamlessly connected to the beginning.            | 1.4.2              |
| containerClassName      | `string`                                              |                                        | The class name of container.                                                                                                                    |                    |
| charClassName           | `string`                                              |                                        | The class name of each character.                                                                                                               |                    |
| separatorClassName      | `string`                                              |                                        | The class name of the separator character (`.` or `,`).                                                                                         |                    |
| valueClassName          | `string`                                              |                                        | The class name for the value of the slot, making it possible to customize the styling and visibility of the value.                              | 1.4.3              |
| sequentialAnimationMode | `boolean`                                             | `false`                                | Determines if the animation should increment or decrement sequentially from the startValue to value instead of random animation.                | 1.9.0              |
| useMonospaceWidth       | `boolean`                                             | `false`                                | Ensures that all numeric characters occupy the same horizontal space, just like they would in a monospace font.                                 | 1.9.0              |
| debounceDelay           | `number`                                              | `0`                                    | Specifies the delay in milliseconds for debouncing animations. When the value changes rapidly, it allows the animation to execute smoothly.     | 1.11.0             |

## Ref

You can access the SlotCounter component using a ref. This ref can be used to start the animation of the component.

| Method           | Description                          |
| ---------------- | ------------------------------------ |
| `startAnimation` | Start the animation of the component |

The `startAnimation` method accepts an optional object with the following properties:

- `duration`: The duration of the animation in seconds. Overrides the `duration` prop.
- `dummyCharacterCount`: The number of dummy characters to be displayed in the animation before reaching the target character. Overrides the `dummyCharacterCount` prop.
- `direction`: This option determines the direction of the slot machine animation. The accepted values are `bottom-top` and `top-bottom`. The default value is `bottom-top`. If `bottom-top` is chosen, the animation will start from the bottom and move towards the top. If `top-bottom` is chosen, the animation will start from the top and move downwards.

Example:

```jsx
import React, { useRef } from 'react';
import SlotCounter, { SlotCounterRef } from 'react-slot-counter';

function App() {
  const counterRef = useRef < SlotCounterRef > null;

  const handleStartClick = () => {
    counterRef.current?.startAnimation();
  };

  return (
    <>
      <SlotCounter value={123456} ref={counterRef} />
      <button onClick={handleStartClick}>Start</button>
    </>
  );
}

export default App;
```

## Contributing

Contributions are always welcome!

## Support Us

If you find this library useful, consider giving us a star on [GitHub!](https://github.com/almond-bongbong/react-slot-counter/stargazers) Your support is greatly appreciated and it helps the project grow.

## License

This project is licensed under the MIT License.
