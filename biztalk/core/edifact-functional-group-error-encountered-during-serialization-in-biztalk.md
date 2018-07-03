---
title: 序列化期間發生的錯誤。 Edifact 功能群組發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed81bc79-d99c-4305-805f-ab38eae91ea0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cd5ce1a94a47c5094862decfe1bb1dbb9c1efb0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977599"
---
# <a name="error-encountered-during-serialization-the-edifact-functional-group-had-the-following-errors"></a>序列化期間發生的錯誤。 Edifact 功能群組發生下列錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                  |
| 產品版本 |                                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                              |
|    事件識別碼     |                                                                                          -                                                                                          |
|  事件來源   |                                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                |
|    元件    |                                                                                     將 EDI 引擎                                                                                      |
|  符號名稱  |                                                                            EfactFunctionalGroupSendError                                                                            |
|  訊息文字   | 序列化期間發生的錯誤。 Edifact 功能群組識別碼 '{0}'，在交換識別碼'{1}'，寄件者識別碼為 '{2}'，接收者識別碼'{3}' 發生下列錯誤： |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線在序列化外寄 EDIFACT 交換內功能群組，因為與群組敘述的錯誤時，會發生錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊來識別功能群組中的錯誤訊息，然後判斷 文件中的問題解決方法。