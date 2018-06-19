---
title: 失敗發生在處理 X12 傳送埠上的訊息： 接收者和傳送者識別碼辨識符號組和名稱的任何合作對象協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fdf445e8-51a3-44fb-aa71-e0b0ab9c428f
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acb05b7795c48c161ab50ab5e79d18a225306fd2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241446"
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs-and-no-party-with-name"></a>失敗發生在處理 X12 傳送埠上的訊息： 接收者和傳送者識別碼辨識符號組和名稱的任何合作對象協議
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|失敗發生在處理 X12 訊息傳送連接埠 {0}。 {1}、 {2}、 {3}、 \ {4 的收件者和寄件者識別碼/辨識符號配對不存在任何協議。 沒有合作對象名稱 {5} 存在。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析合作對象的 EDIFACT 交換，因為 BizTalk Server 無法符合升級寄件者辨識符號和識別項屬性和升級接收者辨識符號和識別項屬性，與合作對象的對應值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定傳送者辨識符號和識別項 （ISA5 和 ISA6） 和接收者辨識符號和識別碼 （ISA7 和 ISA8） 合作對象的 ISA 區段定義 頁面的 EDI 屬性 對話方塊中定義符合升級的對應交換的內容中的屬性。