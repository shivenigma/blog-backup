## Chrome dev tools: File drop event bug that cost me hours in debugging

I was working on my [Kindle highlights utility](https://kindle-highlights-extractor.vercel.app/). It is a simple app that mainly has a file upload and some text parsing. I finished the basic app with file browser and wanted to implement file upload by drag and drop.

It was something I did multiple times but I don't recall encountering this issue before. I configured the `ondrop` Event, added `preventDefault`, and even added `dragOver` event handler. The dragOver event handler is also necessary for the drop to work properly. But when I log the event inside the drop callback, the `event.dataTransfer` array was always empty even if I dropped a valid file. Try selecting a file by click and by dropping in the embedded Codepen below.

%[https://codepen.io/ShivEnigma/pen/PojXwgy]

The file variable will log the file in both cases, but the `event.dataTransfer` will be empty on a drop. This might seem like a small thing, but I wasted good amount of my utility building time into debugging why the file is not being uploaded when it is dropped.

Finally I just went ahead and wrote the `event.dataTransfer.files[0]` and assigned it to the file variable and it was working. So the issue is not in my code, the console is behaving weirdly in case of a drop Event.

With a quick search, I found I'm not alone. There are lot of people reported this issue under lot of open source projects such as Dart and Electron. But the issue truly seems to be coming from Chromium. I tried to find if there is an existing chromium bug but couldn't find any.

The same Codepen works well in Firefox and dropEvent has files inside it. For now I'm just putting this here so someone facing this might waste lesser time than me.