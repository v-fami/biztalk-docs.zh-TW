---
title: 在處理傳送埠上的 Edifact 訊息發生失敗： 沒有接收者和傳送者識別碼辨識符號組和名稱的任何合作對象的協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11880c7c-6032-449b-b251-27fc2b2f0d72
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7df88a39d9ccbbcd94fd4498c5847c5104bb40cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240094"
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs-and-no-party-with-name"></a>在處理傳送埠上的 Edifact 訊息發生失敗： 沒有接收者和傳送者識別碼辨識符號組和名稱的任何合作對象的協議
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|在處理傳送埠 {0} 上的 Edifact 訊息發生失敗。 {1}、 {2}、 {3}、 \ {4 的收件者和寄件者識別碼/辨識符號配對不存在任何協議。 沒有合作對象名稱 {5} 存在。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析 EDIFACT 交換的合作對象，因為它無法符合升級寄件者辨識符號和識別項屬性和升級接收者辨識符號和識別項使用合作對象的對應值的屬性。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定傳送者辨識符號和識別 （UNB2.1 和 UNB2.2） 和接收者辨識符號和識別 （UNB3.1 和 UNB3.2） 合作對象的 UNB 區段定義 頁面的 EDI 屬性 對話方塊中定義符合對應交換的內容中的升級的屬性。