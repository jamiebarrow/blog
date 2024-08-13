# 2013-02-13 Where did my Visio BMPN stencils go?

tags: BPMN, Visio, Visio Stencils

For some reason, when opening up a saved Visio diagram that uses the BPMN stencils, these no longer show up in the Shapes window.

To get them back, click on `More Shapes > Open Stencil...` then find the Visio content directory, in my case this is `C:\Program Files\Microsoft Office\Office14\Visio Content\1033`, and then enter `BPMN*_M.vss` to show only the metric BPMN stencils. Select them all, then click `Open`.

I have no idea why it isn't stored with the document somehow. Apparently if you go to `File > Info > Properties > Advanced Properties` and then check the `Save workspace` option, then it should save things like this, but that's checked for me and it doesn't. Maybe because it's the Professional version and not the Premium version, but I doubt it. Sounds like a bug to me.
