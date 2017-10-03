---
title: "建立控制訊息失敗批次識別碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f03078e7-46b0-4082-9d66-6b892152a12d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a5650ab649e9b0957e64f3cdecc13c725d64536
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creation-of-control-message-failed-for-batch-id"></a>建立控制訊息失敗批次識別碼
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|CreateControlMessageFailed|  
|訊息文字|建立控制訊息失敗批次識別碼 {0}。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 已啟動/停止批次。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定具有指定識別碼的批次存在內含協議的協議屬性，且資料庫已啟動。