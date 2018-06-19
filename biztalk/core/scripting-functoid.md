---
title: 指令碼處理運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Scripting functoids, about Scripting functoids
- Scripting functoids
- Scripting functoids, configuring
ms.assetid: ea8353da-049b-4e0c-a700-f51708db22a3
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 822bdbc4482a7e16a7458c7c44d128967203f283
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22273334"
---
# <a name="scripting-functoid"></a>指令碼處理運算質
**指令碼處理**運算質可讓您在執行階段使用自訂指令碼或程式碼來執行無法使用的功能。 例如，您可以呼叫執行階段的.NET 組件使用**指令碼處理**運算質和撰寫您自己的自訂函式。  
  
 **指令碼處理**運算質可支援下列語言：  
  
-   C# .NET  
  
-   JScript .NET  
  
-   Visual Basic.NET  
  
-   可延伸樣式表語言轉換 (XSLT)  
  
-   XSLT 呼叫範本  
  
 另一個重要差異目前**指令碼處理**運算質和較早版本已不再需要建立並儲存在本身的運算質指令碼。 相反地，您可以建立指令碼在不同的.NET 組件和參考組件透過**指令碼**屬性。 讓指令碼在個別組件中，可讓您在一個以上的對應中使用相同的指令碼。 此外，您可以購買**指令碼處理**來自協力廠商所提供的運算質組件。  
  
 您可以使用**指令碼處理**建立在目前版本的 BizTalk 對應工具與舊版的 BizTalk 對應工具運算質。 不過，您必須先移轉運算質。 如需有關如何移轉**指令碼處理**運算質，請參閱[移轉運算質](../core/migrating-functoids.md)。  
  
 當您將加入**指令碼處理**運算質到對應，您必須設定運算質所使用的指令碼。 如果您選取**指令碼處理**運算質，**指令碼**中屬性已啟用**屬性**視窗。 如果您按一下省略符號 (**...**) 按鈕，為此屬性，**設定指令碼處理運算質**對話方塊隨即開啟。 或者，您可以按兩下**指令碼處理**運算質。  
  
 下表顯示此對話方塊的欄位。  
  
|設定指令碼處理運算質對話方塊欄位|Description|  
|---------------------------------------------------|-----------------|  
|**選取指令碼類型**|使用此欄位來選取您想要使用此指令碼的類型**指令碼處理**運算質。<br /><br /> 值：<br /><br /> -   **外部組件**。 使用此值，如果您想要關聯**指令碼處理**運算質與全域組件快取 (GAC) 中的組件。 **警告：** 外部組件中的程式碼必須是安全執行緒。 在負荷條件下，對應的多個執行個體可能會同時執行。<br />-   **內嵌 C#**。  使用此值，如果您想要關聯**指令碼處理**包含 C# 程式碼中的運算質**內嵌指令碼**緩衝區。<br />-   **內嵌 JScript.NET**。 使用此值，如果您想要關聯**指令碼處理**運算質中的 JScript.NET 指令碼與**內嵌指令碼**緩衝區。<br />-   **內嵌 Visual Basic.NET**。 使用此值，如果您想要關聯**指令碼處理**與 Visual Basic.NET 程式碼中的運算質**內嵌指令碼**緩衝區。<br />-   **內嵌 XSLT**。 使用此值，如果您想要關聯**指令碼處理**運算質中的 XSLT 與**內嵌指令碼**緩衝區。<br />-   **內嵌 XSLT 呼叫範本**。 使用此值，如果您想要關聯**指令碼處理**運算質與 XSLT 呼叫範本中**內嵌指令碼**緩衝區。|  
|**指令碼組件**|選取要與建立關聯的組件**指令碼處理**運算質。 只有在 [專案] 視窗中所參考的組件會顯示在此清單中。 也請注意，您必須在 GAC 中註冊組件。<br /><br /> 這個欄位時，才可以使用**選取指令碼類型**設**外部組件**。|  
|**指令碼類別**|選取您要此選擇的組件內類別**指令碼處理**運算質使用。<br /><br /> 這個欄位時，才可以使用**選取指令碼類型**設**外部組件**。|  
|**指令碼方法**|選取您要此選擇類別內的方法**指令碼處理**運算質使用。 **注意：** 確定此方法預期的輸入參數數目符合中指定的輸入參數數目**設定指令碼處理運算質** 對話方塊。|  
|**內嵌指令碼**|在此文字方塊中寫入或複製要使用的內嵌指令碼。 有效的語言與指令碼包括：C#、JScript .NET、Visual Basic .NET、XSLT 以及 XSLT 呼叫範本。<br /><br /> 這個欄位時，才可以使用**選取指令碼類型**設定為其中一個**內嵌**設定。 **注意：** 避免重複使用相同的方法簽章。 數個指令碼處理運算質具有相同的方法簽章時，BizTalk 會選取第一個實作，並捨棄其他實作。|  
  
 下圖顯示如何**指令碼處理**運算質出現在地圖中使用 C#.Net script 重新格式化電話號碼。  
  
 ![使用 C# 35; 對應若要格式化電話號碼。] (../core/media/scriptingfunctoid.gif "scriptingfunctoid")  
指令碼處理運算質對應  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用外部組件指令碼](../core/scripting-using-external-assemblies.md)  
  
-   [使用內嵌 C#、 JScript.NET 和 Visual Basic.NET 指令碼](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)  
  
-   [使用內嵌 XSLT 與 XSLT 呼叫範本指令碼](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)