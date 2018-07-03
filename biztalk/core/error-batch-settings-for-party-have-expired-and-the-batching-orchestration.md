---
title: 合作對象的批次設定已過期，和批次處理協調流程即將終止 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2f272b6-4da2-4736-8d61-ce48359f36dd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 471d42035f0c8c279fd25e8bb5ba480f7e0f962a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990055"
---
# <a name="the-batch-settings-for-party-have-expired-and-the-batching-orchestration-is-being-terminated"></a>合作對象的批次設定已過期，正在終止批次處理協調流程
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                   |
| 產品版本 |                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                               |
|    事件識別碼     |                                                                                           -                                                                                           |
|  事件來源   |                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                 |
|    元件    |                                                                                    批次引擎                                                                                    |
|  符號名稱  |                                                                                 BatchSettingsExpired                                                                                  |
|  訊息文字   | 合作對象的批次設定{0}已過期批次處理協調流程即將終止。 將不會產生其他批次，直到此合作對象的批次處理啟動 |
  
## <a name="explanation"></a>說明  
 這則警告表示批次協調流程執行個體已停用，因為已達到啟用範圍的結尾。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重新啟動下列批次處理程序：  
  
1.  開啟 BizTalk Server 管理主控台中，並移至 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。  
  
2.  重設結束準則，並按一下來重新啟動協調流程**啟動**。  
  
3.  當您按下的時間之前開始的日期時間是否**開始**，按一下**是**更新目前的日期時間的開始日期時間。