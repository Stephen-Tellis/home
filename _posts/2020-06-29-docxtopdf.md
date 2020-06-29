---
layout: page
title:  ".docx to .pdf on Linux"
subtitle: ""
date:   2020-06-24 21:21:21 +0530
categories: ["Linux"]
---
How to convert a folder full of  .docx files to pdf on Linux with a python script? - the struggle is real.
The solution on windows is simple while using python, thanks to the handy [library](https://pypi.org/project/docx2pdf/ "Go to site").  
<br>
Unfortunately, the library requires an MS Office installation on the system. So what do we do? Use an online API? no way!   
Libre office comes to our rescue with its handy little helper scripts on bash.   
Although Libre office doesnot strictly work well with .docx files, I have personally found the conversions to be trouble free.
All that is needed now, is pass a the command.   
<br>
The general syntax is this:
```
soffice --headless --convert-to <TargetFileExtension>:<NameOfFilter> file_to_convert.xxx
```
`--headless` - Starts in "headless mode" which allows using the application without GUI.([Documentation](https://help.libreoffice.org/Common/Starting_the_Software_With_Parameters "Go to site"))   
`<TargetFileExtension>` - This will be pdf in our case.  
`<name of filter>`  - Filter names are found [here](https://cgit.freedesktop.org/libreoffice/core/tree/filter/source/config/fragments/filters "Go to site") and depends on the file you are trying to convert to. A quick `Ctrl+F` will return the result *"calc_pdf_Export"*.   

#### Here is an example  

Just open your terminal and enter the following:
```
soffice --headless --convert-to pdf:"calc_pdf_Export" name_of_doc_file.docx
```
This is for one file.   

While automating on python (Jupyter notebook), implementing this is as easy as inserting an exclamation before the command and it runs seamlessly with the script.      
```
!soffice --headless --convert-to pdf:"calc_pdf_Export" name_of_doc_file.docx
```
(This is because Jupyter Notebook executes all commands with an exclamation (!) from the underlying OS)


**Note** that although .docx-.pdf is demonstrated here, soffice is extremely powerful and supports many formats including doc-->txt, xlsx-->xlc and many others. 
Read documentation for specific applications.

Did I miss something? Improvements? Suggestions?  
Feel free to reach me on my E-mail: tellisstephen(at)gmail(dot)com

{% comment %}
Might you have an include in your theme? Why not try it here!
{% include my-themes-great-include.html %}
{% endcomment %}


