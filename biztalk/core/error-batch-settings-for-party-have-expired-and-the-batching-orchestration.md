---
title: 合作對象的批次設定已過期，正在結束批次處理協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2f272b6-4da2-4736-8d61-ce48359f36dd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d56e06766a980c1ce293b211d2956a86c093726
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241302"
---
# <a name="the-batch-settings-for-party-have-expired-and-the-batching-orchestration-is-being-terminated"></a>合作對象的批次設定已過期，正在結束批次處理協調流程
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|BatchSettingsExpired|  
|訊息文字|合作對象 {0} 的批次設定已過期，正在終止批次處理協調流程。 將不會產生進一步的批次，直到批次啟動此合作對象|  
  
## <a name="explanation"></a>說明  
 這個警告表示批次處理協調流程執行個體已停用，因為已達到啟用範圍的結尾。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重新啟動批次處理程序執行下列動作：  
  
1.  開啟 BizTalk Server 管理主控台，然後移至 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。  
  
2.  重設結束準則，然後按一下 重新啟動協調流程**啟動**。  
  
3.  在您按一下時的時間之前開始的日期時間是否**啟動**，按一下 **是**更新目前的日期時間的開始日期時間。