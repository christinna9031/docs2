---
title: "Introduction"
num: 0
---


A buffer is basically a space within the system memory that is used to store small packets of data for just about anything. Since it is held in system memory, it is very fast to access. You can think of it as a temporary place to put things that need to be worked on or processed.

{% include image.html w="75" src="Buffer_Memory.png" alt="Buffer within memory" %}

You can save and load *ANY* file into a buffer in SAMMI, which is the best part about having buffer commands!\
For example, SAMMI does not natively support text files, but that's okay, because you can simply load, read and save any text file using buffers instead!

{% include alert.html text="A buffer will exist until you either manually delete it or restart SAMMI." type="warning" %}

**Data Types**

| Buffer Type | Description |
|-------|--------
| Unsigned 8bits | A single byte value. This is a positive value from 0 to 255.
| Signed 8bits | A single byte value. This can be a positive or negative value from -128 to 127 (0 is classed as positive).
| Unsigned 16bits | 2 bytes value. This is a positive value from 0 to 65,535.
| Signed 16bits | 2 bytes value. This can be a positive or negative value from -32,768 to 32,767 (0 is classed as positive).
| Unsigned 32bits | 4 bytes value. This is a positive value from 0 to 4,294,967,295.
| Signed 32bits | 4 bytes value. This can be a positive or negative value from -2,147,483,648 to 2,147,483,647 (0 is classed as positive).
| Float 32bits | 4 bytes value. This can be a positive or negative value from -2,147,483,648 to 2,147,483,647 that can contain decimal point numbers.
| Float 64bits |8 bytes value. This can be a positive or negative value from 1-2^63 and 2^63 that can contain decimal point numbers.
| Boolean | A boolean value. Can only be either 1 or 0 (true or false).
| String | A string (text), finalized with a null terminating character.
| Text | A string(text) without the final null terminating character. Cannot be used for Buffer: Peak or Read commands (as the the length of a string is found by searching for the (first) null.)
{:class='table table-primary w-auto table-hover'}









