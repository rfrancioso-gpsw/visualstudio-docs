---
title: Uncommitted edits
description: Commit in-process edits on data-bound Windows Forms controls before saving data in ADO.NET applications. Call EndEdit for all BindingSource components on a form.
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
author: ghogen
ms.author: ghogen
manager: mijacobs
ms.subservice: data-tools
---
# Commit in-process edits on data-bound controls before saving data

[!INCLUDE [Data access tech note](./includes/data-technology-note.md)]

When editing values in data-bound controls, users must navigate off the current record to commit the updated value to the underlying data source that the control is bound to. When you drag items from the [Data Sources Window](add-new-data-sources.md) onto a form, the first item that you drop generates code into the **Save** button click event of the <xref:System.Windows.Forms.BindingNavigator>. This code calls the <xref:System.Windows.Forms.BindingSource.EndEdit%2A> method of the <xref:System.Windows.Forms.BindingSource>. Therefore, the call to the <xref:System.Windows.Forms.BindingSource.EndEdit%2A> method is generated only for the first <xref:System.Windows.Forms.BindingSource> that is added to the form.

The <xref:System.Windows.Forms.BindingSource.EndEdit%2A> call commits any changes that are in process, in any data-bound controls that are currently being edited. Therefore, if a data-bound control still has focus and you click the **Save** button, all pending edits in that control are committed before the actual save (the `TableAdapterManager.UpdateAll` method).

You can configure your application to automatically commit changes, even if a user tries to save data without committing the changes, as part of the save process.

> [!NOTE]
> The designer adds the `BindingSource.EndEdit` code only for the first item dropped onto a form. Therefore, you have to add a line of code to call the <xref:System.Windows.Forms.BindingSource.EndEdit%2A> method for each <xref:System.Windows.Forms.BindingSource> on the form. You can manually add a line of code to call the <xref:System.Windows.Forms.BindingSource.EndEdit%2A> method for each <xref:System.Windows.Forms.BindingSource>. Alternatively, you can add the `EndEditOnAllBindingSources` method to the form and call it before you perform a save.

The following code uses a [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) query to iterate all <xref:System.Windows.Forms.BindingSource> components and call the <xref:System.Windows.Forms.BindingSource.EndEdit%2A> method for each <xref:System.Windows.Forms.BindingSource> on a form.

## To call EndEdit for all BindingSource components on a form

1. Add the following code to the form that contains the <xref:System.Windows.Forms.BindingSource> components.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::
     ---

2. Add the following line of code immediately before any calls to save the form's data (the `TableAdapterManager.UpdateAll()` method):

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::
     ---

## Related content

- [Bind Windows Forms controls to data in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hierarchical update](../data-tools/hierarchical-update.md)
