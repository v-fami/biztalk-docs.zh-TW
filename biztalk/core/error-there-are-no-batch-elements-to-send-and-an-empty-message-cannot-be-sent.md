---
title: "沒有要傳送的批次元素並無法傳送空白訊息，因為它不會設定合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0752079a-173e-4de3-96f4-e5de01b799b5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80dcf96feef006a2576afc5829e7927e003524a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="there-are-no-batch-elements-to-send-and-an-empty-message-cannot-be-sent-as-it-is-not-configured-for-party"></a>沒有要傳送的批次元素並無法傳送空白訊息，因為它不會設定合作對象
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|EmptyMessageNotAllowed|  
|訊息文字|沒有要傳送的批次元素並無法傳送空白訊息，因為它不會設定合作對象 {0}|  
  
## <a name="explanation"></a>說明  
 這個警告表示任何批次訊息已傳送排程為基礎的批次程序中，因為有尚未收到任何批次項目，當批次釋放已排程，以及空的批次訊號未啟用。  
  
## <a name="user-action"></a>使用者動作  
 若要避免此警告訊息公佈，請透過下列方式設定空的批次訊號：  
  
1.  開啟 [BizTalk Server 管理] 主控台。  
  
2.  移至合作對象節點。  
  
3.  開啟 [EDI 屬性] 對話方塊的合作對象。  
  
4.  按一下 [交換批次建立設定] 節點 （適用於適當的編碼方式）。  
  
5.  按一下 排程器。  
  
6.  按一下 [傳送空的批次訊號] 屬性。