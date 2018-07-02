---
title: 配接器當地語系化問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d200ce9-1a60-455b-88b0-6ec86092a786
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c829ce496c124f3333c353f481eb3958e29d5c77
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996335"
---
# <a name="adapter-localization-issues"></a><span data-ttu-id="f8ae1-102">配接器當地語系化問題</span><span class="sxs-lookup"><span data-stu-id="f8ae1-102">Adapter Localization Issues</span></span>
<span data-ttu-id="f8ae1-103">下列主題涵蓋在開發自訂配接器時，您可能會遭遇的當地語系化問題。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-103">The following topics cover localization issues that you may encounter when developing custom adapters.</span></span>  
  
## <a name="xsd-issues"></a><span data-ttu-id="f8ae1-104">XSD 問題</span><span class="sxs-lookup"><span data-stu-id="f8ae1-104">XSD Issues</span></span>  
 <span data-ttu-id="f8ae1-105">藉由使用配接器架構，配接器開發人員可以用 XML 結構描述定義 (XSD) 結構描述來實作配接器屬性頁。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-105">By using the Adapter Framework, adapter developers can implement adapter property pages with XML Schema Definition (XSD) schemas.</span></span>  
  
 <span data-ttu-id="f8ae1-106">如果您的配接器沒有全球化或當地語系化需求，則您可以硬式編碼 XSD 結構描述字串**Getconfigschema**函式。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-106">If your adapter has no globalization or localization requirements, then you can hard code the XSD schema string inside the **IDynamicAdapterConfig:GetConfigSchema** function.</span></span>  
  
 <span data-ttu-id="f8ae1-107">如果您的配接器沒有全球化或當地語系化需求，您就可以用兩種方式之一實作 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-107">If your adapter has globalization or localization requirements, you can implement the XSD schema in one of two ways.</span></span>  
  
- <span data-ttu-id="f8ae1-108">在設計階段二進位資料的外部使用個別的 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-108">Use separate XSD files outside the design-time binary.</span></span> <span data-ttu-id="f8ae1-109">使結構描述的全部文字都成為資訊清單資源。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-109">Make the whole text of the schema a manifest resource.</span></span>  
  
- <span data-ttu-id="f8ae1-110">從資源動態地取代 [屬性名稱] 和 [描述]：</span><span class="sxs-lookup"><span data-stu-id="f8ae1-110">Dynamically replace the Property Names and Description from the resource:</span></span>  
  
  -   <span data-ttu-id="f8ae1-111">將 _locID 新增到您所要當地語系化的每個項目。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-111">Add a _locID to each element that you want to localize.</span></span>  
  
  -   <span data-ttu-id="f8ae1-112">使用 xpath 提取在結構描述中具有 _locID 屬性的所有節點。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-112">Use an xpath to pull back all the nodes in the schema that have a _locID attribute.</span></span>  
  
  -   <span data-ttu-id="f8ae1-113">查詢由 _locID 的值索引之字串的資源。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-113">Look up the resources for a string indexed by the value of the _locID.</span></span>  
  
  -   <span data-ttu-id="f8ae1-114">以結果取代節點文字。</span><span class="sxs-lookup"><span data-stu-id="f8ae1-114">Replace the node text with the result.</span></span>  
  
  <span data-ttu-id="f8ae1-115">以下是第二個選項的範例程式碼：</span><span class="sxs-lookup"><span data-stu-id="f8ae1-115">The following is sample code for the second option:</span></span>  
  
```  
string mySchema = GetSchemaFromResource(“mySchema”);  
string myLocalizedSchema = LocalizeSchemaDOM (mySchema, resourceManager);  
//  where…  
protected string GetSchemaFromResource (string name)  
{  
Assembly assem = this.GetType().Assembly;  
Stream stream = assem.GetManifestResourceStream(name);  
StreamReader reader = new StreamReader(stream);  
string schema = reader.ReadToEnd();  
return schema;  
}  
  
protected XmlDocument LocalizeSchemaDOM (string schema, ResourceManager resourceManager)  
{  
XmlDocument document = new XmlDocument();  
document.LoadXml(schema);  
XmlNodeList nodes = document.SelectNodes  
("/descendant::*[@_locID]");  
foreach (XmlNode node in nodes)  
{  
string locID = node.Attributes["_locID"].Value;  
node.InnerText = resourceManager.GetString(locID);  
}  
return document;  
}  
```