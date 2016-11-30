
# Excel-Add-in-JS-WoodGrove-Expense-Trends

The **WoodGrove** Bank Expense Trends add-in **demonstrates** how you can use the new JavaScript API for Microsoft Excel 2016 to create **a compelling Excel add-in.** With Expense Trends, you can import expense transactions into the, workbook, create dashboard and trackers, view and analyze *trends,* and track special transactions such as charitable *donations* and follow up items. *The sample provides two experiences:* one with task pane and another with add-in commands. The following figures show the main screens of this add-in.

With Expense Trends, you can import expense transactions into the workbook, create dashboard and trackers, view and analyze trends, and track special transactions such as charitable donations and follow up items. The *sample provides two* experiences: one with task pane and another with add-in commands. *The following figures show the main screens of this add-in.*

*Applies to: Excel 2016, Excel for iPad, Excel for Mac*


## Table of Contents

* [Prerequisites](#prerequisites) 
* [Properties](#properties) 
* [Relationships](#relationships) 
* [Method details](#method-details) 

## Prerequisites

You'll need:

* [Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) 
* [Office Developer Tools for Visual Studio](https://www.visualstudio.com/en-us/features/office-tools-vs.aspx) 
* Excel 2016, version 6769.2011 or later

## Properties

| **Property** | **Type** | **Description** | 
|:--|:--|:--|
| style | string | Gets or sets the style used for the body. This is the name of the pre-installed or custom style. | 
| text | string | Gets the text of the body. Use the **insertText** method to insert text. Read-only. | 
| name | string | Gets the name of the element. | 

## Relationships

| **Relationship** | **Type** | **Description** | 
|:--|:--|:--|
| contentControls | [ContentControlCollection](https://github.com/OfficeDev/office-js-docs/blob/master/reference/word/contentcontrolcollection.md)  | Gets the collection of rich text content control objects that are in the body. Read-only. | 
| font | [Font](https://github.com/OfficeDev/office-js-docs/blob/master/reference/word/font.md)  | Gets the text format of the body. Use this to get and set font name, size, color, and other properties. Read-only. | 
| inlinePictures | [InlinePictureCollection](https://github.com/OfficeDev/office-js-docs/blob/master/reference/word/inlinepicturecollection.md)  | Gets the collection of inlinePicture objects that are in the body. The collection does not include floating images. Read-only. | 
| paragraphs | [ParagraphCollection](https://github.com/OfficeDev/office-js-docs/blob/master/reference/word/paragraphcollection.md)  | Gets the collection of paragraph objects that are in the body. Read-only. | 
| parentContentControl | [ContentControl](https://github.com/OfficeDev/office-js-docs/blob/master/reference/word/contentcontrol.md)  | Gets the content control that contains the body. Returns null if there isn't a parent content control. Read-only. | 

## Method details


### clear()

Clears the contents of the body object. The user can perform the undo operation on the cleared content.


#### Syntax

```
bodyObject.clear();
```

#### Parameters

None


#### Returns

void


#### Examples

```
// Run a batch operation against the Word object model.
Word.run(function (context) {
 
    // Create a proxy object for the document body.
    var body = context.document.body;
 
    // Queue a commmand to clear the contents of the body.
    body.clear();
 
    // Synchronize the document state by executing the queued commands,
    // and return a promise to indicate task completion.
    return context.sync().then(function () {
        console.log('Cleared the body contents.');
    });
})
.catch(function (error) {
    console.log("Error: " + JSON.stringify(error));
    if (error instanceof OfficeExtension.Error) {
        console.log("Debug info: " + JSON.stringify(error.debugInfo));
    }
});
```
The [Silly stories](https://aka.ms/sillystorywordaddin)  add-in sample shows how the **clear** method can be used to clear the contents of a document.


## Support details

Use the [requirement set](https://msdn.microsoft.com/EN-US/library/office/mt590206.aspx)  in run time checks to make sure your application is supported by the host version of Word. For more information about Office host application and server requirements, see [Requirements for running Office Add-ins](https://msdn.microsoft.com/EN-US/library/office/dn833104.aspx) 


##### List One: top level is bullets

* First bullet
* Second bullet
    1. First item in numeric sublist
    1. Second item in numeric sublist
* Third bullet



##### List Two: top level is numeric

1. First numeric item
    * First item in bulleted sublist
    * Second item in bulleted sublist
        1. Item in numeric sub-sublist
        1. Another item in numeric sub-sublist
1. Second numeric item
1. Third numeric item



##### List Three: nine levels (the maximum)


        1. Third level is numeric
            1. Fourth level is numeric
                * Fifth level is bullet
                    1. Sixth level is numeric
                        * Seventh is bullet
                            1. Eighth is numeric
                                * Ninth is bullet

