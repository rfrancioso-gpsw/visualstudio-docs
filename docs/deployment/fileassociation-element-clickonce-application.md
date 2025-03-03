---
title: "&lt;fileAssociation&gt; Element (ClickOnce Application)"
description: The fileAssociation element identifies a file extension to be associated with the application. The fileAssociation element is optional.
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords:
  - "<fileAssociation> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], fileAssociation element"
author: mikejo5000
ms.author: mikejo
manager: mijacobs
ms.subservice: deployment
---
# &lt;fileAssociation&gt; element (ClickOnce application)

Identifies a file extension to be associated with the application.

## Syntax

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## Elements and attributes
 The `fileAssociation` element is optional. The element has the following attributes.

|Attribute|Description|
|---------------|-----------------|
|`extension`|Required. The file extension to be associated with the application.|
|`description`|Required. A description of the file type for use by the shell.|
|`progid`|Required. A name uniquely identifying the file type.|
|`defaultIcon`|Required. Specifies the icon to use for files with this extension. The icon file must be specified by using the [\<file> Element](../deployment/file-element-clickonce-application.md) within the [\<assembly> Element](../deployment/assembly-element-clickonce-application.md) that contains this element.|

## Remarks
 This element must include an XML namespace reference to "urn:schemas-microsoft-com:clickonce.v1". If the `<fileAssociation>` element is used, it must come after the `<application>` element in its parent [\<assembly> Element](../deployment/assembly-element-clickonce-application.md).

 ClickOnce will not overwrite existing file associations. However, a ClickOnce application can override the file extension for the current user only. After that ClickOnce application is uninstalled, ClickOnce deletes the file association for the user, and the per-machine association is active again.

## Example
 The following code example illustrates `fileAssociation` elements in an application manifest for a text editor application deployed using ClickOnce. This code example also includes the [\<file> Element](../deployment/file-element-clickonce-application.md) required by the `defaultIcon` attribute.

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## See also
- [ClickOnce application manifest](../deployment/clickonce-application-manifest.md)