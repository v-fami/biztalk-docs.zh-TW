---
title: 使用外部組件指令碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Scripting functoids, warnings
- Scripting functoids, external assemblies
ms.assetid: 0bdf6adc-91b9-462e-8fd0-9cb48bfa7817
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 475a3b9781eecb0ccc79165bbe54e6dfd542ecfc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269198"
---
# <a name="scripting-using-external-assemblies"></a>使用外部組件的指令碼處理
使用外部組件的指令碼處理是 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用指令碼處理的慣用方式。 外部組件提供數個優點：  
  
-   輕鬆共用程式碼  
  
-   維護更簡便  
  
-   更容易偵錯  
  
> [!NOTE]
>  測試對應失敗時，如果**指令碼處理**運算質所使用的外部組件未登錄在 GAC 中。 它適用於外部組件位於相同的 bin 資料夾，做為目前專案的組件 （放置在建置之後）。  
  
 重複使用指令碼只需要設定**指令碼**屬性**指令碼處理**運算質。 因為指令碼儲存在對應的外部，所以您不需要變更對應就可以修改指令碼。 而且您可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 偵錯工具的完整陣列，確定指令碼是否正確執行。  
  
> [!WARNING]
>  外部組件中的程式碼必須是安全執行緒。 在負荷條件下，對應的多個執行個體可能會同時執行。  
  
 在 外部組件中的範例函式，請參閱[（BizTalk Server 範例資料夾） 的 XML 工具](../core/xml-tools-biztalk-server-samples-folder.md)。  
  
## <a name="see-also"></a>另請參閱  
 [指令碼處理運算質](../core/scripting-functoid.md)   
 [使用內嵌 C#、 JScript.NET 和 Visual Basic.NET 指令碼](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)   
 [使用內嵌 XSLT 與 XSLT 呼叫範本指令碼](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [如何新增指令碼運算質至對應](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)