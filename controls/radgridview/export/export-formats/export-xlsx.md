---
title: ExportToXlsx
page_title: ExportFormat.Xlsx
description: ExportFormat.Xlsx
slug: gridview-export-xlsx
tags: exportformat.xlsx
published: True
position: 1
---

# ExportToXlsx

* [Assembly References](#assembly-references)

* [Method Overloads](#method-overloads)

* [Export Default Styles](#export-default-styles)

* [Disable Column's Width Auto Fit](#disable-column-width-auto-fit)

* [Events](#events)

The __ExportToXlsx__ method allows exporting to "Xlsx" format. As the mechanism uses **RadSpreadProcessing** internally, there is no need for the user to make the integration manually. The method was introduced in __Q1 2015__.

## Assembly References

The __ExportToXlsx__ method uses additional libraries so you need to add references to the following assemblies:

* Telerik.Windows.Documents.Core.dll
* Telerik.Windows.Documents.Spreadsheet.dll 
* Telerik.Windows.Documents.Spreadsheet.FormatProviders.OpenXml.dll
* Telerik.Windows.Zip.dll
* Telerik.Windows.Controls.GridView.Export.dll

>  __Telerik.Windows.Controls.GridView.Export.dll__ is a new binary introduced in __Q1 SP of 2015__. It delimits the exporting to __Xlsx__ functionality from __Telerik.Windows.Controls.GridView.dll__, so in order to use __ExportToXlsx__ method, the new dll should also be added.

## Method Overloads

1. __ExportToXlsx(Stream stream)__ - Expects the specified stream to which you are exporting data to.

2. __ExportToXlsx(Stream stream, GridViewDocumentExportOptions options)__ - Expects the specified stream to which you are exporting data to and parameter of type GridViewDocumentExportOptions. The latter is used to set the following export options:

* Culture
* Items
* ShowColumnFooters
* ShowGroupFooters
* ShowColumnHeaders
* ExportDefaultStyles  
* ExcludedColumns

The following example shows how to use the method on a button click:

#### __[C#] Example 1: Use of ExportToXlsx Method__
	private void btnExport_Click(object sender, RoutedEventArgs e)
	{
	    string extension = "xlsx";
	
	    SaveFileDialog dialog = new SaveFileDialog()
	    {
	        DefaultExt = extension,
	        Filter = String.Format("{1} files (*.{0})|*.{0}|All files (*.*)|*.*", extension, "Excel"),
	        FilterIndex = 1
	    };
	
	    if (dialog.ShowDialog() == true)
	    {
	        using (Stream stream = dialog.OpenFile())
	        {
	            gridViewExport.ExportToXlsx(stream,
	                new GridViewDocumentExportOptions()
	                {
	                    ShowColumnFooters = true,
	                    ShowColumnHeaders = true,
	                    ShowGroupFooters = true
	                });
	        }
	    }
	}


## Export Default Styles

>To export the Default Styles of RadGridView in grouped state, at least one row must be expanded, so that the exporting engine can get the styles.

RadGridView can be exported with its default styles by setting the __ExportDefaultStyles__ property to __True__

By default the ExportDefaultStyles property is set to false. You can see the result (Figure 1).

#### __Figure 1: Exporting with ExportDefaultStyles set to “false” (default)__
![ExportDefaultStyles false](../images/exportdefaultstyles.png)

You can set the __ExportDefaultStyles__ value to __“true”__ and see the result (Figure 2).

#### __[C#] Example 2: Configuring ExportDefaultStyles Setting__

	gridViewExport.ExportToXlsx(stream,
	    new GridViewDocumentExportOptions()
			{
			    ShowColumnHeaders = true,
			    ShowColumnFooters = true,
			    ShowGroupFooters = true,
			    ExportDefaultStyles = true
			});   

#### __Figure 2: Exporting with ExportDefaultStyles set to True__
![ExportDefaultStyles false](../images/exportdefaultstyles2.png)

## Disable Column Width Auto Fit

__GridViewDocumentExportOptions__ expose the boolean __AutoFitColumnsWidth__ property. Its default value is __True__, meaning that the column's width will be automatically fit based on its content. To disable this behavior, its value can be set to __False__.

#### __[C#] Example 3: Setting the AutoFitColumnsWidth Property to False__

	if (dialog.ShowDialog() == true)
	{
	    using (Stream stream = dialog.OpenFile())
	    {
	        gridViewExport.ExportToXlsx(stream,
	            new GridViewDocumentExportOptions()
	            {
	                ShowColumnHeaders = true,
	                ShowColumnFooters = true,
	                ShowGroupFooters = true,
	                ExportDefaultStyles = true,
	                AutoFitColumnsWidth = false
	            });
	    }
	}

#### __Figure 3: Exporting with AutoFitColumnsWidth set to False__
![AutoFitColumnsWidth false](../images/autofitcolumnswidth.png)

## Events

There are two events related to the exporting of RadGridView with the ExportToXlsx method: *ElementExportingToDocument* and *ElementExportedToDocument*. You can find more information regarding them in the [Export Events]({%slug gridview-export-events%}) section.

## How to

* __[Get the Column of the Corresponding Cell]({%slug gridview-troubleshooting-cell-column%})__

* __[Disable the Export of a Particular Column]({%slug gridview-troubleshooting-disable-column-export%})__

* **[Style Exported XLSX & PDF Documents]({%slug gridview-export-style-exported-xlsx-pdf-documents%})**


## See Also

 * [RadGridView Overview]({%slug gridview-overview2%})

 * [Export]({%slug gridview-export%})

 * [Export Async]({%slug gridview-export-async%})

 * [Export Events]({%slug gridview-export-events%})
