# 2016-07-07 Updating NuGet extension on Visual Studio 2015

tags: nuget, nuget package manager, Visual Studio, Visual Studio 2015, Visual Studio extension

NuGet is pretty awesome, though for some reason the [NuGet Package Manager for Visual Studio 2015 extension](https://marketplace.visualstudio.com/items?itemName=NuGetTeam.NuGetPackageManagerforVisualStudio2015) was re-done and every time I try to update it I get an error, and then the extension seems to not work when restarting Visual Studio.

Took quite a while to figure out why, but it seems that it's to do with not being able to uninstall the old version of the extension. Extensions are installed into the folder <b>C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\Extensions</b> (or similar depending on the VS version). Certain folders in this path relate to an extension per folder.

Each time the NuGet extension tried to update, it would fail to remove the old installation, and then create a new folder for the 'upgrade'. If you tried to upgrade it a few times, you may have quite a few folders that contain the NuGet extension. When you restart VS it seems to have issues loading the extension because of this. Go through each of these to find those folders.

Close Visual Studio, and then delete each of those folders specific to the NuGet extension. Then manually download the VSIX extension installer from the website, and install it outside of Visual Studio. Once complete, start up Visual Studio and the extension should be installed properly. Whether it works or not is another thing, it seems the GUI is quite buggy with this extension, so I prefer using the Package Manager Console.

Hope this helps someone, I've had to come back to doing this a few times, so it'll definitely help me in future I'm sure :D

