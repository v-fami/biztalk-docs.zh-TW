---
title: 步驟 3： 測試 Solution2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30dbc7c9-3c5f-4953-b26f-5c41141c22ad
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c0e484a9f6af788775ec4ae7309965327378267
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277270"
---
# <a name="step-3-test-the-solution"></a>步驟 3： 測試方案
![步驟 3 之 3](../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您會測試 EAI 方案處理訊息的方式。  
  
 **用途：** 在此步驟中，您會檢查 EAIProcess 協調流程是否正確處理訊息。 您必須將範例訊息放入 EAI 應用程式所指定的接收位置。 若 EAI 方案正確地運作，且 EAIProcess 協調流程接收到倉儲的訊息要求超過 500 個項目，協調流程會產生拒絕的要求訊息。 若 EAIProcess 協調流程接收到倉儲的訊息要求少於 500 個項目，協調流程會將訊息傳遞到 ERP 系統。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前必須先完成[步驟 2： 設定並啟動應用程式](../core/step-2-configure-and-start-the-application1.md)。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-test-the-eai-solution"></a>測試 EAI 方案  
  
1.  開啟 Windows 檔案總管並瀏覽至**C:\BTSTutorials\WareHouse**。  這個資料夾會建立安裝教學課程檔案。  
  
2.  複製**RequestInstance.XML**並將它貼入**C:\BTSTutorials\WareHouse\Request**。  
  
3.  當檔案消失時，會檢查**C:\BTSTutorials\ERP\Request**。  
  
4.  在 Windows 檔案總管，瀏覽至**C:\BTSTutorials\WareHouse**。  
  
5.  複製**RequestInstance （透過限制）。XML**並將它貼入**C:\BTSTutorials\WareHouse\Request**。  
  
6.  當檔案消失時，會檢查**C:\BTSTutorials\WareHouse\RequestDecline**。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 您在 EAI 應用程式的接收位置中放置範例訊息以測試 EAI 方案。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 部署專案](../core/step-1-deploy-the-projects.md)   
 [步驟 2： 設定並啟動應用程式](../core/step-2-configure-and-start-the-application1.md)