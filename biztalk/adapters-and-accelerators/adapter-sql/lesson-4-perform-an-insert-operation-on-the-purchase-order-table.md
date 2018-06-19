---
title: 第 4 課： 執行插入作業的採購訂單資料表 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66fc64c5-a3da-4014-8545-f34e6577bd73
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c966e3c10f18424b2cfb1fde0235caedbb5f58f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222686"
---
# <a name="lesson-4-perform-an-insert-operation-on-the-purchase-order-table"></a>第 4 課： 執行插入作業的採購訂單資料表
在[第 3 課： 執行預存程序來選取新加入的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)，您可以執行**UPDATE_EMPLOYEE**預存程序，並接收回應訊息包含詳細資料的新插入位員工的記錄。 在這一課，您將會根據上一課並更新協調流程以執行下列步驟：  
  
1.  在協調流程中，您建立訊息上執行插入作業**Purchase_Order**資料表。 這個步驟是類似於[步驟 1： 建立要求訊息的 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)。  
  
2.  建立要求訊息之後，您將對應的回應訊息**UPDATE_EMPLOYEE**預存程序來插入作業的要求訊息**Purchase_Order**資料表。 藉由對應的訊息，您將傳遞回應訊息從接收到插入作業的要求訊息的值。  
  
3.  傳送要插入資料錄中的訊息**Purchase_Order**資料表，並接收回應。  
  
4.  您傳送至傳送埠的回應。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 建立要求訊息 Purchase_Order 資料表的 Insert 作業](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)  
  
-   [步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)  
  
-   [步驟 3： 傳送要插入的記錄，並接收回應的要求訊息](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)  
  
-   [步驟 4： 建置專案](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)