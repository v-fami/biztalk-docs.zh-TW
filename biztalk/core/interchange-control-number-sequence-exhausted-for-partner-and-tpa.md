---
title: 交換控制編號序號已耗盡協力電腦和 TPA |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e77c0574-bc51-4690-a7f6-5702f6486f05
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4744a8db00985db3e85c1cb8843f07b3488544b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257038"
---
# <a name="interchange-control-number-sequence-exhausted-for-partner-and-tpa"></a>協力電腦和 TPA 交換控制編號序號已耗盡
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EdiControlNumberExhaustedForParty|  
|訊息文字|交換控制編號序號用盡夥伴 '{1}' TPA '{2}'。 重設 {2}-EDI 屬性使用 BizTalk Server 管理 中的順序。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法處理文件，因為在 {2} 協議的交換控制範圍用完。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請發出滴答聲 {2} 協議的控制編號重設或增加控制編號範圍或點擊重設按鈕控制項的數字範圍規格針對協議中的核取方塊。