---
title: 回條傳遞選項的值無效 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0eed306b-0912-4694-a55c-976128117c02
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8966e3d95e89aff023300a9834ab1bca2915421f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994847"
---
# <a name="receipt-delivery-option-value-is-invalid"></a>回條傳遞選項的值無效
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                           InvalidReceiptDeliveryOptionError                            |
|  訊息文字   |                 回條傳遞選項值:"{0}"無效。  {1}                  |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示回條傳遞選項中收到的 AS2 訊息不是有效的 URL，且不符合 AS2 RFC 4130 中的規格。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請變更為包含有效的 URL 和符合 AS2 RFC 4130 7.3 節中的規格，然後重新傳送 AS2 訊息的 AS2 訊息中有回條傳遞選項。