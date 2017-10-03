---
title: "設定 AS2 管線屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edir2.AS2.pipeline.properties
ms.assetid: 7faf6b05-710a-4d00-8c77-590ce9d9f962
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e41afd99e7af1441e2d3d8cc936c04cd9321779
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-as2-pipeline-properties"></a>設定 AS2 管線屬性
管線屬性可在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷會解析為所傳送或所接收交換的協議時，用來處理內送或外寄 AS2 訊息。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="as2-pipeline-properties"></a>AS2 管線屬性  
 您可以在 AS2 管線中設定下列屬性：  
  
|屬性|使用|值|管線/階段|  
|--------------|---------|------------|---------------------|  
|ContentTransferEncoding|指出將使用哪個方法，以 ASCII 文字格式表示二進位資料。|8bit (預設值)<br /><br /> 7bit<br /><br /> 8bit|AS2EdiSend/編碼<br /><br /> AS2Send/編碼|  
  
### <a name="to-set-a-pipeline-property"></a>若要設定管線屬性  
  
1.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，以滑鼠右鍵按一下使用您要設定屬性之管線的接收位置或傳送埠。 按一下 **[屬性]**。  
  
2.  按一下要設定屬性之管線旁邊的省略符號按鈕 (?。  
  
3.  輸入值的屬性，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)