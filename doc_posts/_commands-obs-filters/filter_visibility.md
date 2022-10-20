---
title: "Filter Change Visibility"
num: 2
---
Changes visibility of a filter in a given source.\
It is highly recommended to use True and False. 

{% include alert.html text="Changing filter visibility on sources inside groups is very inconsistent. It's recommended to use nested scenes instead." type="warning
" %} 

| Box Name | Type | Description | 
|-------|--------|--------
|OBS|Dropdown|OBS to send this command to (if using multiple OBS)|
|Source	|String	| Source name containing the filter
|Filter	|String	| Filter name to change the visibility
|Visible|checkbox| checked = visible, unchecked = not visible
{:class='table table-primary'}









