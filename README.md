# SimpleEQ (JUCE, C++)

A three-band EQ plugin I'm building with the [JUCE](https://juce.com) framework, as a hands-on way to learn audio DSP and plugin architecture in C++.

> **Status: work in progress.** The filter chain and parameters work; the editor is still a basic slider layout. It isn't packaged or released as a finished plugin.

## What's implemented

- **Low-cut and high-cut filters** with selectable slopes of 12, 24, 36 or 48 dB/oct, built by chaining up to four IIR filters.
- **Peak filter** with frequency, gain and Q (quality) controls.
- Parameters managed with `AudioProcessorValueTreeState`, so the processor and the editor stay in sync and settings can be saved with a session.
- Separate left and right processing chains (`juce::dsp::ProcessorChain`), prepared with a `ProcessSpec` and updated from the parameter values on every block.
- Editor with sliders attached to every parameter.

## Code tour

- [`Source/PluginProcessor.h`](Source/PluginProcessor.h): the `Slope` enum, `ChainSettings`, the filter chain types and the helpers that update the cut filters.
- [`Source/PluginProcessor.cpp`](Source/PluginProcessor.cpp): parameter layout, `prepareToPlay`, the per-block filter updates and `processBlock`.
- [`Source/PluginEditor.cpp`](Source/PluginEditor.cpp): slider attachments and layout.

## Building

Open `SimpleEQ.jucer` in the Projucer, export for your IDE (Xcode or Visual Studio), and build the plugin target.

## Next steps

- A frequency response curve drawn in the editor.
- A cleaner custom look for the sliders.
- Testing in a DAW and packaging a VST3/AU build.

---

More of my work: [deniztugluaudio.com](https://deniztugluaudio.com) · [GitHub](https://github.com/deniztuglu)

## License

My code is MIT licensed (see [LICENSE](LICENSE)). JUCE itself is not included here and is covered by its own license; see [juce.com](https://juce.com/get-juce/).
