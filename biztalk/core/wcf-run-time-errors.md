---
title: "WCF 執行階段錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5591bd4-aa15-4c7a-903e-fc73b880692f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97f4107ddf791b8d9fd152f2258cd3185f23498f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-run-time-errors"></a>WCF 執行階段錯誤
診斷及解決 WCF 執行階段事件的資訊。  
  
## <a name="wcf-service-host-restarted"></a>WCF 服務主控件已重新啟動
  
||錯誤詳細資料|  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0x1FB0|  
|事件來源|0|  
|元件|0|  
|符號名稱|BTS_I_WCF_SERVICE_HOST_RESTARTED|  
|訊息文字|0|  
  
## <a name="explanation"></a>說明  
 此訊息提供一個方式，讓 WCF 配接器寫入「資訊性」事件日誌項目 (針對配接器提供的 API 可用來建立警告或錯誤，但無法建立資訊)。  
  
## <a name="user-action"></a>使用者動作  
 如果您在事件日誌中看到此資訊事件，表示自動復原已成功。 不需要針對此訊息採取任何進一步動作。