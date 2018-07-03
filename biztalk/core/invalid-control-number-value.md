---
title: 無效的控制編號值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ac762e2-2d48-45e8-b4c4-2df246b7568c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09b274170505bf1b010d61fbefe9d43a51528aac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019836"
---
# <a name="invalid-control-number-value"></a>無效的控制編號值
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                       X12Ta1InvalidControlNumberValueDescription                       |
|  訊息文字   |                              無效的控制編號值                              |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的控制編號 （交換、 群組或交易集） 的值不符合的資料類型，或沒有正確的結構描述指定的數字數目。 結構描述是 x12serviceschema EdifactServiceSchema BaseArtifacts.dll 中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定的控制編號是否符合的資料類型和結構描述中，指定的數字的數目，然後重新傳送交換。