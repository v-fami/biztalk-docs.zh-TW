---
title: BizTalk 商務活動監控尚未設定 EDI-AS2 狀態報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f46c1c8-2771-4b16-8fb1-71952792ac4a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb2a6b9d6eaa6ac14f51c7f05e40a9f6ccffccd5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010527"
---
# <a name="biztalk-business-activity-monitoring-has-not-been-configured-for-edi-as2-status-reporting"></a>BizTalk 商務活動監控尚未設定 EDI-AS2 狀態報告
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| 產品版本 |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    事件識別碼     |                                                                      -                                                                      |
|  事件來源   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                            |
|    元件    |                                                                 AS2 引擎                                                                  |
|  符號名稱  |                                                                      -                                                                      |
|  訊息文字   | EDI/AS2 狀態報告 BizTalk 商務活動監控尚未設定。 因此將停用狀態報告功能。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI/AS2 狀態報告未啟用，因為尚未設定商務活動監控 (BAM) 透過 「 BizTalk 組態精靈 」。 BAM 基礎結構是 EDI/AS2 狀態報告的必要條件。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行 BizTalk 組態精靈設定商務活動監控。