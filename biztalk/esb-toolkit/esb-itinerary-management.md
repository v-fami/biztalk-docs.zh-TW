---
title: ESB 路線管理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f78240de-34da-4751-aceb-b69d81403124
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fb7c2566cbd445ea305089033935427b82046bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294334"
---
# <a name="esb-itinerary-management"></a>ESB 路線管理
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供兩個不同的選項，ESB 路線管理： 集中式與分散式。 本章節將討論這些選項的每個效益和風險。  
  
## <a name="decentralized-esb-policy-management"></a>非集中式的 ESB 原則管理  
 在此案例中，ESB 用戶端應用程式會提供內容的 ESB 行程 ESB 來為每個已提交之訊息的附件。 訊息包含 SOAP 標頭的計劃的內容;管線元件收到訊息時，它會解碼訊息，然後它會升級訊息內容中，做進一步路由路線。 雖然這項設計提供的機會，以輕鬆地實作路由名單模式，完全可讓用戶端控制的訊息流程帶來下列挑戰：  
  
-   允許用戶端判斷哪些處理程序應該套用至訊息，可供選擇可用的處理序的詳細資料而言是透明 ESB 用戶端應用程式。 這種作法可能無法公開機密資訊給用戶端 ESB 行程。  
  
-   除了潛在的安全性考量，允許用戶端管理的每則訊息所送出行程不會強制執行 ESB 行程為原則除非它實作特定的用戶端。 因此，強制執行新版路線變更管理的成本極高，而且會增加受信任的用戶端應用程式的每個新的特定類型。  
  
-   允許將整個路線已提交之訊息的用戶端，用戶端應該永遠是位於受信任的子系統。否則，ESB 行程可能無法指定已不再有效的惡意的處理指示。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]處理在用戶端所提交的行程的支援不過，這個選項應該只能用於回溯相容性與測試之用。  
  
 如需啟用用戶端行程的詳細資訊，請參閱[使用管線元件讀取行程](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)。  
  
## <a name="centralized-esb-policy-management"></a>集中式的 ESB 原則管理  
 有潛在的安全性和同步處理考量固有與允許旅附加，以提交訊息，因此最佳做法是為了管理 ESB 行程實作成 SQL database中包含的中央儲存機制中的用戶端[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]針對此目的。 藉由部署旅到中央位置，ESB 路線原則可以輕鬆地管理和修改而不需要實作重大用戶端變更，而且組織可以控制訊息的處理而不會暴露潛在機密資訊給用戶端。  
  
 若要判斷適當 ESB 行程附加至輸入訊息提供特製化的管線元件。 此方法提供兩個不同的選項，讓您提交於行程為基礎的路由的訊息。  
  
-   使用第一個選項，用戶端應用程式仍可能不同的 ESB 行程藉由提供 SOAP 標頭附上要求訊息，而非提交完成路線 ESB 路線的參考資訊。 這項資訊包括 ESB 路線名稱和選擇性的版本。 在此案例中，用戶端仍可以指定如何路由訊息，但沒有任何原則同步處理錯誤或安全性項目都會破壞的風險所公開的 ESB 行程，用戶端應用程式的內容。  
  
-   第二個選項是設定 ESB 上手來自動判斷適當的 ESB 行程中，為基礎的內容或內容的訊息，而不需要從提交的用戶端的任何標頭資訊。 此案例可讓組織可以控制送出訊息的流程，並不需要留意的訊息路由用戶端。