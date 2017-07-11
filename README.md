# card-sample-shared-toggle

## Instructions

Here are the steps used to create this card component from scratch:

* Create a new repository in GitHub named ChannelElementsTeam/card-sample-shared-toggle and clone it to your local machine

* If you have not already done so, install polymer-cli.  Note that you may need to use `sudo` depending on your machine.

```
npm install -g polymer-cli
```

* Open a shell and set the current working directory to the root folder of this repository

* `polymer init` and select the default options (including that this is a "component")

* Because this is a component that will be sharing state between cards, we are using the distributed-state-controller, and it needs to be added as a dependency.  Also, we'll use a couple of Polymer standard web components in our user interface.

```
bower install --save distributed-state-controller
bower install --save PolymerElements/paper-toggle-button
bower install --save PolymerElements/paper-button
```

* The `polymer-cli init` command created a default initial implementation of a web component.  But a Channels component consists of two web components -- one for composing and a second one for viewing.  Replace the contents of the [card-sample-shared-toggle.html](./card-sample-shared-toggle.html) file to contain declarations for these two components.

* Create a new file called channels-component.json which is used by Channels to know which web components to use when composing and viewing:

```json
{
  "composerTag": "card-sample-shared-toggle-composer",
  "viewerTag": "card-sample-shared-toggle-viewer"
}
```

* To make it easier to refine your layouts, you can take advantage of polymer-cli's ability to host your component during development.  Since it was designed to handle a single component, you need to update [demo/index.html](./demo/index.html) so that the composer and viewer components will be shown. 

```html
<demo-snippet>
  <template>
    <div style="width:400px;border:1px solid #ccc;margin:25px 0;padding:5px;">
      <card-sample-shared-toggle-composer></card-sample-shared-toggle-composer>
    </div>
    <div style="width:400px;border:1px solid #ccc;margin:25px 0;padding:5px;">
      <card-sample-shared-toggle-viewer></card-sample-shared-toggle-viewer>
    </div>
  </template>
</demo-snippet>
```

* To see your composer and viewer on a webpage while developing, run:

```
polymer serve
```

Copy the "reusable components" URL that is returned and paste it into your browser.  You should see your composer and viewer displayed inside a test card.

This will start a local webserver with file mappings to create the appropriate environment for viewing your components.  Note, however, that the 'channel' object is not initialized so calling methods on that object will not work.  So this is mainly to help with visual layout.

* Update [bower.json](./bower.json) and add an "ignore" section so that only essential files are included:

```json
  ...
  "ignore": [
      "**/.*",
      "node_modules",
      "bower_components",
      "test",
      "demo"
    ]
```

* Tell Git to ignore everything under `bower_components` folder

* Commit changes and push to the GitHub repository

* Open a Channels-compliant client, create a test channel, click to set the composer, select "Import a component", and enter `ChannelElementsTeam/card-sample-shared-toggle`

