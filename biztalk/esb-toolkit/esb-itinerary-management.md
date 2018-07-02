---
title: ESB 路線管理 |Microsoft Docs
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
ms.openlocfilehash: a17da64d784d433d18720ca9a0c35c359fffb7b9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966103"
---
# <a name="esb-itinerary-management"></a>ESB 路線管理
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] 提供兩種不同的選項，ESB 路線管理： 集中式與非集中式。 本章節會討論每個選項的優點與風險。  
  
## <a name="decentralized-esb-policy-management"></a>非集中式的 ESB 原則管理  
 在此案例中，ESB 用戶端應用程式會提供內容的 ESB 路線，為每個已提交之訊息的附加至 ESB。 訊息包含 SOAP 標頭的路線的內容;當管線元件收到訊息時，它將訊息解碼，然後它會升級訊息內容中做進一步路由路線。 雖然這項設計會提供機會來輕鬆實作傳閱名單模式，完全允許用戶端控制的訊息流程帶來下列挑戰：  
  
- 允許用戶端判斷哪些處理程序應該套用至訊息，可供選擇的可用處理序的詳細資料而言是透明的 ESB 用戶端應用程式。 這種做法可能會公開至用戶端從 ESB 路線的機密資訊。  
  
- 除了潛在的安全性考量，好讓用戶端管理的每則訊息所送出路線不會強制使用 ESB 路線為原則除非它實作特定的用戶端。 因此，強制執行路線的新版本的變更管理的成本是極高，而且會增加每個新的特定類型的受信任的用戶端應用程式。  
  
- 允許用戶端傳遞整個路線，並提交訊息，用戶端應該永遠是位於受信任的子系統;否則，ESB 路線可能無法指定已不再有效的惡意的處理指示。  
  
  [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] 處理用戶端; 提交的路線的支援不過，此選項只應用於回溯相容性和測試用途。  
  
  如需啟用用戶端端路線的詳細資訊，請參閱 <<c0> [ 使用管線元件讀取路線](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)。  
  
## <a name="centralized-esb-policy-management"></a>集中式的 ESB 原則管理  
 有潛在的安全性和同步處理考量固有與允許用戶端以使用路線附加，提交訊息，因此最佳做法是管理 ESB 行程，在中央儲存機制實作做為 SQL 資料庫，並包含在[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]針對此目的。 藉由部署到中央位置的路線，ESB 路線原則可以輕易地管理及修改而不需要實作戲劇化的用戶端變更，並組織可以控制訊息的處理，而不會暴露潛在機密用戶端的詳細資訊。  
  
 若要判斷適當的 ESB 路線，附加至輸入的訊息提供特製化的管線元件。 此方法提供兩個不同的選項，可提交以路線為基礎的路由的訊息。  
  
-   使用第一個選項，用戶端應用程式仍表示不同的 ESB 路線藉由提供 SOAP 標頭，以及要求的訊息，而不是送出完整的路線中的 ESB 路線的參考資訊。 這項資訊包括 ESB 路線的名稱和選擇性的版本。 在此案例中，用戶端仍可以指定如何可以路由傳送訊息，但不沒有原則同步處理錯誤或安全性受侵犯任何風險所公開的 ESB 路線，用戶端應用程式的內容。  
  
-   第二個選項是設定 ESB 入口匝來自動判斷適當的 ESB 路線，根據內容或內容的訊息，而不需要從提交的用戶端的任何標頭資訊。 此案例可讓組織來控制已提交的郵件流程，並不需要留意的方式將訊息路由用戶端。