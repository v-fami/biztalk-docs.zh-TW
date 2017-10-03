---
title: "執行 「 命名空間元件 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f334a8-06de-4a56-a41a-3df088bf4a72
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fc142ca70971f023e491dbdeee693a8d41c42fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-namespace-component-sample"></a>執行命名空間 」 元件範例
命名空間 」 元件範例應用程式包含四個接收位置/傳送連接埠配對。 每一組代表測試。 下面是四個測試：  
  
-   **將加入傳遞至**。 這項測試將命名空間加入至 XML 文件訊息，並將訊息直接寫入檔案，以便您可以看到新的命名空間。 這項測試的輸入的檔是 TEST_Add_to_PassThrough.0000.ns.xml。 這項測試會使用**NamespaceSampleReceivePipeline**包含**AddNamespace**元件。  
  
-   **加入移除**。 這項測試將命名空間加入至 XML 文件訊息，並將其移除。 然後，它會將訊息直接寫入檔案。 這項測試的輸入的檔是 TEST_ Add_to_Remove.0000.ns.xml。 這項測試會使用**NamespaceSampleReceivePipeline**包含**AddNamespace**元件和**NamespaceSampleSendPipeline**包含**RemoveNamespace**元件。  
  
-   **移除傳遞**。 這項測試的所有命名空間移除 XML 文件訊息，並將訊息直接寫入檔案，以便您可以確認這。 這項測試的輸入的檔是 TEST_PassThrough_to_Remove.0000.ns.xml。 這項測試會使用**NamespaceSampleSendPipeline**包含**RemoveNamespace**元件。  
  
-   **擷取傳遞至透過加入**。 這項測試會擷取**OrderDetails**元素的 XML 文件訊息和寫入新的訊息，包含這個項目的直接到檔案。 這項測試的輸入的檔是 TEST_AddViaExtraction_to_PassThrough.0000.ns.xml。 這項測試會使用**NamespaceSampleReceivePipeline**包含**AddNamespace**元件**ExtractionNodeXPath**屬性設定為**/CanonicalOrder/OrderDetails** （此屬性，都可以使用任何有效的 XPath，傳回的項目）。  
  
 範例應用程式中的基礎接收位置有檔案遮罩適用於每個測試類型，以及相關傳送連接埠篩選器的接收埠名稱。 因此，若要執行測試，您只要適當命名的訊息放入輸入的資料夾。 範例應用程式執行測試，然後將更新的訊息置放到輸出資料夾中使用目前的測試中，適當的名稱，包括訊息識別碼。  
  
 本節包含下列主題：  
  
-   [執行測試命名空間元件](../esb-toolkit/running-the-namespace-component-tests.md)  
  
-   [如何新增命名空間範例的運作方式](../esb-toolkit/how-the-add-namespace-sample-works.md)  
  
-   [移除命名空間範例的運作方式](../esb-toolkit/how-the-remove-namespace-sample-works.md)