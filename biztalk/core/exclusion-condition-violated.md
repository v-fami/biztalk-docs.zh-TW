---
title: "違反排除條件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e508da6-7edc-45c0-a7ab-f23337dc1b54
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5a508c113daf628491837adee119649ac17b478
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exclusion-condition-violated"></a>違反排除條件
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12DeExclusionConditionViolatedDescription|  
|訊息文字|排除條件違反，如需詳細資訊的執行個體中參考欄位值|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示該驗證的 X12 交換因失敗而在設計階段 （使用 XML 驗證工具），或是在執行階段，在接收端或傳送端，執行個體中的線段失敗跨欄位驗證排除規則。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認失敗排除規則的區段會變更，使其通過欄位交互驗證，然後執行驗證程序一次。