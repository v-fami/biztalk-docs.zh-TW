---
title: 收集例外狀況並保存使用 ESB 例外狀況處理器內容 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52650eed-e760-4ade-bc3f-2b5b2a1c43ff
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c43925006153ccfdcfa0c9700dd1ecf27fd3fd2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994815"
---
# <a name="collecting-exceptions-and-persisting-the-payload-using-the-esb-exception-processor"></a>收集例外狀況並保存使用 ESB 例外狀況處理器內容
在此使用案例中，協調流程的例外狀況處理常式會發佈 ESB 錯誤訊息到 BizTalk Server 訊息方塊，或是 BizTalk 失敗訊息路由機制，會產生錯誤訊息。 使用 ESB 例外狀況的編碼器管線元件中，預先設定的傳送埠會訂閱這兩個錯誤訊息類型。 它會處理錯誤訊息，並再將它們保存為磁碟檔案，您可以檢視使用 InfoPath，如 圖 1 所示。  
  
 ![收集例外狀況承載](../esb-toolkit/media/ch3-collectingexceptionspayload.gif "Ch3 CollectingExceptionsPayload")  
  
 **圖 1**  
  
 **擷取錯誤訊息，並將它保存到磁碟檔案**  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包括下列：  
  
- **預先設定的傳送埠使用 ESB 錯誤處理器傳送管線。** 您可以根據特定的需求設定此傳送埠。  
  
- **訊息保存自訂例外狀況處理常式範例。** 這個範例會示範如何鬆散偶合的泛型例外狀況處理常式可以接收錯誤訊息擷取 BizTalk Server 訊息，它們包含、 標準化及擴充訊息，和將它們以磁碟檔案寫入至檔案系統。  
  
- **BizTalk 失敗訊息路由的範例。** 此範例示範如何將正規化 ESB 例外狀況管理架構和擴充原生 BizTalk Server 中的失敗訊息路由機制所產生的錯誤訊息。  
  
  如需詳細資訊，請參閱 <<c0> [ 執行訊息保存自訂例外狀況處理常式範例](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md)並[執行 BizTalk 失敗訊息路由 ESB 處理範例](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md)。