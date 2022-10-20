---
title: "Change Settings"
num: 10
---
Changes settings of a source. Not to be confused with item transform settings. \
Requires the same formatting that is used in the OBS JSON file.\
Easy way to see your current source's settings is to use a Fetch OBS Data command: {% include selectAll.html text='<code>{"request-type":"GetSourceSettings","sourceName":"YOURSOURCENAME","message-id":"6666"}</code>' %}. Execute it and you will get back a JSON string of the source's settings. Paste it into a document and extract the particular value you want to use.

Use [JSON string validator](https://jsonlint.com/) if you want to make sure your formatting is correct.


| Box Name | Type | Description | 
|-------|--------|--------|
|OBS|Dropdown|OBS to send this command to (if using multiple OBS)|
|Source|	String |	Source name to change settings.
|Settings|	JSON String|	The settings to be included. Formatted as a [JSON String](https://www.w3schools.com/js/js_json_syntax.asp). Must be enclosed in `{}`.
{:class='table table-primary'}

{% include alert.html text="Pay special attention to the forward slashes / in the file paths, as it will not work if you use back slashes \ instead." type="warning" %} 

|JSON String|Description|
|-------|--------|--------|
|{% include selectAll.html text='{"url":"http://twitch.tv"}' %}|Change URL of a browser source|
|{% include selectAll.html text='{"local_file":"E:/Stream/hello.html"}' %}|Change local file path of a browser source|
|{% include selectAll.html text='{"file":"E:/Stream/image.png"}' %}|Change local file path of an image source|
|{% include selectAll.html text='{"playlist": [{"value": "E:/videos/video1.mp4"},{"value": "E:/videos/video2.mkv"}]}' %}|Change local file paths for your VLC source. Each `{"value":"X"}` represents one file.|
|{% include selectAll.html text='{"font": {"face": "Arial","flags": 8,"size": 48,"style": "Regular"}}' %}|Change font settings of your GDI+ text source. Needs to include all values.|
{:class='table table-secondary w-auto table-responsive table-hover' }









