---
title: 違反排除條件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e508da6-7edc-45c0-a7ab-f23337dc1b54
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93e55595eaf2903ead7319b5f0269f803a3a83e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968735"
---
# <a name="exclusion-condition-violated"></a>違反排除條件
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                       X12DeExclusionConditionViolatedDescription                       |
|  訊息文字   |       違反排除條件，請參閱詳細資料的執行個體中的欄位值       |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示該驗證的 X12 交換失敗在 （使用 XML 驗證工具） 的設計階段或在執行階段，在接收端或傳送端，因為執行個體中的區段無法跨欄位驗證排除規則。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定無法排除規則的區段已變更，讓它通過欄位交互驗證，然後再執行驗證程序一次。