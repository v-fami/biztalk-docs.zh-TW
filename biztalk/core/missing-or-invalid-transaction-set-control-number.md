---
title: 遺漏或無效的交易集控制編號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6064b974-e8cd-4486-abc2-010afe0d956e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14b8a05a636be08e605d8d2a5bae98748fd3dbb7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971679"
---
# <a name="missing-or-invalid-transaction-set-control-number"></a>遺漏或無效的交易集控制編號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                    X12TsMissingOrInvalidTsControlNumberDescription                     |
|  訊息文字   |                   遺漏或無效的交易集控制編號                    |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線或傳送管線無法處理交換，因為交易集控制編號 （ST02 欄位中） 的值遺漏或具有無效的值。 交易集控制編號必須是英數字元值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
1.  請確定每個交易集具有交易集控制編號。  
  
2.  請確定每個交易集控制編號的英數字元值。