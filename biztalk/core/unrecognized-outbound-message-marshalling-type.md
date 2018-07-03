---
title: 無法辨認的輸出訊息封送處理類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e675112b-12f3-47ff-95f7-ce1a05db120e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cda3e7bd3d20e39bb59c2c1fbe14dfc964fd541a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023428"
---
# <a name="unrecognized-outbound-message-marshalling-type"></a>無法辨認的輸出訊息封送處理類型
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]               |
|    事件識別碼     |                                           0                                            |
|  事件來源   |                                           0                                            |
|    元件    |                                           0                                            |
|  符號名稱  |                                           0                                            |
|  訊息文字   | 無法辨認的輸出訊息封送類型;預期 UseBodyElement 或 UseTemplate |
  
## <a name="explanation"></a>說明  
 WCF 中。OutboundBodyLocation 屬性設定為比 UseBodyElement 或 UseTemplate，自訂管線元件或協調流程中不同的值。  
  
## <a name="user-action"></a>使用者動作  
 設定 WCF。OutboundBodyLocation 屬性設為有效的值。 有效值為"UseBodyElement 」 或 「 UseTemplate"這是程式碼變更。   
如需輸出訊息的詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
-   [使用 WCF 配接器內容屬性設定動態傳送埠](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [設定 WCF 配接器](../core/configuring-the-wcf-adapters.md)