---
title: 剖析期間發生的錯誤。 X12 交換發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c1085d4-75ef-4f63-84c9-287a4a61274a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48acca94e1a32f32a296c5128e25404572f688af
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968335"
---
# <a name="error-encountered-during-parsing-the-x12-interchange-had-the-following-errors"></a>剖析期間發生的錯誤。 X12 交換發生下列錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                           |
| 產品版本 |                                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                       |
|    事件識別碼     |                                                                   -                                                                    |
|  事件來源   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                         |
|    元件    |                                                               將 EDI 引擎                                                               |
|  符號名稱  |                                                       X12InterchangeReceiveError                                                       |
|  訊息文字   | 剖析期間發生的錯誤。 X12 交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生下列錯誤： |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線時發生錯誤剖析內送 X12 交換，因為交換中敘述的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，找出交換中的錯誤訊息，並接著決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。