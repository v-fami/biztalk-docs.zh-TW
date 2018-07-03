---
title: Loopback 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- loopbacks, tutorial
- loopback tutorial, about the loopback tutorial
- loopback tutorial
- tutorials, loopback tutorial
ms.assetid: 0f69c1f1-4039-4949-8eed-127ceabbc3cc
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97714d5f7e604acbb798739fc4eb545a07968980
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010095"
---
# <a name="loopback-tutorial"></a>Loopback 教學課程
本教學課程包含詳細的步驟，說明如何使用 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]來模擬在單一電腦上的主要和夥伴組織之間的程序實作。  
  
 在真實的生產環境，您的交易夥伴組織實作會是在遠端電腦上。 此教學課程使用回送公用程式建立鏡像交易夥伴協議，以在相同電腦上模擬交易夥伴。 單一電腦的回送實例只適用於開發和測試。 建議您，不要在實際執行環境中使用回送公用程式。  
  
 此回送實例不支援簽章訊息，因此也不支援不可否認性。  
  
 如果您設定憑證授權單位，並且已有用於測試的加密私密金鑰，此實例便會支援訊息加密。  
  
 在此教學課程中，您將建立主要組織、交易夥伴組織、交易協議、使用回送公用程式建立鏡像協議，並且執行範例程序以確認回送實例。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [教學課程的事前準備](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-tutorial.md)  
  
-   [步驟 1：建立主要組織](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-the-home-organization.md)  
  
-   [步驟 2：建立交易夥伴組織](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-the-partner-organization.md)  
  
-   [步驟 3：編輯交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/step-3-edit-the-partner-interface-process.md)  
  
-   [步驟 4：建立交易協議](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md)  
  
-   [步驟 5：建立鏡像協議](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)  
  
-   [步驟 6：啟動協調流程](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)  
  
-   [步驟 7：建立範例 LOB 訊息](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md)  
  
-   [步驟 8：檢視 BTARN 資料庫中的訊息](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)