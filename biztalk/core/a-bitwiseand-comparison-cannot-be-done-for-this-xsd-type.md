---
title: 無法對此 XSD 類型執行 BitwiseAnd 比較 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82bc2351-c002-458a-9d35-5fdcc91c6a0e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d057efc9f0fd9e1cd5625f191f811c53b2e1ad4f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019499"
---
# <a name="a-bitwiseand-comparison-cannot-be-done-for-this-xsd-type"></a>無法對此 XSD 類型執行 BitwiseAnd 比較
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                             Err_InvalidBitwiseComparision                              |
|  訊息文字   |               無法對此 XSD 類型執行 BitwiseAnd 比較。                |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法嘗試決定要批次處理的訊息比較的內容屬性。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定在作用中批次中提供的篩選條件未指定內容屬性其中具有 CSD 類型無法位元比較。