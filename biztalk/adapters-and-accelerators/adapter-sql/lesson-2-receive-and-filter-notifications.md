---
title: 第 2 課： 接收和篩選器通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5ec679c-1c67-4bf4-aa88-0787373343f5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f28d0479510078b3717d68f99976808ee19aa7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222550"
---
# <a name="lesson-2-receive-and-filter-notifications"></a>第 2 課： 接收和篩選器通知
在這一課中，在您開始建立協調流程接收的變更通知**員工**資料表。 協調流程收到通知之後，它會擷取的通知和通知類型是否為插入作業中，在類型**員工**資料表，將"if"條件用來執行後續的工作。 在這一課，您將會執行下列工作：  
  
1.  新增單向接收埠和**接收**圖形至協調流程接收通知訊息。  
  
2.  新增**運算式**圖形，其中包含 xpath 查詢來擷取通知類型。  
  
3.  已知的通知類型之後，將篩選加入協調流程藉由**決定**圖形。 此圖形會決定是否通知用於插入通知，並接著執行後續的作業。 如果通知不是插入作業，協調流程不會執行任何動作。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 加入以接收通知的協調流程圖形](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)  
  
-   [步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)  
  
-   [步驟 3： 將篩選加入 Insert 通知](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)