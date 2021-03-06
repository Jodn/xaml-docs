---
title: Getting Started
page_title: Getting Started
description: Getting Started
slug: virtualgrid-getting-started2
tags: getting,started
published: True
position: 0
---

# Getting Started

This tutorial will walk you through the required steps for using __RadVirtualGrid__. 

* [Assembly References](#assembly-references)
* [Adding RadVirtualGrid to the Project](#adding-radvirtualgrid-to-the-project)
* [Populating with Data](#populating-with-data)
* [Setting Initial Row and Column Count](#setting-initial-row-and-column-count)
* [Resetting the Capacity to the Initial Row and Column Count](#resetting-the-capacity-to-the-initial-row-and-column-count)
* [Populating with Data through DataProvider](#populating-with-data-through-dataprovider)

## Assembly References

In order to use __RadVirtualGrid__ in your application, you need to add references to the following assemblies:

* __Telerik.Windows.Controls__
* __Telerik.Windows.Controls.VirtualGrid__
* __Telerik.Windows.Data__

## Adding RadVirtualGrid to the Project

#### __[XAML] Example 1: Defining RadVirtualGrid Declaratively__

	 <telerik:RadVirtualGrid x:Name="VirtualGrid"/>

## Populating with Data

> In order the control to be populated with data, its [InitialRowCount and InitialColumnCount](#setting-initial-row-and-column-count) properties need to be set

The control populates its data through the __CellValueNeeded__ event. It is raised when the control is initially loaded and when newly data is about to be loaded on demand when the user scrolls horizontally or vertically. The event arguments expose the following properties:

### CellValueNeeded

* __CellIndex__: Provides information regarding the index of the currently loaded cell

* __RowIndex__: Provides information regarding the index of the currently loaded row

* __Value__: Through it the needed value for the respective cell can be set

### HeaderValueNeeded

Through this event the appearance of the row and column headers can be controlled. The event arguments provide the following properties:

* __HeaderOrientation__: Enumeration through which has two values: __Horizontal__ and __Vertical__. The first one sets the value to the Row Header, whereas the second one sets the value to the Column Header

* __Index__: Sets the index of the Header

* __Value__: The actual value to be applied to the Header

## Setting Initial Row and Column Count

The control needs to be initially populated with fixed amount of rows and columns. The below listed properties are exposed for achieving this. An important note is that when additional rows or columns are  added at runtime, the values of these properties remain unmodified, but the capacity of the control increases. More information on inserting rows and columns can be found in the [Insert and Remove Data]({%slug virtualgrid-insert-data-and-remove-data%}) topic.

* __InitialRowCount__: Gets or sets the amount of initially loaded rows

* __InitialColumnCount__: Gets or sets the amount of initially loaded columns

## Resetting the Capacity to the Initial Row and Column Count

As inserting rows and columns does not affect the __InitialRowCount__ and __InitialColumnCount__ properties, __RadVirtualGrid__ supports resetting its capacity to the values that are set to them. This can be done through the following methods:

* __Reset()__: Resets the capacity of the control to the values of the __InitialRowCount__ and __InitialColumnCount__ properties

* __Reset(int rowCount, int columnCount)__: Through this overload of the Reset method, the capacity of __RadVirtualGrid__ can be reset to values different from the ones initially set to the __InitialRowCount__ and __InitialColumnCount__ properties. Furthermore, the two properties will be updated accordingly.

## Populating with Data through DataProvider

Instead of using the __CellValueNeeded__ event, __RadVirtualGrid__ provides an option to populate its data through the built-in __DataProvider__ mechanism. The __DataProvider__ object accepts an IEnumerable through its constructor and can be applied to __RadVirtualGrid__ through its relevant property.

#### __[C#] Example 2: Applying a DataProvider__

	this.VirtualGrid.DataProvider = 
    	new Telerik.Windows.Controls.VirtualGrid.DataProvider(this.myCollection);

> The __DataProvider__ mechanism is intended to cover basic scenarios for populating the control with data. For extending the default behavior, __RadVirtualGrid__ provides support for [Custom DataProvider]({%slug virtualgrid-custom-dataprovider%})

## See also

* [Editing]({%slug virtualgrid-editing%})

* [Insert and Remove Data]({%slug virtualgrid-insert-data-and-remove-data%})

* [Pinned Rows and Columns]({%slug virtualgrid-pinned-rows-and-columns%})

* [Custom Data Provider]({%slug virtualgrid-custom-dataprovider%})



