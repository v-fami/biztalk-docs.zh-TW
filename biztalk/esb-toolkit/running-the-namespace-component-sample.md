---
title: 執行命名空間元件範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2f334a8-06de-4a56-a41a-3df088bf4a72
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83a24d2720fd9c46bd1d5ccb70d92a068f8a2ec4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021731"
---
# <a name="running-the-namespace-component-sample"></a>執行命名空間元件範例
命名空間元件範例應用程式包含四個接收位置/傳送連接埠配對。 每個配對表示測試。 以下是四個測試：  

- **將新增至傳遞**。 這項測試將 XML 訊息文件中的命名空間，並將訊息直接寫入檔案，讓您可以看到新的命名空間。 這項測試的輸入的檔案是 TEST_Add_to_PassThrough.0000.ns.xml。 這項測試會使用**NamespaceSampleReceivePipeline** ，其中包含**AddNamespace**元件。  

- **加入移除**。 這項測試將命名空間加入至 XML 文件訊息，並將其移除。 然後，它會將訊息直接寫入檔案。 這項測試輸入的檔為 TEST_ Add_to_Remove.0000.ns.xml。 這項測試會使用**NamespaceSampleReceivePipeline** ，其中包含**AddNamespace**元件， **NamespaceSampleSendPipeline**包含**RemoveNamespace**元件。  

- **移除傳遞**。 這項測試會從 XML 文件訊息中移除所有命名空間，並，如此您可以確認這會將訊息直接寫入檔案。 這項測試的輸入的檔案是 TEST_PassThrough_to_Remove.0000.ns.xml。 這項測試會使用**NamespaceSampleSendPipeline** ，其中包含**RemoveNamespace**元件。  

- **擷取傳遞至透過新增**。 這項測試會擷取**OrderDetails**元素的 XML 文件訊息和寫入新的訊息，包含這個項目的直接至檔案。 這項測試的輸入的檔案是 TEST_AddViaExtraction_to_PassThrough.0000.ns.xml。 這項測試會使用**NamespaceSampleReceivePipeline** ，其中包含**AddNamespace**元件**ExtractionNodeXPath**屬性設定為 **/CanonicalOrder/OrderDetails** （任何有效的 XPath，傳回的項目就夠了這個屬性）。  

  基礎的接收位置，範例應用程式中有檔案遮罩，適用於每種測試類型，而且相關傳送連接埠篩選器在接收埠名稱。 因此，若要執行測試，您只要適當命名的訊息放入 input 資料夾。 範例應用程式執行測試，並將更新的訊息放入輸出資料夾，使用適用於目前的測試名稱，並包括 「 訊息識別碼 」。  

  本節包含下列主題：  

- [執行命名空間元件測試](../esb-toolkit/running-the-namespace-component-tests.md)  

- [新增命名空間範例運作方式](../esb-toolkit/how-the-add-namespace-sample-works.md)  

- [移除命名空間範例運作方式](../esb-toolkit/how-the-remove-namespace-sample-works.md)
