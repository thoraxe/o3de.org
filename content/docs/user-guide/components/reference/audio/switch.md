---
title: Audio Switch
description: Use the Audio Switch component to set up a default switch and switch states for an entity in O3DE.
toc: true
---

The **Audio Switch** component provides basic [Audio Translation Layer (ATL)](/docs/user-guide/interactivity/audio/audio-translation-layer) switch functionality. With switches (and switch states), you can specify the state of an entity. The audio middleware interprets states, modifies the behavior of sounds, and plays the appropriate sounds.

## Audio Switch Properties

The Audio Switch component has the following properties:

**Default Switch**
Enter the name of the audio switch to use by default. You can associate any audio switch with the entity.

**Default State**
Enter the name of the audio switch state to use by default. Use the [Audio Controls Editor](/docs/user-guide/interactivity/audio/audio-controls-editor) to assign the state to the switch. When this component is activated, the default switch is set to the default state.

## EBus Request Bus Interface

Use the following request functions with the EBus interface to communicate with other components of your game.

For more information about using the Event Bus (EBus) interface, see [Working with the Event Bus (EBus) system](/docs/user-guide/engine/ebus).

### SetState

Sets the specified state of the default switch.

**Parameters**
`stateName` - Name of the state to set

**Return**
None

**Scriptable**
Yes

### SetSwitchState

Sets a specified switch to a specified state.

**Parameters**
`switchName` - Name of the switch to set
`stateName` - Name of the state to set

**Return**
None

**Scriptable**
Yes
