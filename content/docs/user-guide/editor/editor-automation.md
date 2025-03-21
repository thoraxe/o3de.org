---
description: ' Use the features of the Python Editor Bindings gem to automate actions
  and tasks inside of the O3DE Editor. '
title: Automating the O3DE Editor with the Python Editor Bindings gem
---

{{< preview-migrated >}}

 Some tasks in the O3DE Editor are tedious or could easily be automated, and to support that, O3DE has support for scripting the editor through Python bindings to the underlying editor implementation. These bindings are enabled with the **PythonEditorBindings** gem, and interacted with through a Python 3 library embedded within the editor. You can access a Python REPL through an in-editor console, or launch the editor with an argument that loads and runs a Python script on boot.

## Enable editor automation 

 Editor automation is enabled by selecting the **PythonEditorBindings** gem for your project, and then rebuilding the editor. No specific configuration (debug, profile, release) is required to enable the Python bindings. Because the bindings are enabled through a gem that you select for your project, you'll need to make sure that this gem is enabled for *all* projects that you intend to use automation with.

## Use editor automation 

 The easiest way to get started with editor automation is to use the REPL that's available from within the O3DE Editor and try out some commands. Open this REPL by selecting **Tools** > **Other** > **Python Console**. The Python console opens in a new editor view, which gives you access to a console that displays output from Python, the REPL input, and a full reference of available commands. To get access to the reference, select the **?** icon in the lower-right corner of the console.

 You can also access a set of available scripts, including some samples for common tasks in the editor, by selecting **Tools** > **Other** > **Python Scripts**. These scripts are stored in a directory depending on their scope. Scripts only for your project are stored in the `Editor\Scripts` directory, and scripts meant to be used along with a gem are stored at `Gems\<name>\Editor\Scripts`.

 Editor automation is driven primarily through the event bus (EBus) system. Before working with the editor bindings, you should become familiar with the basics of EBus from [Working with the Event Bus (EBus) system](/docs/user-guide/engine/ebus/_index.md). To learn about some of the specific buses used by the editor automation system, take a look at the [Python Editor Bindings gem examples](/docs/user-guide/editor/editor-automation-examples.md).
