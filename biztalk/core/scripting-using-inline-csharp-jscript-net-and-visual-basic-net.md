---
title: "使用內嵌 C#、 JScript.NET 和 Visual Basic.NET 指令碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scripting functoids, JScript
- Scripting functoids, warnings
- Scripting functoids, Visual Basic .NET
- Scripting functoids, inline C#
- Scripting functoids, .NET
ms.assetid: dda60024-58bd-483f-a750-31b21059eded
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe2002bd92342a953406a21e076b801d3e90b938
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="scripting-using-inline-c-jscript-net-and-visual-basic-net"></a>使用內嵌 C#、JScript .NET 以及 Visual Basic .NET 的指令碼處理
對於您不想在應用程式之其他地方使用的自訂程式碼而言，內嵌指令碼非常方便。  
  
 BizTalk 會在定義對應的可延伸樣式表語言轉換 (XSLT) 樣式表中儲存內嵌指令碼。 因此，內嵌指令碼可以將相同的命名空間當成任何其他 XSLT 樣式表指令碼。 下表顯示可用的命名空間。  
  
|命名空間|Description|  
|---------------|-----------------|  
|系統|系統類別。|  
|System.Collection|集合類別。|  
|System.Text|文字類別。|  
|System.Text.RegularExpressions|規則運算式類別。|  
|System.Xml|核心 XML 類別。|  
|System.Xml.Xsl|XSLT 類別。|  
|System.Xml.Xpath|XPath 類別。|  
|Microsoft.VisualBasic|Visual Basic 指令碼類別。|  
  
 如需有關命名空間和資料類型的詳細資訊，搜尋"XSLT 樣式表指令碼處理使用\<msxsl: script\>"和"System.Xml.Xsl.XslCompiledTransform".NET Framework 集合中。  
  
> [!CAUTION]
>  請避免重複使用相同的方法簽章。 數個指令碼處理運算質具有相同的方法簽章時，BizTalk 會選取第一個實作，並捨棄其他實作。  
  
 除了對一次指令碼相當方便以外，內嵌指令碼對於在一些指令碼之間宣告全域變數而言也相當有用。 例如，在 C# 內嵌指令碼中，您可以將下列程式碼行放在任何類別外部。  
  
```  
ArrayList statusList = new ArrayList();  
```  
  
 這會建立**ArrayList**， `statusList`，可在對應中的所有內嵌指令碼。  
  
 內嵌指令碼範例，請參閱[（BizTalk Server 範例資料夾） 的 XML 工具](../core/xml-tools-biztalk-server-samples-folder.md)。  
  
## <a name="see-also"></a>請參閱  
 [指令碼處理運算質](../core/scripting-functoid.md)   
 [使用外部組件指令碼](../core/scripting-using-external-assemblies.md)   
 [使用內嵌 XSLT 與 XSLT 呼叫範本指令碼](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [如何新增指令碼運算質至對應](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)