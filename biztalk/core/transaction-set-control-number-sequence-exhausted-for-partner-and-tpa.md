---
title: 交易集控制編號序號已耗盡協力電腦和 TPA |Microsoft 文件
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
ms.openlocfilehash: 40d87b1f2681bb07816721971cfbd17d2c3a0b91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278334"
---
# <a name="transaction-set-control-number-sequence-exhausted-for-partner-and-tpa"></a>協力電腦和 TPA 的交易集控制編號序號已耗盡
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EdiControlNumberExhaustedForParty|  
|訊息文字|交易集控制編號序號已耗盡夥伴 '{1}' 為 TPA '{2}' 的。 重設 {2}-EDI 屬性使用 BizTalk Server 管理 中的順序。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 找不到文件的交易集控制範圍，因為使用完畢 {2} 在協議的程序。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請發出滴答聲 {2} 協議的控制編號重設或增加控制編號範圍或點擊重設按鈕控制項的數字範圍規格針對協議中的核取方塊。