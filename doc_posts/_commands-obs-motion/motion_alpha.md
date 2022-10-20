---
title: "Motion: Alpha Filter"
num: 6
---
Gradually changes the transparency of a source over a set duration.\
Requires a Color Correction filter to be added to your source.\
This way you can gradually fade out a source before turning its visibility completely off and gradually fade in a source after turning its visibility on.

{% include alert.html text="Older Color Correction filters require 0-100 range, however newer ones require 0-1 range." type="warning" %} 

| Box Name | Type | Description | 
|-------|--------|--------
|OBS|Dropdown|OBS to send this command to (if using multiple OBS)|
|Source Name |	String	Source name to change the transparency of.
|Filter	|String	| Filter name to change the visibility
|Color Correction	| String|	Color Correction filter name.
|Alpha Start |	Real{% include asterisk.html%}|	Starting transparency percentage. 0-100 or 0-1 depending on the filter's version.
|Alpha End |	Real{% include asterisk.html%}|	Final transparency percentage. 0-100 or 0-1 depending on the filter's version.
|Duration(ms) |	Int {% include asterisk.html%}|	Transition duration in milliseconds
{:class='table table-primary'}









