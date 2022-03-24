---
sidebar_position: 20
---

# Anatomy of a plugin

The [`Plugin`](api/../../api/classes/Plugin_2.md) class defines the lifecycle of a plugin and exposes the operations available to all plugins:

```ts {1,3} title="main.ts"
import { Plugin } from "obsidian";

export default class ExamplePlugin extends Plugin {
  async onload() {
    // Configure resources needed by the plugin.
  }
  async onunload() {
    // Release any resources configured by the plugin.
  }
}
```

## Plugin lifecycle

[`onload()`](../api/classes/Component.md#onload) runs whenever Obsidian the user starts using the plugin. This is where you'll configure most of the plugin's capabilities.

[`onunload()`](../api/classes/Component.md#onunload) runs when the plugin is disabled. Any resources that your plugin is using must be released here to avoid affecting the performance of Obsidian after your plugin has been disabled.

To better understand when these methods are called, you can print a message to the console whenever the plugin loads and unloads. The console is a valuable "behind the scenes" tool for developers to use to monitor the status of their code. To view the console, press ctrl-shift-i in Windows/Linux, or cmd-option-i on the Mac. Click on the Console Tab in the resultant side window that appears. 

```ts {5,8} title="main.ts"
import { Plugin } from "obsidian";

export default class ExamplePlugin extends Plugin {
  async onload() {
    console.log('loading plugin')
  }
  async onunload() {
    console.log('unloading plugin')
  }
}
```
