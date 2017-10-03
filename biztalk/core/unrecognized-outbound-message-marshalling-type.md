---
title: "無法辨認封送處理類型的輸出訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e675112b-12f3-47ff-95f7-ce1a05db120e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3928bde0d81a4fe22b7c16af41c3a4b6d5c7121c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-outbound-message-marshalling-type"></a>無法辨認封送處理類型的輸出訊息
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法辨認輸出的訊息類型，封送處理預期 UseBodyElement 或 UseTemplate|  
  
## <a name="explanation"></a>說明  
 WCF。OutboundBodyLocation 屬性設定為與 UseBodyElement 或 UseTemplate，自訂管線元件或協調流程中不同的值。  
  
## <a name="user-action"></a>使用者動作  
 設定 WCF。OutboundBodyLocation 屬性為有效的值。 有效值為"UseBodyElement"或"UseTemplate 「 這是程式碼變更。   
如需輸出訊息的詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [設定動態傳送埠使用 WCF 配接器內容屬性](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [設定 WCF 配接器](../core/configuring-the-wcf-adapters.md)