---
title: "BizTalk Server 如何具現化配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ebe7585-5939-4142-9281-990b4849e28d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b32e6e40bf39c09e747391bba51a54143fc67e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-biztalk-server-instantiates-an-adapter"></a>BizTalk Server 如何具現化配接器
當 BizTalk 服務啟動時，便會具現化所有的接收配接器 (只要這些配接器具有一個或多個已設定的使用中接收位置)。 根據預設，在「傳訊引擎」從佇列移除使用某個傳送配接器所傳送的第一個訊息前，不會具現化該傳送配接器 （這有時候稱為 「 延遲建立 」。）不過，如果您需要具現化傳送配接器服務啟動時，您可以使用**InitTransmitterOnServiceStart**配接器功能。 這樣便會指引「傳訊引擎」在服務啟動時建立傳送配接器，而非使用預設的延遲建立。 當沒有在端點上設定配接器時，預設的延遲建立方法有助於減少系統資源的使用量。  
  
 當您建立自訂配接器時，建議您使用 Managed 程式碼。 然而，也有可能使用原生的 COM 元件。 COM 元件的配接器中執行個體化時正常方式使用**CoCreateInstance**。  
  
 Managed 程式碼，您必須指定.NET**類型**組態檔案中的組件路徑為選擇性。  
  
 下列是可能的部署選項：  
  
|.NET 類型|組件路徑|組件部署方法|  
|---------------|-------------------|--------------------------------|  
|已指定|未指定|使用與組件相同的名稱，將組件 XCopy 到產品目錄，或是產品目錄中的子目錄|  
|已指定|未指定|全域組件快取 (GAC) 組件|  
|已指定|已指定|將組件複製至指定的目錄|  
  
 **疑難排解秘訣：**當您建立配接器使用 managed 程式碼，如果在建立失敗時，則使用 fuslogvw.exe 工具來判斷是否有無法解析的組件的參考。 這是常見的錯誤。  
  
 下圖顯示根據指定的組態而建立配接器的邏輯：  
  
 ![](../core/media/initializingtheadapter.gif "InitializingTheAdapter")  
  
 下表提供如何設定接收配接器的範例，以及設定執行階段組件的方式。  
  
|組件部署方法|InboundTypeName|InboundAssemblyPath|  
|--------------------------------|---------------------|-------------------------|  
|指定組件位置|Microsoft.Samples.MyReceiveAdapter|C:\MyAdapter\MyAdapter.dll|  
|指定 .NET 類型 (包括公開金鑰、版本及文化特性資訊)|Microsoft.Samples.MyReceiveAdapter，MyReceiveAdapter，版本 = 1.0.2510.24622，Culture = neutral，PublicKeyToken = 077cf886a2d1c020|不適用|  
|GAC 組件|Microsoft.Samples.MyReceiveAdapter，MyReceiveAdapter，版本 = 1.0.2510.24622，Culture = neutral，PublicKeyToken = 077cf886a2d1c020|不適用|