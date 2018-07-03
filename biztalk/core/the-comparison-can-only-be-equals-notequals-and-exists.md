---
title: Equals、 NotEquals 和 Exists 比較只能是 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aad902a2-d0dc-4d91-87a7-a6305e2f40e0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50499ea6ab9f002d36c213a8bca871884d3b077a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023468"
---
# <a name="the-comparison-can-only-be-equals-notequals-and-exists"></a>比較只能 Equals、 NotEquals 和 Exists
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                 Err_InvalidComparision                                 |
|  訊息文字   |                比較只能 Equals、 NotEquals 和 Exists。                |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法嘗試決定要批次處理的訊息比較的內容屬性。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定在作用中批次中提供的篩選條件不指定 Equals、 NotEquals 和 Exists 以外的操作員。 不支援其他作業的 XSD 型別。