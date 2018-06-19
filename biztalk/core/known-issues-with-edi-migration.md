---
title: EDI 移轉的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc5d0a7e-974d-4e3b-a406-412420779456
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd62c1c965e814929537a62dc5d49be7e017ae3b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005967"
---
# <a name="known-issues-with-edi-migration"></a>EDI 移轉的已知問題
本主題說明中的 EDI/HIPAA 配接器模型移轉的已知的問題[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]至 BizTalk Server。  
  
## <a name="credential-information-not-migrated-for-a-file-send-port"></a>未移轉 FILE 傳送埠的認證資訊  
 移轉使用 FILE 傳輸類型的傳送埠時，用來存取的檔案資料夾，當主機沒有網路共用的權限的認證將不會移轉。 移轉之後，您必須手動啟用認證，並輸入使用者名稱和密碼來使用，在**驗證**頁面**FILE 傳輸屬性** 對話方塊。  
  
## <a name="see-also"></a>請參閱  
 [疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md)   
 [EDI 移轉公用程式](../core/edi-migration-utilities.md)