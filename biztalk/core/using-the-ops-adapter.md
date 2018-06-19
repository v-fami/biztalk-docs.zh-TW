---
title: 使用 Ops 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IOpsAIC interface
- Ops adapters, configuring
- Ops adapters, IOpsAIC interface
- process management solution tutorial, Ops adapters
- Ops adapters, processing
ms.assetid: 331f3614-e00b-4587-b82b-3c7bc394f361
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d93436e727265c4b381cdff72c42b3a677d0a4dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288734"
---
# <a name="using-the-ops-adapter"></a>使用 Ops 配接器
商務程序管理解決方案使用 Ops 配接器處理來自新錯誤報告功能的錯誤報告。 解決方案包括一個處理配接器訊息的範例處理常式，但您可以輕鬆的撰寫自己的處理常式，並使用其他解決方案中的配接器。 錯誤報告功能的相關資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。  
  
> [!NOTE]
>  雖然解決方案使用配接器處理錯誤報告，但配接器的用途不僅限於錯誤處理。 您可以在執行特定物件方法以回應訊息的各種不同狀況中使用配接器。  
  
## <a name="how-the-ops-adapter-processes-error-reports"></a>Ops 配接器如何處理錯誤報告  
 在方案中使用錯誤報告的連接埠最後會傳送錯誤訊息，以**BIZTALKERRORS-SP**連接埠。 連接埠篩選條件會測試是否存在**ErrorReport.ErrorType**內容屬性。 只有錯誤報告訊息擁有此內容屬性。  
  
 **BIZTALKERRORS-SP**傳送連接埠會透過使用 XML 組合器元件將訊息放置在信封中的管線執行錯誤訊息。 然後訊息移至 Ops 配接器。  
  
 ErrorEnvelope 結構描述所定義的信封標示為可接受任何類型的訊息。 但 "any" 表示 BizTalk 群組中所定義的任何訊息類型。 若解決方案收到未知類型的訊息，便會產生擱置的訊息。 這類訊息會產生錯誤，就會路由至**BIZTALKERRORS-SP**連接埠。 然後，訊息會在管線的 XML 組合器元件中產生錯誤，因為它不是已知的訊息類型。 管線錯誤會擱置訊息。  
  
> [!NOTE]
>  若要處理未知的訊息類型導致的路由錯誤，您必須撰寫自訂管線元件，並使用中的自訂管線元件**BIZTALKERRORS-SP**連接埠。 自訂元件會取代 XML 組合器元件。 您的自訂元件必須將**ErrorReport**信封標頭中的屬性並將訊息加入至 envelope 的主體。  
  
 Ops 配接器是交易式的單向傳送配接器。 配接器處理訊息時，若有必要，會先載入指定的組件。 配接器將組件快取在記憶體中，以避免載入各呼叫組件的額外負荷。 它接著會建立指定類別的執行個體，然後再使用反映取得的物件中實作的組件**IOpsAIC**介面。 如果全部都成功，配接器會呼叫**初始化**方法，然後呼叫**Execute**方法，傳遞錯誤報告訊息。  
  
 如果錯誤呼叫**Execute**，配接器重新提交訊息。 如果指定的類別未實作**IOpsAIC**找不到介面或類別或組件，配接器會擱置訊息。  
  
> [!TIP]
>  因為配接器使用反映，包含類別的組件必須位於全域組件快取 (GAC) 中。  
  
## <a name="the-iopsaic-interface"></a>IOpsAIC 介面  
 配接器需要實作的物件**IOpsAIC**介面。 介面顯示如下：  
  
```  
interface IOpsAIC  
{  
    void Initialize(string config);  
    void Execute(byte[] message);  
}  
```  
  
 配接器會將原始訊息傳遞為位元組陣列**Execute**方法。  
  
## <a name="configuring-the-adapter"></a>設定配接器  
 設定此配接器的方法和設定其他配接器的方法相同。 下表描述配接器的組態屬性：  
  
|顯示名稱|Description|  
|------------------|-----------------|  
|**.NET 組件強式名稱**|組件的完整格式名稱。|  
|**OpsAIC 類別名稱**|實作的組件內的類別名稱**IOpsAIC**介面。|  
|**初始化資料**|做為引數傳遞的字串**初始化**類別的方法。|  
  
 請注意，配接器需要有組件的完整格式名稱。 完整格式名稱是您將組件新增至 GAC 時所指定的名稱。 完整格式名稱是包含組件名稱、版本、文化特性、公開金鑰 Token 的字串。 您可以使用全域組件快取工具 gacutil.exe 查看組件的完整格式名稱。  
  
 如需有關完整格式組件名稱的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的＜組件名稱＞。 如需有關 gacutil.exe 的詳細資訊，請參閱《[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 開發人員手冊》中的＜全域組件快取工具 (Gacutil.exe)＞。  
  
 您必須在類別名稱提供命名空間。 例如，如果類別為**OpsHandler**中**OperationsHandler**命名空間，您會將類別命名做為**OperationsHandler.OpsHandler**。  
  
## <a name="see-also"></a>另請參閱  
 [Ops 配接器](../core/the-ops-adapter.md)