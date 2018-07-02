---
title: 交易集控制編號序號已耗盡夥伴和 TPA 的 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67f194ca-3e0f-4ad4-8bc8-88aa7e5193a7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c39815ccd013deea9ac4ef78426320e5c371feb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968511"
---
# <a name="transaction-set-control-number-sequence-exhausted-for-partner-and-tpa"></a>協力電腦和 TPA 的交易集控制編號序號已耗盡
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                           |
| 產品版本 |                                                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                       |
|    事件識別碼     |                                                                                   -                                                                                    |
|  事件來源   |                                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                         |
|    元件    |                                                                               將 EDI 引擎                                                                               |
|  符號名稱  |                                                                   EdiControlNumberExhaustedForParty                                                                    |
|  訊息文字   | 交易集控制編號序號已耗盡夥伴的 '{1}'用於 TPA'{2}'。 重設在序列{2}-EDI 屬性使用 BizTalk Server 管理。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 找不到文件的交易集控制範圍，因為已使用協議中的處理序{2}。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請勾選核取方塊，以重設的控制編號{2}合約或增加控制編號範圍，或者協議中遇到對控制項的數字範圍規格 [重設] 按鈕。