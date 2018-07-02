---
title: 使用 BaseFunctoid |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26a54d-20bf-4302-a5cb-b38e4091002b
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f56dfac683e9bf10504857bbf705336b9a197c5c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993327"
---
# <a name="using-basefunctoid"></a>使用 BaseFunctoid
所有的自訂運算質都必須從 **BaseFunctoid** 類別衍生。 您必須先覆寫建構函式，然後進行一組呼叫，告知 BizTalk 對應工具有關自訂運算質的資訊。 然後您需要寫入運算質邏輯。  

## <a name="overriding-the-constructor"></a>覆寫建構函式  
 您必須在類別建構函式覆寫方法中執行數個工作，以辨識您的運算質。 這些工作是外加於您方案所需的任何運算質特定程式碼。 下表描述主要的工作。  


|                                                               工作                                                                |                                        使用這些方法或屬性                                        |                                                                                                                                                                                                                                                                                          註解                                                                                                                                                                                                                                                                                          |
|-----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                指派唯一識別碼至運算質                                                 |                                                    **ID**                                                     |                                                                                                                                                                                                                                  使用大於 6000 且尚未使用的值。 小於 6000 的值將保留供內部運算質使用。                                                                                                                                                                                                                                   |
|                                          指示運算質是否有副作用                                           |                                              **HasSideEffects**                                               |                                                                                                                                                                                                                                             由對應工具使用，以最佳化產生的 XSLT 程式碼。 依預設值，此屬性為 True。                                                                                                                                                                                                                                              |
|                                                  指向資源組件                                                   |                                           **SetupResourceAssembly**                                           |                                                                                                                                                                                              包含具有您專案的資源檔案。 如果使用建置[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，資源組件必須**ProjectName.ResourceName**。                                                                                                                                                                                               |
|                                讓自訂運算質出現在 BizTalk 對應工具工具板中                                 |        **SetName**<br /><br /> **SetTooltip**<br /><br /> **SetDescription**<br /><br /> **SetBitmap**        |                                                                                                                                                                                                                                          使用指向名稱、提示和描述字串的資源識別碼；使用 16x16 像素點陣圖。                                                                                                                                                                                                                                           |
|                                           指派運算質至一或多個類別                                           |                                                 **類別目錄**                                                  |                                                                                                                                                                                              使用一或多個 [Microsoft.BizTalk.BaseFunctoids.FunctoidCategory](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.functoidcategory.aspx) 值分類運算質。                                                                                                                                                                                              |
|                                             指定接受的參數數目                                             |                **SetMinParams**<br /><br /> **SetMaxParams**<br /><br /> **HasVariableInputs**                | 使用 **SetMinParams** 方法設定所需的參數數目，使用 **SetMaxParams** 方法設定選用的參數數目。 使用下列指導方針設定這些值：<br /><br /> -如果您不有任何選擇性參數，設定 min = max。<br />-如果您有一些選擇性的參數，請設定 max = （數字的選擇性參數-最小參數數目）。<br />-如果您想要允許無限制的選擇性參數，請勿設定最大。<br />-如果您有數目可變的輸入，請勿設定 min 或 max，並設定**HasVariableInputs** = `true`。 |
|                                             宣告可連接至您運算質的項目                                             |                                          **Microsoft.biztalk.basefunctoids.connectiontype**                                           |                                                                                                                                                                                     對每個運算質支援的 **Microsoft.BizTalk.BaseFunctoids.ConnectionType** 呼叫一次 [AddInputConnectionType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.connectiontype.aspx) 。                                                                                                                                                                                      |
|                                             宣告您的運算質可連接至的項目                                             |                                           **OutputConnectionType**                                            |                                                                                                                                              使用 [Microsoft.BizTalk.BaseFunctoids.ConnectionType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.connectiontype.aspx) 中的值，告知 BizTalk 對應工具可從您運算質擷取輸出的物件類型。 使用 **OR** 來指定多個連接類型。                                                                                                                                              |
| 告知 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 要為您的運算質叫用的方法 | **SetExternalFunctionName**<br /><br /> **SetExternalFunctionName2**<br /><br /> **SetExternalFunctionName3** |                                                                                                                     對於累計運算質，請使用 **SetExternalFunctionName** 來設定初始設定函式、使用 **SetExternalFunctionName2** 來設定累計函式，以及使用 **SetExternalFunctionName3** 來指定傳回累計值的函式。 對於非累計運算質，請使用 **SetExternalFunctionName** 來設定運算質方法。                                                                                                                      |
|  讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用內嵌程式碼叫用您的運算質  |                                   **AddScriptTypeSupport SetScriptBuffer**                                    |                                                                                                                                             搭配 **Microsoft.BizTalk.BaseFunctoids.ScriptType** 呼叫 [AddScriptTypeSupport](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) 以啟用內嵌程式碼。 叫用 **SetScriptBuffer** 以在運算質的程式碼中傳遞。 此程式碼將複製到對應中。                                                                                                                                              |
|                                          宣告內嵌運算質的全域變數                                          |                                           **[Setscriptglobalbuffer]**                                           |                                                                                                                                                                                                                                                     包含在對應中的其他內嵌程式碼都可以看到所進行的任何宣告。                                                                                                                                                                                                                                                     |
|                                   指示您的內嵌運算質所需的協助程式函式                                   |                                       **RequiredGlobalHelperFunctions**                                       |                                                                                                                                                                                                              使用 **InlineGlobalHelperFunction** 列舉，來指定所需的協助程式函式。 使用 **OR** 來指定多個協助程式函式。                                                                                                                                                                                                               |
|                                            驗證傳遞至您運算質的參數                                            |                                     **IsDate**<br /><br /> **IsNumeric**                                      |                                                                                                                                                                                                                                                         這些函式會提供 true/false 回應，而不會擲回例外狀況。                                                                                                                                                                                                                                                         |

## <a name="implementing-functoid-logic"></a>實作運算質邏輯  
 若要使運算質變的有用，您必須視運算質類別實作一或多個方法。 如果運算質為累計，則您需要提供三個方法：一個供初始設定使用、一個用來執行累計、一個用來傳回累計值。 如果運算質為非累計，則您需要提供一個傳回值的方法。  

 您也必須決定運算質實作程式碼應該複製到對應中，或是保留在編譯的 .NET 組件中並透過參考使用。  

 在下列情況下，請考慮使用內嵌運算質：  

- 其他人可讀取也可修改您的商務邏輯。  

- 您的運算質僅依存於對應所支援的 .NET Framework 命名空間。 可用的命名空間，請參閱 <<c0> [ 指令碼使用內嵌 C#、 JScript.NET 和 Visual Basic.NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)。  

- 您不想要使用 BizTalk 方案來部署和維護另一個組件。  

- 您正在寫入一系列共用變數的運算質。  

  在下列情況下，請考慮使用參考的運算質：  

- 您不想要將商務邏輯複製到可能會被其他人看到或修改的對應中。  

- 您的運算質依存於對應不支援的 .NET Framework 類別。  

- .NET Framework 所提供的新增功能讓您可以使用 BizTalk 方案來部署和維護另一個組件。  

## <a name="see-also"></a>另請參閱  
 [開發自訂參考運算質](../core/developing-a-custom-referenced-functoid.md)   
 [開發自訂內嵌運算質](../core/developing-a-custom-inline-functoid.md)   
 [開發自訂累計運算質](../core/developing-a-custom-cumulative-functoid.md)   
 [Microsoft.BizTalk.BaseFunctoids.BaseFunctoid](http://msdn.microsoft.com/library/Microsoft.BizTalk.BaseFunctoids.BaseFunctoid.aspx)