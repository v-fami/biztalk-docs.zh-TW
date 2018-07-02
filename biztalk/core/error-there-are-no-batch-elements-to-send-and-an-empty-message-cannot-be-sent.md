---
title: 沒有要傳送的批次項目，並無法傳送空白訊息，因為它不會針對合作對象設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0752079a-173e-4de3-96f4-e5de01b799b5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73d0d44c8a5a206748eb128cd2461d1d04b54c93
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976663"
---
# <a name="there-are-no-batch-elements-to-send-and-an-empty-message-cannot-be-sent-as-it-is-not-configured-for-party"></a>沒有要傳送的批次項目，並無法傳送空白訊息，因為它不會針對合作對象設定
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------|
|  產品名稱   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| 產品版本 |                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    事件識別碼     |                                                       -                                                       |
|  事件來源   |            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI             |
|    元件    |                                                批次引擎                                                |
|  符號名稱  |                                            EmptyMessageNotAllowed                                             |
|  訊息文字   | 沒有要傳送的批次項目，並無法傳送空白訊息，因為它不會針對合作對象設定 {0} |
  
## <a name="explanation"></a>說明  
 這則警告指出，批次沒有傳送任何訊息在排程為基礎的批次程序中因為已排程批次釋放，並將空的批次訊號尚未啟用時，先前已收到批次元素。  
  
## <a name="user-action"></a>使用者動作  
 若要避免這個警告，發佈，請透過下列方式設定空的批次訊號：  
  
1.  開啟 [BizTalk Server 管理] 主控台。  
  
2.  將移至 [合作對象] 節點。  
  
3.  開啟 [EDI 屬性] 對話方塊中的合作對象。  
  
4.  按一下 [交換批次建立設定] 節點 （適用於適當的編碼方式）。  
  
5.  按一下 排程器。  
  
6.  按一下 傳送空的批次訊號 」 屬性。