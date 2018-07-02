---
title: 錯誤通知的產生失敗，因為 X12 全域交易的最大限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8bbcae14-6e5c-4f79-87c6-311b4b54c7ff
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ef251a7e9af04245d1987e2d196a03f7c01b911
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980479"
---
# <a name="error-ack-generation-has-failed-as-maximum-limit-of-x12-transaction-global"></a>錯誤通知的產生失敗，因為 X12 全域交易的最大限制
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                  |
| 產品版本 |                                                                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                              |
|    事件識別碼     |                                                                                                                          -                                                                                                                          |
|  事件來源   |                                                                                                                 BizTalk Server EDI                                                                                                                  |
|    元件    |                                                                                                                     將 EDI 引擎                                                                                                                      |
|  符號名稱  |                                                                                                                          -                                                                                                                          |
|  訊息文字   | 通知產生失敗，因為可接受 X12 交易集控制編號已達到 Guest 設定的最大限制。 瀏覽至 全域設定寄件者角色畫面，欄位 ST 2 在夥伴協議管理員重設計數器 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法產生 x12 交換因為它進入交易控制編號設定通知控制編號 (ST2) 大於通知允許的項目 ST2 的最大值。 在此情況下，BizTalk Server 會使用 EDI 全域屬性，來建立通知。  
  
 交易集控制編號的最大值取決於所使用的控制編號的數字數目。 所有的三個欄位的長度上限是 9;在前置詞和尾碼欄位的最大長度為 8。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設控制編號 欄位 (ST2.2) 交易集控制編號 (ST2) 的 GS 和 ST 區段定義頁面為低於最大限制值的。 在 [EDI 全域屬性] 對話方塊中，在 BizTalk Server 管理主控台中設定此屬性。