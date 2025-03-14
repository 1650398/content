---
title: BaseAudioContext.createBiquadFilter()
slug: Web/API/BaseAudioContext/createBiquadFilter
page-type: web-api-instance-method
tags:
  - API
  - AudioContext
  - BaseAudioContext
  - Method
  - Reference
  - Web Audio API
  - createBiquadFilter
browser-compat: api.BaseAudioContext.createBiquadFilter
---

{{ APIRef("Web Audio API") }}

The `createBiquadFilter()` method of the {{ domxref("BaseAudioContext") }}
interface creates a {{ domxref("BiquadFilterNode") }}, which represents a second order
filter configurable as several different common filter types.

> **Note:** The {{domxref("BiquadFilterNode.BiquadFilterNode", "BiquadFilterNode()")}} constructor is the
> recommended way to create a {{domxref("BiquadFilterNode")}}; see
> [Creating an AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode).

## Syntax

```js
createBiquadFilter()
```

### Parameters

None.

### Return value

A {{domxref("BiquadFilterNode")}}.

## Examples

The following example shows basic usage of an AudioContext to create a Biquad filter
node. For a complete working example, check out our [voice-change-o-matic](https://mdn.github.io/voice-change-o-matic/) demo (look
at the [source code](https://github.com/mdn/voice-change-o-matic) too).

```js
const audioCtx = new AudioContext();

//set up the different audio nodes we will use for the app
const analyser = audioCtx.createAnalyser();
const distortion = audioCtx.createWaveShaper();
const gainNode = audioCtx.createGain();
const biquadFilter = audioCtx.createBiquadFilter();
const convolver = audioCtx.createConvolver();

// connect the nodes together

source = audioCtx.createMediaStreamSource(stream);
source.connect(analyser);
analyser.connect(distortion);
distortion.connect(biquadFilter);
biquadFilter.connect(convolver);
convolver.connect(gainNode);
gainNode.connect(audioCtx.destination);

// Manipulate the Biquad filter

biquadFilter.type = "lowshelf";
biquadFilter.frequency.setValueAtTime(1000, audioCtx.currentTime);
biquadFilter.gain.setValueAtTime(25, audioCtx.currentTime);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
